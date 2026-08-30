# How it works - porting QHack to JP-ITA

The Italian translation and QHack v1.3 were made for different releases of *Symphony of the Night*. The translation targets Japanese Rev 2 (`SLPM_860.23`), while QHack targets the US release (`SLUS_000.67`). Their files, code addresses and raw CD offsets do not line up, so applying the two original PPF files in sequence is not a valid port.

The final build follows this path:

```text
Japanese Rev 2 -> Italian translation v1.0 -> QHack changes ported to JP -> new PPF
```

## 1. Separating game data from CD metadata

The original QHack PPF was first resolved against the US disc. Each changed raw-sector byte was mapped back to its owning ISO file and file-relative offset. This separated actual game changes from sector-level EDC/ECC data.

QHack contains 58,119 changed user-data bytes. Every one of them had to be classified before a release could be built. An unknown byte stopped the build instead of being copied blindly.

## 2. Finding the Japanese counterparts

Most unchanged code and assets still share short byte sequences between the US and Japanese releases, even when their absolute offsets differ. Unique surrounding sequences were used as anchors to relocate each QHack change into the JP-ITA files.

A mapped byte was accepted only when the Japanese target still contained the expected original value. This catches wrong anchors, regional layout differences and accidental writes into translated data.

The straightforward mapping covered tiles, collision data, entities, room data and most code changes. The remaining regional cases were handled separately.

## 3. Regional cases

A few changes could not be copied byte for byte:

- **Italian text renderer:** the translation already replaces parts of `DRA.BIN`. Those renderer changes were kept. Only the independent QHack menu-layout adjustments were ported.
- **Pointers:** absolute US addresses were never copied. The displacement introduced by QHack was applied to the corresponding Japanese pointer instead.
- **Room geometry:** `ST/CAT/CAT.BIN` and `ST/RCAT/RCAT.BIN` differ between regions. Their new room definitions were matched by structure and ported explicitly.
- **Japanese Rev 2 fixes:** some requested QHack values were already present in the Japanese release and needed no write.

No raw US pointer remains in the final build, and stage file sizes are unchanged.

## 4. Rebuilding the disc patch

The mapped payload was written onto the Italian-patched Japanese Track 1. EDC/ECC was then regenerated for all 501 touched sectors.

The public PPF is a raw diff between that repaired Track 1 and the required JP-ITA base. It contains both the game changes and the regenerated sector integrity bytes, so applying it with a normal PPF3 patcher directly produces the expected Track 1 without a separate repair step.

Release figures:

| Item | Value |
|---|---:|
| QHack source user-data bytes accounted for | 58,119 / 58,119 |
| Unaccounted source bytes | 0 |
| Touched sectors | 501 |
| Changed raw bytes in the direct-apply PPF | 156,982 |
| PPF records | 20,365 |
| Raw US pointers copied | 0 |

## 5. Verification

The release PPF was reapplied to the required JP-ITA Track 1 and compared with the repaired build byte for byte. Both produce:

```text
SHA-256 d4d2e2e8eb60147e7efba79e78f9f1fc4383ccd59f280be7a4a39aa646effbbc
```

Targeted runtime checks covered the opening, menus, saves, the added hatch rooms in both castles, the Richter gate block, the Death-skip block, the Royal Chapel boundary and the white loading rooms on the map. Normal and reverse castle geometry was checked at representative modified stages.

This is not a claim of a complete playthrough. A continuous 201.1% run through every modified room is still pending, and testing on additional hardware remains useful.
