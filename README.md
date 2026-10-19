# Juno for Mac

Juno is a team of AI agents that works for you. Each agent can use your Mac (files and commands, always asking first) and its own sandbox computer with a browser.

This repository only hosts the installers. The source code is not public yet: Juno is a work in progress.

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
- **Sandbox computer**: a Linux desktop with Chromium in a lightweight VM. Juno starts it the first time an agent needs a browser.

## Known limitations (0.1 beta)

- The sandbox image is not downloadable yet, so on other Macs agents have files and commands on your Mac but no sandbox browser. This comes in the next release.
- Not notarized (see Install step 2).
- No automatic updates yet: download new versions from Releases.

## Feedback

Open an [issue](../../issues).

## Third-party software

Juno includes Apple's [container](https://github.com/apple/container) (Apache License 2.0); its license is inside the app at `Juno.app/Contents/Resources/apple-container/LICENSE`.
