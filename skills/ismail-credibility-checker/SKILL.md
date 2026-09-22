---
name: ismail-credibility-checker
description: "Evaluates whether a specific claim, theory, study, or source is actually well-supported, separating validity from social signals (prestige, credentials, citation count) via an eight-rule protocol with a domain-appropriate evidence hierarchy—formal proof for deductive claims, consilience for empirical ones. Runs at General Discovery depth by default; First-Principles depth traces citation chains to primary sources, on request only. Use whenever the user asks to fact-check, credibility-check, verify, or scrutinize a specific claim, study, argument, or source; asks 'is this true,' 'can I trust this,' or 'check this citation'; shares a claim or article for a second opinion; questions whether a credential or prestigious name makes a claim more trustworthy; or names 'Ismail's Credibility Checker' directly. Do not run automatically on every statement Claude makes—only on an explicit or clearly-implied request to evaluate a specific claim."
---

# Ismail's Credibility Checker

Evaluates whether a specific claim, theory, or source is actually well-supported, using an eight-rule protocol that separates validity from prestige, credentials, and institutional affiliation.

Created by Muhammed Ismail (independent researcher). GitHub: M-Ismail-ZA | ORCID: 0009-0000-3713-7105

---

## What this skill contains

`references/ruleset.md` holds the eight operative rules, in dependency order, each with a statement and concrete apply-by steps. This is the core of the skill—load it in full for every check.

`references/application-layer.md` defines the two depth tiers (General Discovery, First-Principles), the four severity levels (Disqualifying, Evidentiary Gap, Caution, Unresolved), and the exact message format for reporting a flag. Load it in full alongside the ruleset—the ruleset says what to check, this says how to report it.

`references/motivation.md` explains why the protocol treats credentials, institutions, and social signals the way it does, with the two named failure patterns behind it (a credential that doesn't match the domain; a credential that matches the domain but doesn't converge with an equally-credentialed peer's). Read it if the reasoning behind a rule needs explaining to the user—it isn't needed to run the check itself.

`references/evidence-audit.md` is the full citation trail backing every rule, including the contested points and the studies that complicate them. It's background for verifying the protocol's own credibility, not something this skill needs to load to evaluate a claim—don't read it by default; point to it if the user asks why a rule should be trusted.

## How to check a claim

### 1. Read the ruleset and application layer first
Load `references/ruleset.md` and `references/application-layer.md` in full before evaluating anything. Do not evaluate from memory of what the rules probably say.

### 2. Isolate the claim
State exactly what's being asserted, separately from how it's phrased and who's presenting it (Rules 1–2). This exact statement is what every later rule evaluates—not a stronger or weaker version of it, and not the general topic it belongs to.

### 3. Determine depth before doing any checking
General Discovery is the default and runs unless told otherwise. Only run First-Principles if the user names it directly, or after this skill offers to go deeper and the user agrees. Never assume First-Principles depth, and never silently upgrade or downgrade depth mid-check.

### 4. Work through Rules 1 through 7 in the order given in the ruleset
Each rule depends on the one before it—Rule 3 (audit the definitions, including any cited sources) gates Rules 4 through 6, and a failure there is disqualifying regardless of what a later rule would otherwise find. Do not skip ahead to Rule 4's hierarchy check before Rule 3 has passed. Rule 8 is a standing check, not a sequential step: while working through the others, note whether a stronger form of evidence now exists for this claim than what it originally cited (a since-published formal proof, a since-completed replication), and use it if so.

### 5. At First-Principles depth, apply the citation-chain mechanism to every load-bearing source
Recurse Rules 3, 5, and 6 into each source the claim relies on, and into each source that source relies on, following the application layer's proportionality test and stopping conditions. Report **Unresolved**, with the trace as far as it got, rather than continuing indefinitely or stopping without saying so.

### 6. Report using the application layer's format exactly
Name the tier that ran. Name the specific rule any flag concerns, by number and short name. State the specific gap in a sentence or two—not a restatement of the rule itself. A clean result is reported as clearing every check run at that depth, never as the claim "being true."

### 7. Never block on a flag
A flag annotates the specific claim it concerns. Deliver the rest of the response normally around it.

---

## Notes

This protocol was checked against real precedent before being finalized—every rule in `references/ruleset.md` has a citation trail in `references/evidence-audit.md`, including places where the supporting research has its own published critics, and one real tension (between Rule 3's definitional audit and Rule 4's verification hierarchy) that changed how both rules are worded here. It was reordered from its original presentation by dependency, not by importance—see the numbering key at the top of `references/evidence-audit.md`, which keeps the original order and needs a translation to match this skill's numbering.

Rule 4 treats machine-checked formal proof and consilience as the ceilings of two separate ladders, not two rungs on one shared scale. A deductive claim (a theorem) needs no empirical confirmation to be accepted; an inductive claim (an empirical finding) needs no formal proof to be accepted. When a formal result is applied to something real—a proven algorithm asserted to solve an actual problem—that application is a separate, additional empirical claim with its own inductive ceiling, not an extension of the original proof. Do not require a claim to clear both ladders, and do not let a claim's strength on one ladder stand in for the other.
