# DeWEB Desktop Releases

Download the latest Windows x64 portable build:

https://github.com/yy54816464/deweb-desktop-releases/releases/latest

## Latest

- Version: `0.1.1`
- File: `DeWEB-Desktop-0.1.1-win-x64.zip`
- SHA-256: `FAC03FEC0A5BF1928BEB7D1094A7CA2DB6C2FF9CF3B416D8CB0C0A2D5DE4F00B`

## Changes in 0.1.1

- Added GitHub release update check in **My**. The app checks at most once per 24 hours and links to the release page; it does not silently replace files.
- Version label now reports application build `0.1.1`.

## Install

1. Download and extract the zip.
2. Run `DeWEB Desktop.exe`.
3. Windows SmartScreen may warn because the build is unsigned.

The app is portable; there is no installer.

## Source policy

This repository hosts release binaries only. The complete desktop application source is not publicly released.

The independently auditable wallet connection mechanism is published at:

https://github.com/yy54816464/deweb-wallet-connector

## Local data

`%APPDATA%\deweb-electron`

Email login and cloud sync are optional. Wallet signing remains in the wallet app; DeWEB does not store private keys.
