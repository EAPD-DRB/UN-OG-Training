# How to contribute to UN-OG-Training.

The UN-OG-Training project follows the [GitHub workflow](https://guides.github.com/introduction/flow/) and [semantic versioning protocol](http://semver.org/).

## Pull requests

We follow the [GitHub Flow](https://guides.github.com/introduction/flow/). All code contributions are submitted via a pull request towards the `main` branch.

Opening a Pull Request means you want that code to be merged. If you want to only discuss it, send a link to your branch along with your questions through whichever communication channel you prefer.

### Peer reviews

All pull requests must be reviewed by someone else than their original author, with few exceptions of pull requests from the main model maintainer.

To help reviewers, make sure to add to your PR a **clear text explanation** of your changes.

In case of changes that break past functionality and connections, you **must** give details about what features were deprecated. You must also provide guidelines to help users adapt their code to be compatible with the new version of the package.

## Advertising changes

### Version number

We follow the [semantic versioning protocol](http://semver.org/). Any change impacts the version number, and the version number conveys API compatibility information **only**.

Every pull request submitted to the main branch of the repository should have a `changelog_entry.yaml` file that has the following structure and format:
```yaml
- bump: {major, minor, patch}
  changes:
    {added, removed, changed, fixed}:
      - <variable or program>
```

Examples:

#### Patch bump

- Fixing or improving an already existing calculation.

#### Minor bump

- Adding a new state's tax logic or a major tax or benefit program (multiple variables and multiple parameters).

#### Major bump

- Major update, refactor, or compatibility change.


### Changelog

UN-OG-Training changes must be understood by users who don't necessarily work on the code. The Changelog must therefore be as explicit as possible.

Each change must be documented with the following elements:

- On the first line appears as a title the version number, as well as a link towards the Pull Request introducing the change. The title level must match the incrementation level of the version.
