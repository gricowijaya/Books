# Equality Explanation Logging
Equality explanation logging is part of z3's trace feature which can be enabled by passing `TRACE=true`. It provides justifications for equalities that were used to match the trigger of a quantifier as well as equalities that were used to substitute terms bound to quantified variables when instantiating quantifiers.

## Equality Justifications
The logged information consists of several `[eq-expl]` lines that indicate why some term `A` is equal to some term `B` that is closer to the root of the union-find data structure representing `A`'s equivalence class. Following these steps to the root from any two terms in the same equivalence class allows a justification for these two terms being equal to be constructed.

**Note**: It is guaranteed that by the time a `[new-match]` line is reached in the log all relevant equalities for that match have been updated, but any steps needed to reach the root from `B` or equalities needed by a congruence step may or may not be up-to-date by the time the justification for `A = B` is logged.

Log lines for equality explanations have the following syntax:
```
[eq-expl] #<id of term A> (lit | root | cg | th) <proof type dependent info> ; #<id of term B>
```
The semantics of such a line is that `A = B` where `B` is closer to the root, as described above. The middle part of the line gives an explanation for why `A = B` holds:
- **lit**: The equality was provided to z3 directly (either asserted or produced by a quantifier). The proof type dependent info then consists of the id of that term. Such a log line may look like:
    ```
    [mk-app] #3 = #1 #2
    [eq-expl] #1 lit #3 ; #2
    ```
- **root**: The term is the root of its equivalence class. The proof type dependent info and the id of term `B` are omitted such that a log line may look like:
    ```
    [eq-expl] #1 root
    ```
- **cg**: The equality `A = B` is part of the congruence closure of a set of other equalities. The proof type dependent info consists of pairs of arguments (the first element being an argument of term `A` and the second an argument of term `B`) that are pairwise equal. Such a log line may look like:
    ```
    [mk-app] #5 f #1 #2
    [mk-app] #6 f #3 #4
    [eq-expl] #5 cg (#1 #3) (#2 #4) ; #6
    ```
- **th**: Indicates that an equality was added by a theory solver. The proof dependent info consists of the name of the theory. For example a log line added by the integer arithmetic theory solver may look like:
    ```
    [eq-expl] #1 th arith ; #2
    ```

## New Matches
When a trigger is matched a `[new-match]` line appears in the log. As mentioned in the note above all equality justifications are guaranteed to be up-to-date at this point. Such a line may look like:
```
[new-match] 0x7f9eb587d440 #166 #165 #476 ; #419 (#418 #477)
```
It provides a fingerprint for the match (`0x7f9eb587d440`) that will be used to reference the match when the quantifier is instantiated, the id of the quantifier that will be instantiated (`#166`), the id of the trigger that was matched (`#165`), the ids of terms that were bound to quantified variables (`#479`), and, after a semicolon, the ids of (single) terms that were matched against top level structure of the trigger (`#419`) or pairs of ids for equalities that were used (`#418`, `#477`, indicating that `#418 = #477` was used). The first term of such a pair will have occurred as a sub-term of some previously matched term and the second term is used to replace that term and obtain the match.

It is then possible to obtain a justification for `#418 = #477` by following the `[eq-expl]` steps from both terms to their common root. When instantiating the quantifier the roots of the terms bound to the quantified variables will be used. This term, too, can be obtained by simply following the `[eq-expl]` steps to the root.