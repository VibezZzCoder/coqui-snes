# Notices, Licensing, and Provenance

## Origin

*Coquí al Anochecer* is an original homebrew game for the Super Nintendo
Entertainment System by **Edwin RodMen** (VibezZzCoder).

| | |
|---|---|
| Repository | <https://github.com/VibezZzCoder/coqui-snes> |
| Author | <https://www.instagram.com/edwin_rodmen/> (@edwin_rodmen) |
| Copyright | © 2026 Edwin RodMen |

The same name, repository address and handle are drawn on the game's own
credits screen (Select on the title), so a copy of this ROM still says where
it came from even with every other file stripped away.

## Licence

Everything in this package that is this project's to license is released under
**Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International
(CC BY-NC-ND 4.0)**. The complete licence text is in `LICENSE`; the plain-
language summary is at <https://creativecommons.org/licenses/by-nc-nd/4.0/>.

In short: keep it, play it, and share the whole package with anyone, for free,
with credit. Do not sell it and do not publish a modified version of it.

`PERMISSIONS.md` grants some additional permissions on top of that licence —
notably that patching or repackaging the ROM to get it onto your own console
or emulator is explicitly fine. Read it before assuming something is forbidden.

The licence covers copyright. It does not license the *Coquí al Anochecer*
name or the wordmark.

## What is this project's own work

- All game code: the 65C816 assembly sources, the cartridge header, the data
  tables, the level data, the save format, and the build.
- **The font.** Every one of the 110 glyphs the game draws its text with is an
  original pixel map drawn for this project. It is not PVSnesLib's example
  font and is not derived from any existing typeface.
- **All sprite and level pixel art.** The coquí, the hen, every vehicle, the
  insect, and the six screens are built pixel-by-pixel by the project's own
  generator scripts from hand-authored tile kits. Concept paintings were made
  during development as visual guides; none was traced, sampled or converted
  into the level art.
- **All audio, with no exceptions.** The call, every cue, and every instrument
  in the music are synthesised from arithmetic by the project's own tools.
  Nothing is recorded, sampled, downloaded or derived from any existing
  recording, and the whole soundtrack regenerates from source.
- Every on-screen string, the layout of the box front, and the credit and
  callout type on it.

## What is not, and is named here rather than assumed

**The title illustration, the ending illustration, and the box key art.** The
picture behind the title screen, the picture the ending plays over, and the
painting on the box front were produced with an AI image generator from
written briefs, then converted deterministically to the SNES's palette and
tile budget by this project's own tools. The exact prompts are kept in the
project's development tree.

The illustrated **wordmark** — the large *COQUÍ / AL ANOCHECER* lettering with
the hibiscus — is part of the generated title illustration. It was reviewed
and approved by the author as the game's mark and appears on the box front
lifted from that same approved picture, not generated a second time. Every
other letter and number on the title, in the game, and on the box is drawn
by project code from the project's own font. No generated image in this
package contains any other lettering, logo, seal or brand mark.

Purely machine-generated images have uncertain copyright standing, and this
project does not claim more than it holds: the licence above conveys this
project's own rights and no others.

## Three patches to the sound driver

The SNESMod driver inside this ROM carries three small alterations by this
project, all made after linking, all in how the driver drives the sound
chip; the music and the effects themselves are unchanged:

1. Its stop routine holds the key-off signal long enough for the sound chip
   to see it every time (the stock driver could miss it about one pause in
   sixteen and leave notes ringing through a pause), and it releases only
   the six music voices, so a sound effect already sounding when the music
   stops or changes finishes its short tail instead of being cut.
2. Its music updater leaves the two sound-effect voices alone (every piece
   of music in this game uses six voices, so nothing changes on real
   hardware; on the SNES Classic's built-in emulator the stock behaviour
   silenced every effect after the first).
3. It keys the voices of a music row on with one write, after each voice's
   own volume, pitch and gain are set, and does the same for an effect (the
   stock driver keyed them one at a time, each before its registers; on the
   SNES Classic chords lost notes until this change).

Each alteration is marked in `THIRD_PARTY_NOTICES.txt` as the zlib licence
requires, and all three are this project's work, not PVSnesLib's or
SNESMod's.

## Non-affiliation

This is an independent, unofficial homebrew project. It is **not** affiliated
with, endorsed by, sponsored by, approved by, or otherwise associated with
Nintendo.

"Super Nintendo Entertainment System", "Super NES", "SNES" and related marks
are the property of Nintendo. They are used here only to identify the hardware
this game runs on. The box front deliberately carries no Nintendo mark, seal,
or trade dress of any kind.

This package contains no commercial ROM, no console BIOS, no manufacturer SDK
code, and no asset copied from any retail game.

## Warranty

None. See sections 5 and 6 of `LICENSE`. This is a homebrew ROM; run it at
your own risk on hardware you are willing to risk.
