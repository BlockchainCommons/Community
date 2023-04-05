# Secure Use of BlockckainCommons Command Line Tools
- There are several Linux-based operating systems built for anonymity, privacy and security:
- [Tails](https://tails.boum.org/)
- [Qubes](https://www.qubes-os.org/)
- [Whonix](https://www.whonix.org/)

This document describes how to install and use BlockchainCommons tools on these systems.

## How to Use BlockchainCommons Command Line Tools on TailsOS

[Tails](https://tails.boum.org/) is a portable operating system that protects against surveillance and censorship. It is based on the Debian GNU/Linux distribution.

The following BlockckainCommons tools have TailsOS release packages that can be installed manually:
- [musign-cli](https://github.com/BlockchainCommons/musign-cli/releases/tag/0.1.0)
- [keytool-cli](https://github.com/BlockchainCommons/keytool-cli/releases/tag/debian%2F0.7.1-1)
- [sweeptool-cli](https://github.com/BlockchainCommons/sweeptool-cli/releases/tag/debian%2F0.1.0-1)
- [bytewords-cli](https://github.com/BlockchainCommons/bytewords-cli/releases/tag/debian%2F0.3.2-1)
- [lifehash-cli](https://github.com/BlockchainCommons/lifehash-cli/releases/tag/debian%2F0.1.0-1)
- [seedtool-cli](https://github.com/BlockchainCommons/seedtool-cli/releases/tag/debian%2F0.9.1-1) 

In order to run any of the above tools on Tails:
0. While running Tails, download one or more of the above packages that you wish to use. You will now have a file with a `*.deb` extension e.g. [seedtool-cli_0.9.1-1_amd64.deb](https://github.com/BlockchainCommons/seedtool-cli/releases/download/debian%2F0.9.1-1/seedtool-cli_0.9.1-1_amd64.deb).
1. Optionally consider saving this file in your [Tails Persistent Storage](https://tails.boum.org/doc/persistent_storage/index.en.html)
2. Open an `Administrator Terminal`. This requires that you had set an `administrator password` when starting Tails.
3. To install the package if it is in the `Tor Browser` folder, enter the command: `dpkg -i "Tor Browser/seedtool-cli_0.9.1-1_amd64.deb"`
4. The executable e.g. `seedtool` will now be in your `PATH` and can be run from the command line.
