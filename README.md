# [PoD] EPE Compatibility Fix

An experimental compatibility patch for **Crusader Kings III** that attempts to make **[Ethnicities & Portraits Expanded (EPE)](https://steamcommunity.com/sharedfiles/filedetails/?id=2507209632)** and **[Princes of Darkness (PoD)](https://steamcommunity.com/sharedfiles/filedetails/?id=2216659254)** work together with fewer visual conflicts.

> [!WARNING]
> This is an **experimental** compatibility patch.
>
> Compatibility is **NOT** guaranteed. It may work correctly, partially work, or fail entirely depending on your mod setup.
>
> **Do not use this patch with important saves.** Always create a backup or start a new game before testing.

---

## What This Patch Attempts to Fix

Running EPE and PoD together can result in several conflicts:

- **Random monster features on humans** — PoD defines supernatural morph genes (horns, wings, Nosferatu deformities, Tzimisce bone growths) that default to active values at index `0`. Since EPE ethnicities do not reference these genes, the game may randomly assign monstrous features to ordinary humans.
- **Missing face sliders** — PoD's `01_genes_morph.txt` replaces EPE's version, removing EPE-exclusive morph genes such as `gene_face_decals`, which can cause portrait glitches.
- **Culture conflicts** — Both mods modify many of the same culture definitions. Without merging them, either PoD gameplay parameters or EPE ethnicity data may be lost.
- **Skin palette conflicts** — Both mods include `skin_palette.dds`. Without using PoD's version, vampire and supernatural skin colors may render incorrectly.

This patch attempts to address these issues by:

1. Zeroing out PoD monstrous genes across EPE ethnicity files so humans are less likely to receive supernatural features.
2. Reintroducing EPE-exclusive morph genes overwritten by PoD.
3. Merging conflicting culture definitions where possible.
4. Providing PoD's skin palette so supernatural skin colors can render correctly.

These changes were produced through automated processing and limited manual review. They have **not** been exhaustively tested in-game.

---

## Installation

### Option A: Manual Install (Recommended)

1. Download this repository as a ZIP (`Code` → `Download ZIP`) and extract it.

2. Copy the extracted folder (containing `descriptor.mod`, `common/`, and `gfx/`) into:

```
Documents/Paradox Interactive/Crusader Kings III/mod/
```

Rename the folder to:

```
[PoD] EPE Compatibility Fix
```

The final structure should look like:

```
Documents/Paradox Interactive/Crusader Kings III/mod/[PoD] EPE Compatibility Fix/descriptor.mod
Documents/Paradox Interactive/Crusader Kings III/mod/[PoD] EPE Compatibility Fix/common/
Documents/Paradox Interactive/Crusader Kings III/mod/[PoD] EPE Compatibility Fix/gfx/
```

3. Create a launcher descriptor next to the folder named:

```
[PoD] EPE Compatibility Fix.mod
```

Contents:

```txt
version="1.0"
tags={
    "Graphics"
    "Fixes"
}
name="[PoD] EPE Compatibility Fix"
supported_version="1.19.*"
path="C:/Users/YOUR_USERNAME/Documents/Paradox Interactive/Crusader Kings III/mod/[PoD] EPE Compatibility Fix"
```

Replace `YOUR_USERNAME` with your Windows username.

4. Launch CK3 and enable the mod.

### Option B: Git Clone

```bash
cd "Documents/Paradox Interactive/Crusader Kings III/mod"
git clone https://github.com/h1ff1dzy/PoD-EPE-Compatch.git "[PoD] EPE Compatibility Fix"
```

Then create the `.mod` file as described above.

---

## Load Order

The mods should be enabled in the following order:

| # | Mod |
|---|-----|
| 1 | Ethnicities & Portraits Expanded (EPE) |
| 2 | Princes of Darkness (PoD) |
| 3 | **[PoD] EPE Compatibility Fix** |

The compatibility patch should load **last** so it can override conflicting files from both mods.

---

## What's Included

| Directory | Purpose |
|-----------|---------|
| `common/genes/` | Restores EPE-exclusive morph genes overwritten by PoD |
| `common/ethnicities/` | EPE ethnicity files with PoD monstrous genes disabled |
| `common/culture/cultures/` | Merged culture definitions |
| `gfx/portraits/` | PoD skin palette for supernatural skin colors |

---

## Disclaimer

This project is provided **as-is**, without any guarantee that it will function correctly.

A significant portion of this compatibility patch was generated or modified using automated tools, including AI-assisted processing. While parts of the output have been manually reviewed, the generated files have **not** been individually verified.

Furthermore, the merged data from the original mods has not been comprehensively tested. There may still be undiscovered incompatibilities or edge cases that this patch does not address.

Possible issues include:

- visual glitches;
- portrait generation errors;
- broken cultures;
- gameplay bugs;
- save corruption;
- other unforeseen compatibility problems.

Use this patch entirely at your own risk.

---

## Credits

- **Ethnicities & Portraits Expanded** team
- **Princes of Darkness** team
- Compatibility patch created using automated tooling, AI-assisted processing, and limited manual review.

---

## License

This project is an unofficial compatibility patch.

All original assets, game data, and intellectual property belong to their respective authors and **Paradox Interactive**. This repository contains only the modifications required to improve compatibility between the original mods.
