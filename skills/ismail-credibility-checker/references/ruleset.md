# Epistemic Verification Protocol: Ruleset

Operative version. Reordered by dependency; reduced to actionable content only. Rationale, citations, case studies, and open debates for every rule below live in the companion document, `references/evidence-audit.md`—nothing here restates them, and nothing here introduces a position that document doesn't already support. How these rules get invoked and reported—depth, severity, message format—is a separate concern, covered in `references/application-layer.md`; citation-chain recursion (Rules 3, 5, 6) and the tier that executes it are defined across both files together.

## Rule order and mapping

| Step | Rule | Tag | Originally |
|---|---|---|---|
| 1 | Assume the Null Position | `null-position` | Rule 1 |
| 2 | Separate the Medium from the Message | `medium-message` | Rule 2 |
| 3 | Audit the Definitions | `definitional-audit` | Rule 5 |
| 4 | Establish the Hierarchy of Verification | `verification-hierarchy` | Rule 3 |
| 5 | Recognize Social Signals as Marketing, Not Truth | `social-signals` | Rule 4 |
| 6 | Institutions Do Not Confer Infallibility | `institutional-authority` | Rule 6 |
| 7 | Burden of Proof, and Tools That Shift It | `burden-of-proof` | Rule 7 |
| 8 | Maintain Epistemic Agility | `epistemic-agility` | Rule 8 |

**Why the order changed:** the original numbering ran the hierarchy check (originally Rule 3) before the definitional audit (originally Rule 5). But a tier can't be assigned to a claim whose definitions haven't been confirmed to hold up—a high tier on a mis-specified claim is a strong proof of the wrong thing, not a strong claim. The definitional audit now runs first, and gates the hierarchy check rather than following it. Social signals (originally Rule 4) and institutional authority (Rule 6) are both constraints on how the hierarchy check is carried out, not independent steps, so they now sit immediately after it instead of on either side of it. Rules 1, 2, 7, and 8 kept their position: 1 and 2 are preconditions for everything else, and 7 and 8 concern what to do once a tier is established and how to keep the whole protocol current—both of which presuppose the rest has already run.

## The governing test

Every rule below serves one question: given the resources and the general direction of the claim and its proposed answer, could this be reproduced—independent of who is making it, what backs it, or how it is presented? No rule below is a substitute for asking that directly; each exists to make the answer reliable.

---

## Rule 1: Assume the Null Position `null-position`

**Dependency:** standing precondition for every rule below.

**Statement:** Treat every new claim as an untested hypothesis until evaluated. Assign it no quality judgment before establishing exactly what it asserts.

**Apply by:**
- Write out the claim's exact content before forming any opinion of it.
- Evaluate the claim as though its source were anonymous. A prestigious name does not raise the prior; an unfamiliar one does not lower it.
- Treat any impulse to excuse a weakness before checking whether it exists as positive skew, and any impulse to dismiss before checking as negative skew. Both are reasons to slow down, not to proceed.

---

## Rule 2: Separate the Medium from the Message `medium-message`

**Dependency:** Rule 1.

**Statement:** The clarity or density of a claim's presentation carries no information about whether it is true. Evaluate the content, not the packaging.

**Apply by:**
- Restate the claim in plain language before judging it, scoped to its definitions and foundational framing—not the full derivation built on top of them. That scope is what makes this step cheap; do not extend it to a full-document translation.
- If a translation tool (including an LLM) is used for this step, treat its output as a lead, and check it against the original wording for anything load-bearing.
- Apply equal scrutiny to a claim in accessible language as to one in dense jargon. Neither is evidence of validity.

---

## Rule 3: Audit the Definitions `definitional-audit`

**Dependency:** Rule 2 (requires the plain-language restatement).

**Statement:** A claim is only as good as whether its definitions map onto the thing it claims to be about, regardless of how it is later verified. The same test applies to any source cited in its support: a citation is only as good as whether its content maps onto the specific point it is cited for, not merely a shared topic or vocabulary. This audit gates Rules 4 through 6.

**Apply by:**
- Read the definitions before any evidence, proof, or verification attached to them.
- Check whether the definitions are comprehensive, and whether they narrow the claim to make it trivially true or diverge from what the claim is understood to mean in ordinary use.
- Extend the audit to citations: check whether a cited source's content substantively bears on the exact point it supports, or only shares a topic, a keyword, or a vocabulary with it. A source that is fully credible on its own terms but answers a different question does not satisfy this audit for the point it is attached to.
- Treat a failed audit as disqualifying, regardless of the claim's tier under Rule 4 or any institutional backing under Rule 6. No downstream rule overrides a definitional failure.
- Treat a passed audit as a precondition, not a conclusion. It clears the claim for evaluation under Rule 4; it does not establish the claim.

---

## Rule 4: Establish the Hierarchy of Verification `verification-hierarchy`

**Dependency:** Rule 3.

**Statement:** Evidence for a claim sits on a spectrum whose achievable ceiling depends on what kind of claim it is. Deductive claims (mathematical, logical) can reach machine-checked formal proof; that proof is complete on its own terms and needs no empirical confirmation to be accepted. Inductive claims (empirical, scientific) cannot reach that rung by definition—their ceiling is consilience: independent, unrelated methods or lines of evidence converging on the same conclusion; that convergence is complete on its own terms and needs no formal proof to be accepted. Neither ceiling outranks the other, and neither substitutes for or validates the other—they answer different questions about different kinds of claims, not two milestones on one shared scale.

**Apply by:**
- Classify the claim as deductive or inductive before choosing a ladder. Do not require formal proof of an inductive claim, and do not require consilience of a narrow, single-domain finding that makes no paradigm-level assertion.
- Deductive ladder: anecdote → peer-reviewed publication → reproduced computation → machine-checked formal proof.
- Inductive ladder: anecdote → peer-reviewed publication → single reproduced result → consilience.
- Do not require a deductive claim to also clear the inductive ladder, or an inductive claim to also clear the deductive one. A proof needs no real-world confirmation to be accepted as proof; convergent empirical evidence needs no formalization to be accepted as strong evidence. Treating the two as needing to confirm each other is the same category error as demanding the wrong ladder's ceiling, run between claim types instead of within one.
- When a formal result is applied to a real-world claim (a proven algorithm is asserted to solve an actual problem well; a proven model is asserted to describe an actual system), treat the application as a separate, additional inductive claim, not an extension of the original proof. Audit the application under Rule 3 and hold it to the inductive ladder on its own terms; this does not require retroactively adding empirical evidence to the original proof, which remains complete as a deductive claim regardless of how the application fares.
- A higher rung reduces only the work needed to confirm internal logic or empirical repeatability. It does not substitute for Rule 3's audit; an objection aimed at the definitions is not defeated by a higher rung just because the objection itself wasn't formalized.
- Before accepting a consilience claim: confirm the converging methods are genuinely independent (distinct failure modes, not shared assumptions), and confirm the match is a shared causal or structural mechanism, not a shared surface number. Where feasible, test the method against a case with no reason to produce the same result; a "match" that appears there too is a property of the method, not the claim.
- A claim's internal or formal correctness at any rung does not guarantee it will cohere with ordinary common sense (the anecdotal rung). The two check different things; neither is dispensable on its own.
- When a claim rests on a cited source, classify that source on this same hierarchy independently. The support it lends the main claim is capped at whatever tier the source itself has actually earned—an anecdote cited in defense of a claim does not become stronger evidence because the claim citing it is otherwise well presented.

---

## Rule 5: Recognize Social Signals as Marketing, Not Truth `social-signals`

**Dependency:** Rule 4.

**Statement:** Citation counts, journal prestige, author affiliation, and volume of discussion measure attention, not accuracy. They do not raise or lower a claim's tier under Rule 4.

**Apply by:**
- When classifying a tier under Rule 4, set aside venue, author institution, and citation count; assign the tier as if the source were anonymous, consistent with Rule 1.
- Treat high discussion volume as evidence a topic is salient, not as evidence it is correct.
- If a claim's certifying venue has a direct interest in the outcome (self-published, self-reviewed, or reviewed by the claimant's own institution), treat that as a reason for the added scrutiny in Rule 6, not as a neutral fact.
- Apply this rule recursively: a cited source's prestige, venue, or popularity carries the same zero evidentiary weight as the main claim's. That the claim's author correctly avoided prestige-based reasoning does not mean the sources they cite are exempt from the same treatment.

---

## Rule 6: Institutions Do Not Confer Infallibility `institutional-authority`

**Dependency:** Rule 4.

**Statement:** A credential, editorial seat, or institutional affiliation is evidence of training, not evidence of an absence of error. Weigh an objection on its content, not on the standing of whoever raises or defends it.

**Apply by:**
- Read "the community agrees" as "people with similar training have not yet found an obvious flaw"—a starting point for checking, not a stopping point.
- Do not treat a claim's tier under Rule 4 as overriding an institutional or community objection unless that objection has been evaluated on its content. If the objection targets Rule 3's definitional question, answer it on that question; do not dismiss it for lacking the claim's own level of formality.
- Apply this rule recursively, to citations and to individuals: a cited source's institutional backing, and an author's own track record of having been right before, do not confer infallibility on this specific claim. A well-established figure being wrong in one instance needs no special explanation—it needs the same audit as anyone else's claim.

---

## Rule 7: Burden of Proof, and Tools That Shift It `burden-of-proof`

**Dependency:** Rules 4 through 6.

**Statement:** Whoever asserts a claim carries the burden of supporting it. Unfalsifiability and unfamiliarity are not reasons to assume a claim true, and absence of a rebuttal is not evidence of one. Separately: tools that did not previously exist now let an evaluator personally close evidence gaps that once required deferring to authority.

**Apply by:**
- Do not fill an evidentiary gap with charity toward the claimant. A claim that has not met its burden under Rule 4 stays at the tier it has actually earned.
- Distinguish two uses of a tool such as an LLM: answering from memory (unverified—treat as a lead only) versus driving search and retrieval that produces independently checkable sources (verified, once checked against the source). Only the second counts as closing a gap.
- Apply the same standard to a formal verification tool: its output counts as evidence only once Rule 3 has confirmed that what it checked is what the claim actually asserts.

---

## Rule 8: Maintain Epistemic Agility `epistemic-agility`

**Dependency:** standing review condition over Rules 1 through 7.

**Statement:** The tools and methods available for verification change. Treat every rung, ceiling, and threshold in Rules 1 through 7 as revisable as better tools become available. Do not defend a current standard on the grounds that it is traditional.

**Apply by:**
- When a new verification method becomes available (a formal checker, a large-scale replication effort, a new measurement technique), re-evaluate whether a claim previously accepted at a lower tier can now be checked at a higher one.
- Do not treat the absence of a tool in the past as a reason to withhold scrutiny a tool now makes possible.
- Periodically re-examine this protocol against its own standard: has a new method changed what is checkable, such that a rule above should tighten or loosen.

---

*Ready to become the source for a SKILL.md when you are—skill-creator can turn the rule order, tags, and dependency notes above directly into trigger conditions and instructions.*
