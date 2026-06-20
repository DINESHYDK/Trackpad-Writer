<div align="center">

# ✏️ TrackPad Writer

### Write digitally on your laptop trackpad — for ₹239, not ₹3,199

[![Cost](https://img.shields.io/badge/Cost-₹239-34D399?style=flat-square)](#-cost-comparison)
[![Platform](https://img.shields.io/badge/Platform-Windows-22D3EE?style=flat-square)](#-requirements)
[![Tool](https://img.shields.io/badge/Built%20with-AutoHotKey%20v1.1-818CF8?style=flat-square)](https://www.autohotkey.com/)
[![License](https://img.shields.io/badge/License-MIT-F1F5F9?style=flat-square)](#-license)

No drawing tablet. No drivers. No Bluetooth pairing.
Just your existing trackpad, a ₹239 capacitive stylus, and one AutoHotKey script.

[Setup](#-setup-autohotkey) · [How It Works](#-how-it-works) · [Usage](#-how-to-use) · [Cost Comparison](#-cost-comparison)

</div>

---

## 📌 The Problem

I wanted to write digitally — notes, diagrams, rough sketches — directly on my laptop. The usual options:

| Option | Cost | Issue |
|---|---|---|
| Budget drawing pad | ₹1,779 | Average reviews, needs drivers |
| Wacom One Small | ₹3,199 | Solid, but a lot for occasional use |
| Just use a mouse | ₹0 | Handwriting is unusable |

As an engineering student, spending ₹3,000+ on a device I'd use a few times a week felt unnecessary — especially when my laptop already had a perfectly good touch-sensitive trackpad sitting unused for this purpose.

So instead of buying hardware, I treated it as an engineering problem: **could I unlock the trackpad I already own with the right software layer?**

---

## 🧭 The Journey

Five iterations, each one fixing the previous attempt's bottleneck:

| # | Attempt | Result |
|---|---|---|
| 1 | Mouse drag (left-click + drag) in Whiteboard | ❌ Completely uncontrollable handwriting |
| 2 | Fingers directly on the trackpad | ❌ Double-tap-then-write timing was impractical |
| 3 | Left hand holds mouse click, right hand writes on trackpad | ⚠️ Worked, but required a mouse at all times |
| 4 | AutoHotKey automates the held click (no mouse needed) | ⚠️ Worked, but fingertip precision on glass was limited |
| 5 | **AutoHotKey + capacitive stylus** | ✅ Natural handwriting, no mouse, no tablet |

The final insight: a drawing app just needs a **held click + tracked movement**. AutoHotKey handles the click. A capacitive stylus — which simply mimics a fingertip electrically — handles precise movement on the trackpad. Together, they're a full substitute for a drawing tablet.

---

## ⚙️ How It Works

```
┌─────────────────┐     ┌──────────────────────┐     ┌────────────────────┐
│  CapsLock press   │ --> │  AutoHotKey holds      │ --> │  Drawing app reads   │
│  (toggle)          │     │  LButton down          │     │  held click + stylus │
└─────────────────┘     └──────────────────────┘     │  movement = ink      │
                                                          └────────────────────┘
        Capacitive stylus moves across trackpad → trackpad reads it as a finger
```

- **AutoHotKey script** — remaps `CapsLock` to toggle the left mouse button between held-down and released, so you don't need to physically hold a click.
- **Capacitive stylus** — passive technology that replicates a human fingertip's electrical signature. No battery, no pairing, works on any capacitive touch surface forever.
- **Your trackpad** — already touch-sensitive on most laptops since ~2016. It was the missing piece all along.

---

## 🧰 Requirements

| Item | Cost | Notes |
|---|---|---|
| Windows laptop with a touch-sensitive trackpad | Already own it | Test by tapping the trackpad with a finger — if the cursor responds, you're set |
| [AutoHotKey v1.1](https://www.autohotkey.com/download/1.1/) | Free | Use **v1.1**, not v2 — script syntax differs |
| Capacitive disc-tip stylus | ~₹239 | Any capacitive stylus works; disc-tip styles give the best precision |

---

## 🚀 Setup: AutoHotKey

1. **Download AutoHotKey v1.1** from [autohotkey.com/download/1.1](https://www.autohotkey.com/download/1.1/) and install with default settings.
2. **Create a script file** — right-click your Desktop → `New` → `AutoHotKey Script` → name it `trackpad-writer.ahk`.
3. **Edit the script** — right-click the file → `Edit Script`, delete the placeholder content, and paste the script from [`trackpad-writer.ahk`](./trackpad-writer.ahk) in this repo.
4. **Run it** — double-click the `.ahk` file. A green **H** icon appears in your system tray, confirming it's active.
5. **(Optional) Auto-start on boot** — press `Win + R`, type `shell:startup`, hit Enter, and drop a shortcut to your `.ahk` file in the folder that opens.

> ⚠️ The script in this repo is written for **AutoHotKey v1.1 syntax**. If you have v2 installed, grab v1.1 separately — both can coexist.

---

## ✍️ How to Use

1. Open any drawing app (Whiteboard, Paint, OneNote, Excalidraw...) and select its **Pen / Draw** tool.
2. Press **CapsLock** — a tooltip confirms "Drawing Mode ON." The click is now held.
3. Write on the trackpad with your capacitive stylus, just like a notepad.
4. Press **CapsLock** again to release the click and stop drawing.
5. Press **Escape** anytime as an emergency release if the click gets stuck.

**Tips**
- Select the app's pen tool *before* pressing CapsLock.
- Rest your palm on the laptop chassis, not the trackpad, to avoid accidental input.
- `Ctrl + Z` undoes stray strokes — same as any drawing app.

---

## 🖥️ Compatible Apps

Works with anything that draws on a held left-click + drag:

`Microsoft Whiteboard` · `MS Paint` · `Paint 3D` · `OneNote` · `Excalidraw` · `Miro` · `FigJam` · `Concepts`

---

## 💰 Cost Comparison

| Solution | Cost | Extra Hardware | Charging Needed | Setup |
|---|---|---|---|---|
| **This setup (DIY)** | **₹239** | Capacitive pen only | Never | Plug-and-play |
| XP-Pen Star G430S | ₹1,779 | USB drawing tablet | Pen battery | Driver install |
| Wacom One Small | ₹3,199 | USB drawing tablet | Pen battery | Driver install |

---

## 📂 Repo Structure

```
trackpad-writer/
├── index.html              # Full project landing page (problem, journey, setup guide)
├── trackpad-writer.ahk     # The AutoHotKey script
└── README.md                # You are here
```

---

## 🛣️ Roadmap

- [ ] Add a system-tray menu (Start / Stop / Exit) instead of relying only on CapsLock
- [ ] Add adjustable click-hold sensitivity for palm-rejection tuning
- [ ] Linux/macOS equivalent using `xdotool` / `Hammerspoon`
- [ ] Pressure-sensitivity workaround exploration

Contributions and ideas welcome — open an issue or a PR.

---

## 🤝 Contributing

This started as a personal hack, not a polished product — so feedback, forks, and pull requests are genuinely welcome. If you improve the script, find a sharper trackpad gesture, or port it to another OS, open a PR.

---

## 📄 License

MIT — use it, modify it, ship it. See [`LICENSE`](./LICENSE) for details.

---

<div align="center">

Built by an engineering student who didn't want to pay ₹3,000 for something solvable with ₹239 and a weekend of iteration.

⭐ **If this saved you some money, star the repo.**

</div>
