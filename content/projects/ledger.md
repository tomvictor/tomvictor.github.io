---
title: "yLedger - A Privacy-First Menu Bar Work Log for macOS"
date: "2026-05-04"
# description: ""
# tags: ["macOS", "Swift", "SwiftUI", "Menu Bar"]
categories: ["projects"]
# series: ["Themes Guide"]
aliases: ["yledger", "yledger-privacy"]
# ShowToc: true
# TocOpen: true
ShowBreadCrumbs: true
---

yLedger is a lightweight macOS menu bar app for capturing what you're working on, the moment you're working on it. It lives in your menu bar, opens with a single click, and writes every entry to a plain JSON file on your own Mac. Nothing is uploaded, nothing is tracked, nothing leaves your computer.

## Features

* Lives in the macOS menu bar — log a note without leaving your current window
* Organise entries into projects, with a default project for one-click logging
* Quick note plus optional details for longer context
* Per-project history with timestamps and friendly relative dates ("Today", "Yesterday")
* Edit or delete entries any time
* Custom Aurora dark theme — a dense, calm interface designed for quick glances
* Sandboxed, fully offline, no account required

## Planned Features

* Tagging and search across entries
* Daily and weekly summary view
* Export to Markdown and CSV
* Optional reminders to log at the end of a focus session

## Installation

yLedger is distributed exclusively through the Mac App Store.

[Download yLedger on the Mac App Store](https://apps.apple.com/app/yledger)

**Requirements:** macOS 13 (Ventura) or later.

## Usage

1. Click the **yLedger** icon in your menu bar (look for the clipboard pencil).
2. Pick a project from the dropdown — or set a default project once and skip this step forever.
3. Type your note, optionally add details, and hit **Log**.

That's the whole loop. Past entries appear underneath, grouped by project, so you can scroll back through your day without opening another app.

## Where your data lives

yLedger stores everything in a single human-readable JSON file at:

```
~/Library/Application Support/yLedger/log.json
```

You can back it up, copy it between Macs, or open it in any text editor. It's your data, in a format you can read.

## Links

- [Docs](https://github.com/tomvictor/ylegder/blob/main/README.md)
- [GitHub](https://github.com/tomvictor/ylegder)
- [Issue Tracker](https://github.com/tomvictor/yledger/issues)

## Support

Star the project on [GitHub](https://github.com/tomvictor/yledger) :)

For questions or bug reports, open an issue on GitHub or email **tom.victor@vinnter.se**.

## Privacy Policy

**Effective date:** 2026-05-04

yLedger is designed around a single principle: your work log is yours, and it never leaves your Mac.

### Data we collect

**None.** yLedger does not collect, transmit, or share any personal data, usage data, or diagnostic data of any kind.

### Where your data is stored

All projects, log entries, timestamps, and preferences are stored **locally on your Mac**, in a single JSON file at:

```
~/Library/Application Support/yLedger/log.json
```

This file is created and managed by the app on your device. It is never uploaded to any server.

### Network access

yLedger makes **no network requests**. It does not contact any server operated by the developer, Apple, or any third party while you use it. You can verify this by running the app with Little Snitch, Lulu, or any other macOS firewall — there is no outbound traffic.

### Analytics and telemetry

**None.** yLedger does not include:

- usage or behavioural analytics (no Firebase, Mixpanel, Amplitude, etc.)
- crash reporting SDKs (no Crashlytics, Sentry, etc.)
- advertising identifiers or trackers
- any third-party SDK that transmits data off-device

### Third-party services

yLedger does not integrate with any third-party service.

### Sandboxing

yLedger runs inside the standard macOS App Sandbox. Its access to the filesystem is limited to the app's own container under `~/Library/Application Support/yLedger/`.

### Children's privacy

yLedger does not collect data from anyone, and that includes children. The app is suitable for all ages.

### Your rights

Because yLedger does not collect any data, there is nothing for the developer to access, export, or delete on your behalf. You are free to delete your log at any time by removing the file at `~/Library/Application Support/yLedger/log.json`, or by uninstalling the app.

### Changes to this policy

If this policy is ever updated, the **Effective date** at the top of this section will change. Material changes will also be noted in the app's release notes.

### Contact

If you have any questions about this privacy policy, please contact:

**Tom Victor** — mail@tomvictor.dev

## License

The project is licensed under the MIT license.
