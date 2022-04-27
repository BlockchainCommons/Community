# Release Best Practices

When releasing a product:

1. Be sure all Issues that were resolved by the release are responded to and closed.
2. Be sure README.md and any other relevant files are updated for the new release.
3. Make sure the development state is updated per [Development Phases](https://github.com/BlockchainCommons/Community/blob/master/release-path.md) and our own [best practices for development phases](https://github.com/BlockchainCommons/Community/blob/master/release-path-standards.md)
4. Choose a version number with [semantic versioning](https://semver.org/) that in brief uses the form `X.Y.Z` where:
   * `X` is the major version number, updated to `1` when a product goes from "Beta" to "Feature-Complete" and to "2" or higher if backward-incompatible changes were introduced.
   * `Y` is the minor version number, updated for major, backward-compatible new features.
   * `Z` is the patch number for bugfixes or other minor changes.
5. Create a new version at the `releases` page on the repo.
6. Typically, version the new release as `vX.Y` for a major or minor release or `vX.Y.Z` for a bugfix.
7. If there were a small number of changes, list them; if there were a large number of changes, categorize them and summarize the major elements (see, for example [Gordian Seed Tool 1.4](https://github.com/BlockchainCommons/GordianSeedTool-iOS/releases/tag/releases%2Funiversal%2F1.4).
8. Hyperlink any changes referred to elsewhere, for example in a manual, a README.md, or another file.
