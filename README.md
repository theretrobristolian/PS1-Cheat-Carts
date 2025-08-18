# PlayStation 1 Cheat Carts & CAETLA

This repo is focused on **PS1 cheat cartridges** (GameShark, Action Replay, Xplorer/Xploder, Goldfinger, etc.) and in particular the **CAETLA firmware**.  
It documents the hardware quirks, firmware differences, tools, and file formats needed to make the most of these classic devices.

---

## 🔎 Overview

Cheat carts were popular throughout the late 90s/early 00s and came in many different brands and clones:

- **US region**: GameShark / Action Replay  
- **UK region**: Xploder / Xplorer, Goldfinger, and a variety of clones (some using poor-quality chips)  
- **ROM sizes**:  
  - 128 KB was common  
  - Some models used 256 KB  
  - A few even reached 512 KB with dual-bank support  

> ⚠️ Some cheap UK clones use a CSI CAT28F010N flash chip in **PLCC32** packaging. These cannot be reflashed or updated from a PS1, making them effectively “dead end” carts. I personally own two with this limitation.

---

## 📚 Cheat Code Resources

Finding codes was half the fun back in the day:

- [ConsoleMods.org – PS1: GameShark Codes](https://consolemods.org/wiki/PS1:GameShark_Codes)  
- [CheatCC (archived, late 90s/00s)](https://web.archive.org/web/20220530205426/https://www.cheatcc.com/psx/codes/psx_0.html) ← my personal favourite source back then

---

## 🧩 CAETLA Firmware

CAETLA is the most flexible firmware replacement for cheat carts.

- **Main versions of interest**:
  - `0.35` – best for ROM-baked codes  
  - `0.37` – stable, recommended when loading codes from memory card files  
  - `0.38` – last release, but known to be buggy  

### Naming & UI quirks
- PS1 memory card block = **8 KB**.  
- File size shows on PS1 as something like `661/7924`.  
- Save names like `0:CHE-cheats` are **case-sensitive**.  
- The displayed name at the bottom is **16 characters**, no auto-centring.  
- Cheat descriptions auto-centre but are also case-sensitive.  
- Row count limit for cheat screen names ≈ **34 characters**.  

---

## 📝 Cheat File Format

Cheat files are plain text (`cheats.txt`) and must be converted into a memory card save using `CAECODE.EXE`.

Example format:

```txt
#----------------------------------------------------------------------------
"007 The World is Not Enough -USA"
#----------------------------------------------------------------------------
"------- Health Upgrades --------" .off
"Invincible" .off
80073A04 0001
30073D3A 0001
"-------- Ammo Upgrades ---------" .off
"Infinite Ammo" .off
30073D3D 0001
...
.end
```

### Rules
- **Quotes** (`" "`) required for cheat/game names  
- Each cheat/game section must end with `.end`  
- `.off` marks a code as disabled by default in the UI  
- Codes must each be on **their own line** (not inline with the name)  
- Lines starting with `#` are comments/annotations  
- Section headers (in quotes) make menus easier to navigate  

---

## 💾 Memory Card Usage

To get cheats onto a memory card:

1. Format your `cheats.txt` file  
2. Use **CAECODE.EXE** (Windows tool, copyrighted – archived [here](https://ia803109.us.archive.org/view_archive.php?archive=/25/items/PS1_Gameshark_Firmware/wintools.zip))  
3. Save into a memory card image (`.mcd`)  
4. Transfer to hardware:
   - With a **MemCard Pro (8BitMods)** you can copy/FTP the `.mcd` to your SD card  
   - Example filename: `MemoryCard1-1.mcd`  

---

## 🛠 Related Projects

- [UniROM](https://unirom.github.io) – alternative ROM project  
- [mkpsxiso](https://github.com/Lameguy64/mkpsxiso) – build bootable PS1 ISOs  
- [nxflash](https://github.com/danhans42/nxflash) – modern flasher for cheat carts (successor to `XFLASH`)  

---

## ✨ Why CAETLA?

Compared to stock firmware, CAETLA provides:
- Memory card–based cheat storage  
- Flexible code editing & organisation  
- Compatibility with more ROM sizes/carts  
- Tools for reflashing & experimenting  

---

## 📖 Notes

- 1 memory block = **8 KB**. Plan cheat file size accordingly.  
- Some carts support dual ROM banks, allowing multiple firmwares.  
- Clones with **non-reflashable flash chips** (e.g., CSI CAT28F010N) are effectively stuck.  

---

## 🔮 Future Directions

- Documenting hardware variations (ROM sizes, pinouts, flash chip IDs)  
- Building a library of ready-to-flash CAETLA images  
- Collecting properly formatted community `cheats.txt` packs  

---

## ⚠️ Disclaimer
This project is for **educational and preservation purposes only**.  
CAETLA, CAECODE, and related binaries are copyrighted by their respective authors.  
Please use responsibly.
