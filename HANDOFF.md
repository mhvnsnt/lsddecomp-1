# HANDOFF — lsddecomp-1

**Last updated: 2026-11-22 (America/New_York).**
**Repo:** `mhvnsnt/lsddecomp-1` (PUBLIC), default branch `main`.
**Purpose of this file:** any agent that picks up work here reads this FIRST, then the linked docs. It states what we've done, where we're at, and what we're working toward — so the owner can say "go to this repo, pick up the work" and you just know. Update this file in the same PR whenever the state changes (add, don't delete).

## 1. What this repo is

An attempt to decompile the 1998 videogame LSD: Dream Emulator — mirrored into the owner's account 2026-11-20. This is the FirecatFG first attempt (2024), the FIRST decompilation attempt on this game. It is a work in progress, mainly intended to provide a verifiable reference to some of the more technical aspects of the game's mechanics — not a complete decomp, and not a playable rebuild on its own. For a modern port, its own README points at LSDRevamped instead.

Read the README's honesty note before trusting any name in here: every symbol and variable name was either manually written by the decompers or inferred by ghidra_psx_ldr. There has never been a symbol file leak of this game, and the decompilation style is fairly assumption-heavy — some things might be wildly different from how the developers originally intended. The docs are kept well written so you can see how the data is actually used, even this early in the process.

How it relates to the owner's other LSD repos:
- `mhvnsnt/lsd-decomp` — the AI-written matching decomp, complete (1,447/1,447 functions read).
- `mhvnsnt/lsddecomp` — the brian-oblivion lineage complete matching decomp (CC0). Its README credits THIS repo (FirecatFG/lsddecomp) for the starting segmentation and symbol names.
- `mhvnsnt/lsd_decompiled` — the cawfee lineage, early-stage WIP decomp.
- `mhvnsnt/LSDRevamped` — Figglewatts' Unity remake of the game (not a decomp).
- `mhvnsnt/libLSD` — Figglewatts' C# library for loading LSD data files.

## 2. Where we're at

### DONE
- **First-attempt decomp work (2024-09-01 → 2024-09-13):** "First remote commit" (`01a8767`), "Create README.md", "Some extra symbols", "More DreamSys functions", "DreamTimer.md" (`c677d8f`). Last push 2024-09-13 — this repo has not been touched in over two years.
- **Mirrored into this account 2026-11-20** (repo created here that day; history carried over).
- **Research docs kept:** `research-docs/`, `symbols_addrs_manual.txt`, `config/`, `disk/`, `gcc263/`.

### IN PROGRESS
- Nothing in progress. No open PRs, no releases. This is a frozen snapshot of the 2024 first attempt.

### BLOCKED
- Nothing blocked here — but be honest about the state: this decomp is early, assumption-heavy, and untouched since 2024-09-13. If the owner needs LSD code that works, the complete repos (`lsd-decomp`, `lsddecomp`) are the ones to use. Do not build plans on this repo as if it were complete, and do not treat its symbol names as proven — the README says plainly they are manual or inferred.

## 3. What we're working toward

Reference and provenance, not development. This repo is kept because everything downstream started here: the segmentation and symbol names in the complete decomps trace back to this attempt. Its value is the research docs, the manual symbol addresses, and the DreamSys/DreamTimer work — a verifiable reference for the game's more technical mechanics. If anyone ever resumes this lineage, that is upstream's work or the owner's call — not a lane's to start unasked.

## 4. Standing rules that apply here

- **Branch → PR → merge, always.** Never push to main directly. Add-only, zero-conflict PRs, no force pushes.
- **Checkpoint-and-save law:** CHECKPOINT.md first, update after every step; the repo is the save; resume, never restart.
- **No-temp-storage law:** nothing in /tmp or any wipeable location, ever. Everything goes straight into the repo or a durable folder the second it exists.
- **Real-source-only:** names here are manual or inferred — say so when you cite them. Never present an inferred name as a proven fact.
- **Licence/source logged honestly:** fan attempt, not affiliated with Asmik Ace or Sony. You need your own copy of the game (SLPS_015.56 in `disk/`) to build anything.
- **Never kill in-progress work.** Never delete game files or other lanes' work without the standing verification rules.

## 5. Key files and paths

| What | Where |
|---|---|
| Build | `Makefile` (`make update-dependencies`, `make clean extract`, `make build`, `make check`) |
| Research docs | `research-docs/`, `symbols_addrs_manual.txt` |
| Config + tools | `config/`, `tools/`, `diff_settings.py`, `gcc263/` |
| Game code (early) | `src/`, `include/`, `disk/` |
| Related repos (NOT this one) | `mhvnsnt/lsd-decomp`, `mhvnsnt/lsddecomp`, `mhvnsnt/lsd_decompiled`, `mhvnsnt/LSDRevamped`, `mhvnsnt/libLSD` |

## 6. Open decisions needing the owner

- **Does this lineage get any more work?** It has been frozen since 2024 and the complete decomps exist. Whether it stays a frozen reference or gets resumed is his call.

## 7. How to pick up

1. Read this HANDOFF.md first, then `README.md` — especially the honesty note about inferred names.
2. To build: Ubuntu or WSL2, gcc-mips-linux-gnu, python3, make, git; clone with `--recursive`; `make update-dependencies`; put your own `SLPS_015.56` in `disk/`; `make clean extract`, then `make build`, then `make check` (the two SLPS files must be identical).
3. Never commit game data. Never present an inferred name as proven.
4. Land work branch → PR → merge, add-only.
5. Update this HANDOFF.md in the same PR when the state changes.
