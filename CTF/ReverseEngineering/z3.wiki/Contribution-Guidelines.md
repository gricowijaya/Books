# Contribution Guidelines

There are many ways to contribute to Z3, and the Z3 team is grateful for all contributions. This overview summarizes the most important steps to get you started as a contributor.


## What to contribute?

- Engage with other Z3 users and developers on [StackOverflow](http://stackoverflow.com/questions/tagged/z3).
- Report bugs to the [Z3 issue tracker](https://github.com/Z3Prover/z3/issues).
- Make suggestions for changes, updates, or new features to the [Z3 issue tracker](https://github.com/Z3Prover/z3/issues).
- Contribute tests and benchmarks to the [Z3 test repository](https://github.com/Z3Prover/z3test).
- Contribute bug fixes, example code, documentation, or tutorials to [Z3](https://github.com/Z3Prover/z3).
- Contribute new features to [Z3](https://github.com/Z3Prover/z3).


## Bug reports

When submitting bug reports, please consider providing the following information (especially if you think that it is irrelevant!):

- Reproduction steps: step by step description to reproduce the problem.
- Expected: Describe the behavior you expect.
- Actual: Describe the behavior you see.
- Test input: If there is any test input, e.g., an SMT2 file, please provide a link to the whole file instead of a partial description. There are many services that save such files for some time. The closest one to GitHub is [GitHub Gist](https://gist.github.com/).
- Version: The Z3 version (run `z3 -h`, include the hash code if it reports one). If you are using any of the APIs, please include the programming language, the platform, and the version of the compiler you use to compile your application (and if you compile Z3 yourself, include platform and compiler version used for this purpose too).


## CLA

Contributors wanting to contribute code are required to sign a [Contribution License Agreement](https://cla.microsoft.com/) (CLA) before any pull requests can be considered. After submitting a request via the provided form, electronically sign the CLA when you receive the email containing the link to the document. This only needs to be done once for each Microsoft OSS project you contribute to.

Please note that your employer may have to agree to the CLA if you want to contribute code in the course of work for you employer.


## Tests and Benchmarks

We are grateful for any contributions to our [test repository](https://github.com/Z3Prover/z3test). Especially where API usage is concerned, we currently do not have a great deal of test cases. 

Performance benchmarks are very welcome as well. If you do have benchmarks in SMT2 format to contribute, please consider sending them to [SMT-LIB](http://www.smtlib.org/).


## Code contributions

For contributions that include a significant amount of source code, please follow these steps:

- If you haven't done so yet, create your own fork of Z3. This is your own copy of Z3 that may hold modified source code and additional branches that are not published within the Z3 repository. If you wish you can also publish links to your own fork and/or branch elsewhere (e.g., for preliminary version in paper submissions, or for prototypes that are not ready for integration into Z3 yet).
- Create a new branch that has a descriptive name.
- Make sure your branch is set up to follow Z3's master branch.
- Commit changes to your branch and push them to your fork.
- Test your code on at least two platforms, a recent version of Windows and at least one Linux or OSX system. If you are unable to comply with this requirement, please ask for help in the [issue tracker](https://github.com/Z3Prover/z3/issues).
- Submit a pull request and include a clear statement about how your code was tested in the pull request comments.

If you're unfamiliar with pull requests, take a look at [Using pull requests](https://help.github.com/articles/using-pull-requests/); Z3 uses the Fork & Pull model.

Small changes like corrections in the documentations and code contributions of less than 15 lines of code do not require a CLA to be in place if no intellectual property is contained in the contribution.


## Bug fixes

Everybody is welcome to submit bug fixes to issues reported in the [issue tracker](https://github.com/Z3Prover/z3/issues). Please follow these steps to make everything as smooth as possible:

- Add a comment in the issue tracker explaining that you're working on a solution.
- Create a branch on your fork with a descriptive name, e.g., issue_xxx.
- Push all changes to your fork.
- Submit a pull request, making sure to link to the respective issue in the tracker.


## Example code, documentation, tutorials

Before preparing any submissions of this category, please make sure that they are wanted and appreciated. Simply open an issue in the [issue tracker](https://github.com/Z3Prover/z3/issues) so that other developers and users can provide feedback before you invest significant effort.

- Example code should be submitted in the form of pull requests adding additional directories/files in the examples directory of Z3.
- New documentation and tutorials will be most conveniently stored in the [Z3 web repository](https://github.com/Z3Prover/z3prover.github.io).
- API Documentation is automatically generated from the source code for the most part, so fixes and updates to the API documentation will are handled just like general code contributions.


## Package management systems

We actively encourage others to publish packages for their favorite package management system. Scripts to generate packages may be published in a separate Z3Prover/* repository. A long-term commitment to maintenance of the packages is required from the submitter. To that end, please add a file called MAINTAINER containing your name and e-mail address alongside the package scripts.


## New features

Before implementing any new features, please make sure that they are welcome. Some new features may not align with our plans and strategy, and if that is the case, we would like to tell you so before you invest significant effort. 

Simply open an issue in the [issue tracker](https://github.com/Z3Prover/z3/issues) so that the developers and other users can provide feedback before you start working on it. 

Note that any new feature that will require maintenance in the future must have a clear commitments from the submitter to maintain the respective components in the future. If you can't make such a commitment please refrain from submitting your contribution. To maintain good quality, we reserve the right to remove any contribution that is not maintained properly or suffers from issues being resolved untimely.

For prototypes and experiments, note that you can publish links to your own fork of Z3. Prototypes that are not fully featured or components that will not be maintained in the future can be archived in your own fork and branches without inconveniencing other users.

### Coding guidelines

Use common sense when contributing code - make an effort to use a similar style to nearby existing code. Strict requirements are that we do not want any TAB characters in the source code; use 4 spaces instead. Further, all new files, including test cases and other types of files, must contain a copyright attribution of the following form:

    Copyright (c) Microsoft Corporation. All Rights Reserved. 

