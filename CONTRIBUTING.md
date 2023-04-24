# Contributing

Any contribution to OpenEBench is more than welcome! This document describes in general terms how to contribute to the project, although OEB ecosystem is build up from
several interconected components. The particularities on contributing to each of these components is placed in the corresponding code repository.
An updated and curated list of components and the corresponding repositories can be found in [repository](README.md).


## Reporting a new issue

If no existing issue seems appropriate for any, a new issue in the corresponding repository.

## How to Contribute

In general, all changes to the OpenEBench should be made through pull requests, expect for those components
not administrated by OEB team but externally provided. For those cases, please, check the contributions policy
in the corresponding repository.

If you are new to Git, the Software Carpentry's [Version Control with
Git](https://swcarpentry.github.io/git-novice/) tutorial is a good place to
start.  More learning resources are listed at
https://help.github.com/en/github/getting-started-with-github/git-and-github-learning-resources

1. Make sure you have a free [GitHub](https://github.com/) account. To increase
   the security of your account, we strongly recommend that you configure
   [two-factor authentication](https://docs.github.com/en/github/authenticating-to-github/securing-your-account-with-two-factor-authentication-2fa).
   Additionally, you may want to [sign your commits](https://docs.github.com/en/github/authenticating-to-github/managing-commit-signature-verification).

2. Fork the repository you are interested to make your changes. To keep your copy up to date with respect to
   the main repository, you need to frequently [sync your
   fork](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/syncing-a-fork):

   ```
   $ git remote add upstream https://github.com/inb/repository_of_interest
   $ git fetch upstream
   $ git checkout dev
   $ git merge upstream/dev
   ```

3. Choose the correct branch to develop your changes against.

   * The `master` branch is kept in sync with the latest tagged release, but
     should **not** be used as the base (i.e. target) branch of a pull request.

   * Additions of new features to the codebase should be based off the `dev`
     branch (`git checkout -b feature_branch dev`), with few
     [exceptions](doc/source/project/organization.rst#handling-pull-requests).

   * Most bug fixes should target the oldest supported release exhibiting the
     issue (`git checkout -b bugfix_branch release_XX.XX`).

4. If applicable, please provide the relevant information to apply the functional
   tests. The developers reviewing your pull request could help you add or run
   them as part of the pull request review process.

5. Write a useful and properly formatted commit message.
   Follow [these guidelines and template](https://git-scm.com/book/en/v2/Distributed-Git-Contributing-to-a-Project#_commit_guidelines),
   in particular start your message with a short imperative sentence on a single
   line, possibly followed by a blank line and a more detailed explanation.

   In the detailed explanation it's good to include relevant external references
   (e.g. GitHub issue fixed) using full URLs, and errors or tracebacks the
   commit is supposed to fix.
   You can use the Markdown syntax for lists and code highlighting, wrapping the
   explanation text at 72 characters when possible.
   
6. Commit and push your changes to your
   [fork](https://help.github.com/en/github/using-git/pushing-commits-to-a-remote-repository).

7. Open a [pull
   request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request)
   with these changes. Your pull request message ideally should include:

   * Why you made the changes (e.g. references to GitHub issues being fixed).

   * A description of the implementation of the changes.

   * How to test the changes, if you haven't included specific tests already.

8. Depending on the repository you are pushing the new code, it could pass all the continuous integration
   tests which are automatically started by GitHub using e.g. Travis CI.

9. If, before your pull request is merged, conflicts arise between your branch
    and the target branch (because other commits were pushed to the target
    branch), you need to either:

    1) [rebase your branch](https://git-scm.com/docs/git-rebase) on top of the
       target branch, or
    2) merge the target branch into your branch.

    We recommend the first approach (i.e. rebasing) because it produces cleaner
    git histories, which are easier to bisect. If your branch is called
    `feature_branch` and your target branch is `dev`, you can rebase your branch
    with the following commands:

    ```
    $ git checkout feature_branch
    $ git pull
    $ git fetch upstream
    $ git rebase upstream/dev
    ```

    Once you have resolved the conflicts in all commits of your branch, you can
    force-push the rebased branch to update the pull request:

    ```
    $ git push --force
    ```

## Style guidelines

### Python

OpenEBench follows [PEP-8](https://www.python.org/dev/peps/pep-0008/), with particular emphasis on readability being the ultimate goal:
  - 4 spaces (not tabs!) per indentation level
  - divergences from PEP-8 are listed in the `[flake8]` section of the `.flake8`
    file and in the `[tool.ruff]` section of the `pyproject.toml` file.
  - The Python code base is automatically formatted using
    [isort](https://pycqa.github.io/isort/) (for imports) and
    [black](https://black.readthedocs.io). To easily format your Python code
    before submitting your contribution, please either use `make diff-format`
    or run `isort FILE; black FILE` for each FILE you modify.
- Python [docstrings](http://www.python.org/dev/peps/pep-0257/) need to be in
  [reStructured Text (RST)](https://docutils.sourceforge.io/rst.html) format and
  compatible with [Sphinx](https://www.sphinx-doc.org).

### PHP
For PHP based coded servers, the convention in use is [PSR-2](https://www.php-fig.org/psr/psr-2/)

### JAVA
APIs and applications written in Java adopt the following [Java Code Covention](https://www.oracle.com/technetwork/java/codeconventions-150003.pdf)
                                                     
## Documentation

General documentation (e.g. final users, community managers, developers is found in the
[https://github.com/inab/oeb_general_docs](https://github.com/inab/oeb_general_docs)
The documentation source files need to be written in one of these markup
languages:
- [reStructuredText](https://www.sphinx-doc.org/en/master/usage/restructuredtext/index.html)
  (with Sphinx extensions)
- [Markdown](https://myst-parser.readthedocs.io/en/latest/syntax/typography.html)
  (with MyST-Parser extensions).
These source files are then built into HTML documentation with
[Sphinx](https://www.sphinx-doc.org/) by running ``make docs`` and published on
the [OpenEBench Documentation website](https://openebench.readthedocs.io).

