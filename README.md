# agix

agix is a canvas for pictures and video that people and Claude work on together: open pictures and videos,
draw and annotate on them, link them, and share a room with others. Every change is an edit you can undo.

This repository holds the downloads and their notes. It holds no source code.

## Download

The [releases page](https://github.com/hector-crean/agix-releases/releases) has each version as
`agix-X.Y.Z-aarch64.dmg`, with `SHA256SUMS` beside it.

- **Apple silicon Macs only** (M1 or later). There is no Intel, Windows or Linux build yet.
- To check a download, put `SHA256SUMS` in the same folder and run `shasum -a 256 -c SHA256SUMS` there.

Open the `.dmg` and drag **agix** to **Applications**.

## Opening it the first time

This build is signed, but not yet notarised by Apple, so macOS cannot check it and will not open it the first
time:

1. Open **agix** from Applications. macOS says it cannot check it for malicious software. Choose **Done**.
2. Open **System Settings > Privacy & Security** and scroll down to **Security**. Beside the line about agix,
   choose **Open Anyway**, and confirm with your password or Touch ID.
3. Open **agix** again and choose **Open**.

From then on it opens like any other app. A new version asks once more, the same way.

## Signing in, and what stays on your Mac

agix opens on Home. Signed out, choose **Open a scratch canvas**: nothing you make there leaves your Mac. This
version does not keep a scratch canvas once you quit.

Sign in with your Google account to make rooms on the agix server and share them. A room's work is then kept on
the server, so the people you invite can open it. Your session is kept in your Mac's keychain until you choose
**Sign out** on Home. While the server is in testing, only the Google accounts it has added can sign in.

## Claude and other agents

While agix runs, it serves its control surface to Claude Code and other MCP clients at
`http://127.0.0.1:3847/mcp`. It listens on this Mac only (127.0.0.1), so nothing else on your network can reach it.
To connect Claude Code:

```sh
claude mcp add --transport http agix http://127.0.0.1:3847/mcp
```

An agent starts out able to read the canvas and propose changes, which you accept or reject; the agent panel is
where you let it do more.

## Licences

agix is available under the MIT licence or the Apache licence, version 2.0, at your choice
([LICENSE-MIT](LICENSE-MIT), [LICENSE-APACHE](LICENSE-APACHE)). [THIRD-PARTY.html](THIRD-PARTY.html) lists every
crate and asset a release is built from, with its licence; the same page is inside the app, at
`agix.app/Contents/Resources/THIRD-PARTY.html`.
