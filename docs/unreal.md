# Unreal Engine: licensing and free sources

> This is the catalog's reading of Epic's terms, not legal advice. Every quote below was read on the live page on 2026-10-13; re-read the source before you ship.

Unreal's free content changed a lot after the Unreal Marketplace became Fab in October 2024. This page covers what the catalog records for Unreal sources, the licence traps that are specific to Unreal, and where the Unreal entries are.

## What the catalog records

- `engine_lock: unreal` marks a licence that only permits use in Unreal Engine-based products. Epic writes this on a Fab listing as "UE-Only Content - Licensed for Use Only with Unreal Engine-based Products". The site shows a **UE only** badge. An entry without it may still be *made for* Unreal; it just carries no engine restriction that we could read.
- `ue_versions` is the engine range the source itself states (a Fab listing's "Unreal Engine versions" field, a README, a `.uplugin` or release names). Each entry's Notes say where it came from. It is not a range we tested.
- Unreal plugins are filed in `tools/` with the `unreal` subcategory and the `unreal-plugin` format. Unreal projects and content packs use the `Unreal` format. The site's Format filter has an **Unreal Engine** group covering both.

## The copyleft trap

The Unreal Engine EULA forbids mixing the engine with copyleft code or content. From [the EULA](https://www.unrealengine.com/eula/unreal) (2026-10-13): "you may not combine the Licensed Technology with code or content that is licensed under any of the following licenses: GNU General Public License (GPL), Lesser GPL (LGPL) (unless you are merely dynamically linking a shared library), or Creative Commons Attribution-ShareAlike License."

What that means for this catalog:

- **Plugins.** A GPL or LGPL Unreal plugin cannot ship in a UE game, so the validator rejects a copyleft licence on any entry with an Unreal format. [Mountea Dialogue System](../catalog/tools/mountea-dialogue-system.md) is MPL-2.0, which the EULA does not name; its entry explains the per-file obligation.
- **CC-BY-SA art.** [docs/licenses.md](licenses.md) treats CC-BY-SA as commercial-OK with share-alike. That holds for most engines, but **not for Unreal**: the EULA names it. Check aggregator entries (OpenGameArt, LPC sprites, Freesound) file by file before importing into an Unreal project.
- **GPL tools are fine.** Blender, GIMP, Krita and the other GPL editors in `tools/` are not combined with the engine; their output is yours. The clause is about code and content inside your Unreal project.

## Epic and Fab content: no public repositories

Epic's sample projects and Fab content may ship inside your built game, but not as source files to the public. From the [Epic Content License](https://www.unrealengine.com/eula/content) (2026-10-13): "you may not Distribute Licensed Content in source format to third parties except to employees, affiliates, and contractors who are utilizing the Licensed Content in good faith to develop a Project on your behalf". The [Fab EULA](https://www.fab.com/eula) Standard License summary says you may not "Resell or redistribute the asset for free on a standalone basis".

In practice: a public GitHub repository of an Unreal project must not contain the `Content/` folder of Lyra, Cropout, City Sample, Megascans or any other Fab download. Keep that content in a private repository or out of version control, and give collaborators their own Fab copy.

## Fab Standard License vs UE-Only Content

Most free Epic listings on Fab now sit under the **Fab Standard License**, whose summary says you may "Use the assets with any compatible tools (usage is not limited to Unreal Engine)" and that "You are not required to give credit". Some listings add a "UE-Only Content" line in their description, which narrows that. The catalog follows the narrower line where one is printed:

- Marked UE-only: [Lyra Starter Game](../catalog/3d/lyra-starter-game.md), [Cropout](../catalog/3d/cropout-sample-project.md), [Electric Dreams](../catalog/environment/electric-dreams-environment.md), and the Buildings, Vehicles and Crowds packs of [City Sample](../catalog/environment/city-sample.md).
- No UE-only line found: [Game Animation Sample](../catalog/animation/game-animation-sample.md), [Stack O Bot](../catalog/3d/stack-o-bot.md), the main City Sample listing and the [Paragon characters](../catalog/characters/paragon-characters.md). These stay `needs-review`: the listing grants the Standard License, but Epic has not said whether its older UE-only designation still applies.

## Megascans and MetaHuman

- **Megascans**: free claiming of the whole library ended at the end of 2024 (Epic's Fab launch post: "Acquire the Quixel Megascans library for free through the end of 2024"). Since January 2025 Epic gives a [free starter set](../catalog/3d/megascans-starter-content.md) under the Fab Standard License, with some tree packs and scenes Unreal-only. A Megascans clause in the Epic Content License still limits Megascans acquired outside a plan to "internal evaluation purposes", so the entry stays `needs-review` until Epic reconciles the two. Paid Megascans are covered by [fab-megascans-standard](../catalog/3d/fab-megascans-standard.md).
- **MetaHuman**: from UE 5.6 it is covered by the Unreal Engine licence and Epic says MetaHumans can be used with any engine. Over $1 million in annual revenue, rendering outside Unreal needs a UE seat licence. The Epic Content License still says acquired MetaHuman *content* "may only be used and shared as UE-Only Content". The [entry](../catalog/characters/metahuman.md) quotes all three and stays `needs-review`.
- **Free and Limited-Time Free listings** on Fab rotate every two weeks. The catalog lists [the program](../catalog/3d/fab-free-content.md), not individual giveaways; read each listing's licence.

## Where the Unreal entries are

- Plugins: [Unreal Engine plugins](../catalog/tools/README.md#unreal-engine-plugins) in `tools/`, with a pick per job (dialogue, saves, quests, event flow, bone physics, coroutines, debug UI, movement, GAS).
- Sample projects and content: [3D](../catalog/3d/README.md), [Animation](../catalog/animation/README.md), [Environment](../catalog/environment/README.md) and [Characters](../catalog/characters/README.md).
- Engine-neutral sources that work in Unreal: CC0 materials from [ambientCG](../catalog/3d/ambientcg.md) and HDRIs from [Poly Haven](../catalog/environment/poly-haven.md). Check each source's normal-map convention; Unreal expects DirectX-style (green down) normals.
- Mixamo: [mixamo](../catalog/animation/mixamo.md). Unreal's IK Rig editor can generate retarget chains automatically from bone names; Epic's documentation does not list Mixamo among its templates, so check the chains it builds.
