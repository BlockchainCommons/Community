# Repo Creation Conventions

The following outlines standards for the creation of Blockchain Commons repos.

## Secure Template Usage

All repos should be creating using the [secure template](https://github.com/BlockchainCommons/secure-template). After creating a repo, be sure to edit the `README.md` file to make it appropriate for your project:

* Replace `$projectname` with **your-project-name**.
* Fill in listings of other documents, origins, and subsequent usage.
* Update the release status based on our [release-path document](https://github.com/BlockchainCommons/Community/blob/master/release-path.md).
* Delete sections you are not using, possibly including project sponsors, installation instructions, etc. 
* Overall, each blank section should either be filled in or deleted.

Be sure to return to your `README.md` occasionally, particularly to update the release status as that changes.

## Naming Conventions

The following naming conventions are suggested for all new repos. (Old repos may be fully brought over to the conventions in the future.)

Consult the section based on your repo-type for the best conventions for that repo.

### Applications

App repos should be of the form `AppName-OS`.

`AppName` should be camel-cased for mobile, desktop, and web apps; and lowercased for command-line apps.

`-OS` might be:

* ` `. Standalone device.
* `-Android`. Android builds.
* `-Catalyst`. Catalyst-only targets; otherwise use `-iOS`.
* `-cli`. Unix command line.
* `-iOS`. All cross-compatible and iOS Apple builds.
* `-macOS`. Mac-native-only targets; otherwise use `-iOS`.
* `-web`. A web app.

_We are not currently including the language used to write CLI and web programs in the repo name, but please feature it clearly and prominently in the `README.md`._

**Examples:** GordianGuardian-iOS

### Categories

Category repos should be of the form `Category-Name`.

** **Examples:** Gordian

### Forks

Add a `-bccfork` suffix.

### Libraries

Libraries should have a `bc-` prefix (to prevent name collisions), then the name, then a language suffix. Separate multiple languages in the suffix by slashes (`/`). The exact formatting of these library repo names should follow naming conventions appropriate to the library language:

* C: bc-library-c
* C++: bc-library-cpp
* Java: bc-library-java
* Rust: bc-library-rs
* Swift: BCLibrarySwift

** **Examples:** bc-libs-java

### Web Sites

Web sites should be of the form `web.site.url`.

**Examples:** www.blockchaincommons.com

### Other Repos

Other repos should be of the form `Repo-Name`.

**Examples:** Airgapped-Wallet-Community, Learning-Bitcoin-from-the-Command-Line

### Old Repo Update Examples

As examples, the following old repos could change as follows:

* `bc-bytewords` -> `bc-bytewords-c` (library)
* `bc-lethekit` -> `LetheKit` (app)
* `bc-seedtool-cli` -> `seedtool-cli` (app)
* `Bitcoin-Standup-Scripts` -> `bitcoinstandup-cli` (app)
* `crypto-commons` -> `Crypto-Commons` (category)
* `LifeHashTool` -> lifehash-cli (app)
* `ResearchAgenda` -> `Research-Agenda` (other)
* `spotbit` -> `Spotbit-web` (app)
* `torgap` -> `Tor-Gap` (category)

## About-Info Conventions

Each repo also features an "About" statement, which shows up on the master BCC repo listings.

It should generally be of the form "[noun phrase]" where the phrase starts with "[specific-info general-category]", with libraries ending with "[in language]" and apps ending with "[for OS]". More farflung repos might not precisely match this convention, but should still be noun phrases.

Generally, try to maintain consistency with existing repos for best clariry. 

**Examples:** Cryptographic Seed Tool for the command line, Blockchain Commons Research papers, Gordian products and technologies such as Wallet and Server, Sharded Secret Key Reconstruction (SSKR) reference library in C
