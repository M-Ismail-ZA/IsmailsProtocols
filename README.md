# Ismail's Protocols

*Rule-based evaluation protocols, built as portable AI skills*

[![content license](https://img.shields.io/badge/content--license-CC--BY--4.0-lightgrey)](./LICENSE-CONTENT)
[![code license](https://img.shields.io/badge/code--license-MIT-blue)](./LICENSE-CODE)
[![skills](https://img.shields.io/badge/skills-2-brightgreen)](./skills)

Ismail's Protocols hosts structured, rule-based protocols for the kinds of judgment calls that are easy to get wrong by instinct: whether a claim is actually well-supported, or whether a piece of writing has slipped into the flattened, formulaic register that AI tools default to. Each protocol ships as a Claude Skill — a `SKILL.md` trigger-and-procedure file plus a `references/` folder holding the actual rule content — and this repo documents, alongside the skills themselves, exactly how to carry the same rules onto other platforms: ChatGPT Custom GPTs, Google Gemini Gems, and (by the same pattern) anything else with an instructions field and a file-upload feature.

This is a companion project to [Ismail's Glossary](https://github.com/M-Ismail-ZA/IsmailsGlossary); where that repo is a navigation index for an existing body of knowledge (Mathlib4), this one is original rule protocols, built to be run rather than looked up.

## What's here

| Skill | What it does | Rules |
|---|---|---|
| [`ismail-credibility-checker`](./skills/ismail-credibility-checker) | Evaluates whether a claim, theory, or source is actually well-supported, separating validity from prestige and credentials | 8 rules, 2 depth tiers, 4 severity levels |
| [`ismail-ai-review`](./skills/ismail-ai-review) | Reviews and rewrites text against a house-style catalog of AI-writing fingerprints — inflated significance, formulaic rhetorical patterns, tool residue, citation integrity | 21 rules across 5 parts |

More protocols will be added here over time, following the same shape: a short trigger description, an explicit procedure, and reference content the procedure depends on.

## Repository structure

```
IsmailsProtocols/
├── README.md
├── ismail-credibility-checker.skill   -- packaged bundle, one-click upload to claude.ai
├── ismail-ai-review.skill             -- packaged bundle, one-click upload to claude.ai
├── skills/
│   ├── ismail-credibility-checker/
│   │   ├── SKILL.md
│   │   └── references/
│   │       ├── ruleset.md            -- the 8 rules, dependency-ordered
│   │       ├── application-layer.md  -- depth tiers, severities, message format
│   │       ├── motivation.md         -- why the protocol is built this way
│   │       └── evidence-audit.md     -- citation trail behind every rule
│   └── ismail-ai-review/
│       ├── SKILL.md
│       └── references/
│           └── rules.md              -- the full 21-rule catalog
├── porting/
│   ├── PORTING-GUIDE.md              -- platform-agnostic translation logic
│   ├── custom-gpts.md                -- worked ChatGPT Custom GPT setup
│   ├── gemini-gems.md                -- worked Google Gem setup
│   └── assets/
│       └── credibility-checker-core-protocol.md  -- pre-merged upload file
├── LICENSE-CONTENT
└── LICENSE-CODE
```

## Ismail's Credibility Checker

An eight-rule Epistemic Verification Protocol, reordered by dependency rather than by the order the rules were first drafted in: null position and medium/message as standing preconditions, a definitional audit that gates everything downstream of it, a verification hierarchy that treats formal proof and empirical consilience as separate ceilings rather than rungs on one shared ladder, then social signals and institutional authority as constraints on how that hierarchy gets applied, and burden of proof and epistemic agility as closing, standing checks.

It runs at one of two depths — **General Discovery** by default, or **First-Principles** on request, which recurses the citation-chain mechanism into every load-bearing source — and reports one of four severities (Disqualifying, Evidentiary Gap, Caution, Unresolved) rather than a binary pass/fail, because a binary collapses distinctions the ruleset itself makes. It never blocks a response; a flag annotates the specific claim it concerns and the rest of the answer proceeds normally.

The design is grounded in two named failure patterns — Nathan Ballantyne's "epistemic trespassing" (a credential from one field carrying unearned authority into another) and Norwood Hanson's theory-ladenness (same-domain experts reaching different conclusions because their training shaped what they treat as relevant evidence) — both covered in full in `references/motivation.md`, with the citation trail for every rule in `references/evidence-audit.md`.

## Ismail AI Review

A 21-rule house-style checklist adapted from Wikipedia's [*Signs of AI Writing*](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) essay, reorganized from a detection field guide into prescriptive writing rules across five parts: content and substance, language and grammar, formatting and punctuation, communication and provenance, and sourcing and citations. It includes a quick-reference table of words to strike on sight, and — deliberately — a "what not to police" section, since flagging a false positive (perfect grammar, one transition word, formal tone alone) erodes trust in the rest of the review faster than missing a real one does.

Output shape adapts to what's actually asked: a request to check or flag issues gets a findings list; a request to fix or polish gets the rewrite first; an open-ended request gets both. Content, numbers, names, and the strength of an argument are never altered in the process — this is a style pass, not a rewrite of substance.

## Installing directly in Claude

`ismail-credibility-checker.skill` and `ismail-ai-review.skill` are the same content as `skills/`, packaged as ready-to-upload bundles — each is just its skill folder zipped, with the extension renamed to `.skill` so it's recognizable at a glance. Unzipped, they're byte-identical to the source folders; the packaging exists purely for one-click installation, not as a different format.

To install: Settings → Capabilities → Skills → upload the `.skill` file. Both stay private to your account. The `skills/` folder stays the canonical, readable, diffable source — edit there, then re-zip to refresh the bundle.

## Porting to GPTs, Gems, and other platforms

The [`porting/`](./porting) folder documents how to carry each skill's rules onto platforms that don't read Claude's Skill format natively. The core translation is the same everywhere — a skill's trigger description becomes the platform's description field, its procedure becomes the instructions field, and its reference files become uploaded knowledge — but one structural difference matters enough to get its own section in [`PORTING-GUIDE.md`](./porting/PORTING-GUIDE.md): a Claude Skill can guarantee a reference file loads in full every time, where GPTs and Gems retrieve from uploaded knowledge by relevance, not by guaranteed full read. The porting docs merge dependent reference files before upload and say so explicitly in the instructions field, to close that gap as far as it can be closed from outside the platform.

[`custom-gpts.md`](./porting/custom-gpts.md) and [`gemini-gems.md`](./porting/gemini-gems.md) give copy-pasteable instructions-field text and a knowledge-file checklist for both skills currently in this repo, including the current character limits and file caps for each platform, sourced and dated so drift is visible rather than silent.

## Contributing

Issues and pull requests are open for: corrections to a rule's wording or dependency logic, additional worked porting docs for platforms not yet covered here (Perplexity Spaces, Poe, Microsoft Copilot declarative agents, and similar all fit the same three-piece translation), and new protocols that follow the existing shape — a trigger description, an explicit procedure, and reference content the procedure depends on. A protocol that changes what a rule requires should also update its citation trail; an unsupported rule is worse than no rule.

## Citation

```
Ismail, M. (2026). Ismail's Protocols: Rule-Based Evaluation Protocols for
Claude Skills and AI Platforms. GitHub. https://github.com/M-Ismail-ZA/IsmailsProtocols
```

```bibtex
@misc{ismail2026protocols,
  author = {Ismail, Muhammed},
  title  = {Ismail's Protocols: Rule-Based Evaluation Protocols for Claude Skills and AI Platforms},
  year   = {2026},
  publisher = {GitHub},
  url    = {https://github.com/M-Ismail-ZA/IsmailsProtocols}
}
```

## License

Split by kind, same reasoning as [Ismail's Glossary](https://github.com/M-Ismail-ZA/IsmailsGlossary#license):

- **Rule content** (every `SKILL.md`, every file under `references/`, the merged porting assets) — [CC BY 4.0](./LICENSE-CONTENT)
- **Instructional prose and tooling** (the porting guides' own explanatory text, any future scripts) — [MIT](./LICENSE-CODE)

`ismail-ai-review`'s rule catalog carries an additional share-alike obligation inherited from its Wikipedia source — see [`LICENSE-CONTENT`](./LICENSE-CONTENT) for the specific terms that apply to that skill.

## Author

Muhammed Ismail, Theoretical Mathematician 
GitHub: [M-Ismail-ZA](https://github.com/M-Ismail-ZA) · ORCID: [0009-0000-3713-7105](https://orcid.org/0009-0000-3713-7105)
