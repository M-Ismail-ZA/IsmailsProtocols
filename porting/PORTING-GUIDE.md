# Porting Guide: From Claude Skill to Any Platform

Every skill in this repo is written as a Claude Skill — a `SKILL.md` plus a `references/` folder — because that format forces a useful discipline: a short trigger description, an explicit instruction to load specific reference files in full before acting, and a clean separation between what the model needs at run time and what it only needs when asked to explain itself. That discipline is what this guide carries over to other platforms. It isn't Claude-specific in substance, only in file format.

This document covers the general translation. `custom-gpts.md` and `gemini-gems.md` give the exact, worked version for each platform, including copy-pasteable field contents for both skills currently in this repo.

## The three-piece translation

Every Claude Skill in this repo maps onto three fields that Custom GPTs, Gems, and most competitor "custom agent" builders all have some version of, even though they name them differently.

| Skill piece | What it is | Maps to |
|---|---|---|
| `SKILL.md` frontmatter `description` | The trigger condition — when this should activate | The platform's short-form **description** or **blurb** field |
| `SKILL.md` body, "How to \_\_\_" section | The procedure — the actual steps to run | The platform's **Instructions** / **System instructions** field |
| `references/*.md` | The full rule content the procedure points at | The platform's **Knowledge** / **uploaded files** feature |

The frontmatter is easy — it's already written as a trigger condition, so it usually just needs light trimming for length. The instructions and the references are where the real porting work happens, because of one structural difference between platforms that this repo treats as load-bearing, not cosmetic.

## The gap that actually matters: guaranteed load vs. best-effort retrieval

A Claude Skill can say, and mean, "load `references/ruleset.md` and `references/application-layer.md` in full before evaluating anything" — both files land in context, completely, every time the skill runs. `ismail-credibility-checker/SKILL.md` depends on this directly: Rule 3 gates Rules 4 through 6, the application layer defines severities that the ruleset never mentions, and neither file is safe to run from a model's paraphrased memory of what it probably says.

Custom GPTs and Gems don't offer that guarantee. Both retrieve from uploaded Knowledge files by relevance to the current query — a form of retrieval-augmented search, not a full-file load. For a short, single-file skill like `ismail-ai-review`, this rarely matters in practice: `rules.md` is one file, read start to finish, and most real queries pull enough of it in to work. For a multi-file, dependency-ordered protocol like `ismail-credibility-checker`, it matters a lot: a partial retrieval that pulls in Rule 4 without Rule 3 having gated it first isn't running the protocol, it's running a fragment of it.

Two mitigations, used together in `custom-gpts.md` and `gemini-gems.md`:

1. **Consolidate before uploading.** Where a Skill splits content across files for Claude's own context-management reasons (so it doesn't load `evidence-audit.md`'s 56K unless someone asks why a rule should be trusted), a GPT or Gem's Knowledge base doesn't benefit from that split — it costs retrieval reliability instead. The porting docs below merge `ruleset.md` and `application-layer.md` into one knowledge file for both platforms, since those two are meant to be read together every time regardless of engine.
2. **Say so in the instructions field, explicitly.** Every instructions draft in this repo's porting docs includes a line telling the model to treat the merged core-protocol file as required reading in full for every check, not an optional reference — because on a retrieval-based platform, an instruction saying so is the only lever available, where a Claude Skill gets the same behavior structurally.

`evidence-audit.md` and `motivation.md` stay as optional, lower-priority Knowledge uploads on every platform — the instructions never require them, matching how the Claude Skill itself treats them as background, loaded only if someone asks why a rule should be trusted.

## General workflow, any platform

1. Read the skill's `SKILL.md` frontmatter `description` — this is your trigger condition and description field, near verbatim.
2. Read the "How to ___" section in the body — this is your instructions field, usually needing compression to fit a character limit (see the platform-specific docs for current limits).
3. Decide which `references/*.md` files are required reading vs. optional background, using the skill's own "What this skill contains" section as the guide — it already states this distinction.
4. Merge required-reading files that depend on each other into a single upload, and say in the instructions field that the merged file must be treated as required, full-context reading.
5. Upload optional/background files separately, and reference them by name in the instructions ("if asked why a rule should be trusted, consult `evidence-audit.md`") so the model knows they exist without treating them as load-bearing.
6. Preserve the skill's own output-format rules verbatim wherever they exist — `ismail-credibility-checker`'s message template and `ismail-ai-review`'s "match the output to what was actually asked" logic are both platform-agnostic and shouldn't be paraphrased away during porting.

## Platform notes

Field names, character limits, and file caps on any external platform can change without notice — the two docs in this folder cite what was current as of this repo's last porting-doc update, with sources. Before relying on a specific number, check the platform's own current documentation; this repo will drift out of date faster than the underlying skills do.

- [`custom-gpts.md`](./custom-gpts.md) — ChatGPT Custom GPTs
- [`gemini-gems.md`](./gemini-gems.md) — Google Gemini Gems

The same three-piece translation applies to other "custom agent" builders not yet documented here (Perplexity Spaces, Poe bots, Microsoft Copilot declarative agents, and similar): find that platform's equivalent of a description field, an instructions field, and a file-upload/knowledge feature, and apply the workflow above. A pull request adding a worked doc for any of these is welcome — see the root README's Contributing section.
