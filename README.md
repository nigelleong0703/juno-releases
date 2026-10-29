# Juno for Mac

Juno is an AI teammate that lives in your group chats. This repository hosts the Mac installers only; the source code, the server and the other clients are at [nigelleong0703/juno](https://github.com/nigelleong0703/juno).

The installers below are the 0.1 beta: a standalone Mac build where agents use your Mac (files and commands, always asking first) and a sandbox computer with a browser. Newer features (group chats on Slack, Feishu, Discord and Telegram, connected apps, documents) need a Juno server; see the main repository.

## Download

Get the latest `.dmg` from [Releases](../../releases).

**Requirements**

- A Mac with Apple silicon (M1 or later).
- macOS 26 or later for the sandbox computer (it runs on Apple's `container`, which ships inside Juno).
- A model: sign in with a ChatGPT plan that allows agent access, or bring an API key (OpenAI-compatible providers, or a local model in Ollama or LM Studio).

## Install

1. Open the `.dmg` and drag **Juno** into **Applications**.
2. This beta is not notarized by Apple yet, so macOS blocks the first launch. Either:
   - open **System Settings → Privacy & Security**, scroll down and click **Open Anyway** next to Juno; or
   - run `xattr -dr com.apple.quarantine /Applications/Juno.app` in Terminal.
3. Open Juno, go through the short intro, choose **Start on this Mac**, and connect a model.

The first time macOS asks to let Juno use its keychain item ("Juno Safe Storage"), click **Always Allow**. Juno keeps its local keys there.

## What runs where

- **On this Mac** (the default): everything stays on your Mac. Data lives in `~/Library/Application Support/@agent-desktop/desktop/`. Agents work in `~/Juno`; anything outside it, and every command, asks you first.
- **Sandbox computer**: a Linux desktop with Chromium in a lightweight VM. The first time an agent needs a browser, Juno downloads the sandbox image (about 640 MB, [ghcr.io/nigelleong0703/juno-sandbox](https://github.com/users/nigelleong0703/packages/container/package/juno-sandbox)) and starts it with Apple's `container` (built in, macOS 26+) or Docker.

## Updates

From 0.1.1 on, Juno checks this repository for new versions, downloads them in the background and asks you to restart. (0.1.0 has no updater: install 0.1.1 by hand once.)

## Known limitations (0.1 beta)

- Not notarized (see Install step 2).
- LibreOffice installs inside the sandbox the first time a document needs it, so that first conversion takes a few minutes.

## Feedback

Open an [issue](../../issues).

## Third-party software

Juno includes Apple's [container](https://github.com/apple/container) (Apache License 2.0); its license is inside the app at `Juno.app/Contents/Resources/apple-container/LICENSE`.
