# Epistemic Protocol: Why This Exists

The ruleset, the application layer, and the evidence audit all answer to one animating observation: social signals are not validity, and qualifications are not competence. This document is that observation, argued out in full, so the rules aren't followed as arbitrary constraints—they're followed because the failure they prevent is common, specific, and worth naming precisely.

## Three ways a credential substitutes for the claim

**The credential doesn't match the domain.** A doctorate certifies training in a specific field, not general authority. It's common enough to have a name in philosophy: Nathan Ballantyne calls it ["epistemic trespassing"](https://philpapers.org/rec/BALET-2)—an expert in one field judging matters in another, carrying the confidence earned in the first field into a domain where it hasn't been earned. His central example is a Nobel laureate: Linus Pauling, a two-time Nobel winner (chemistry, and the peace prize for anti-nuclear-weapons activism), later argued that mega-doses of vitamin C could treat cancer, a claim the medical research on the question did not support. Two Nobel prizes in unrelated work didn't make him right about oncology. (The full case, and others like it, is in the evidence audit's Social Signals section—the point here is just that this is a named, recurring pattern, not a one-off.) One honest caveat: not every step outside a narrow specialty is illegitimate trespassing—critics of Ballantyne's account have pointed out that adjacent fields, worked in good faith, aren't the same as a hard boundary crossing. The operative test isn't "did they leave their field," it's whether the specific credential being leaned on actually certifies training in the specific question at hand.

**The credential matches the domain, and still doesn't converge.** This is the sharper problem, because "stay in your lane" doesn't solve it. Two psychologists, both legitimately credentialed in the same subfield, can disagree in good faith about the same clinical phenomenon because their training ran through different schools—psychodynamic, cognitive-behavioral, biological—each of which doesn't just supply different tools, it supplies a different lens on what counts as the relevant evidence in the first place. Norwood Russell Hanson named the general version of this in 1958: observation is ["theory-laden"](https://en.wikipedia.org/wiki/Theory-ladenness), shaped by the theoretical background the observer already holds, so two trained people can look at the same case and reach different conclusions—not because one of them is careless, but because their frameworks pick out different features as significant. Thomas Kuhn later extended this to whole scientific communities working in different paradigms. The upshot for this protocol: a credential tells you someone was trained. It doesn't tell you which of several legitimate lenses they were trained in, and that lens is doing real, unstated work in whatever they conclude.

**The credential is invoked as a shield.** Distinct from both of the above: sometimes a qualification or an affiliation isn't offered as relevant context, it's offered instead of an argument—"Harvard graduate," "McKinsey consultant," used as a backdrop meant to end the conversation rather than open it. This is the classical appeal to authority, and it's worth separating from the first two problems because it usually isn't an error of reasoning on the claimant's part—it's a rhetorical move, aimed at the audience's respect for the institution rather than the audience's judgment of the claim. It works precisely because it's rarely challenged directly.

## What actually counts

An artifact—a Lean proof, working code, a published dataset someone else can rerun—is a categorically stronger signal than any of the three problems above, for a simple reason: it doesn't ask anyone to trust a person's training, lens, or institution at all. It can be checked directly. That's most of why the hierarchy treats machine-checked proof as the ceiling for deductive claims, and it's why this protocol treats an artifact as the thing worth asking for when a claim is in dispute, instead of a name.

That said, an artifact is not automatically a free pass either, and this protocol doesn't treat it as one. A Lean proof can be entirely rigorous and still prove the wrong thing, if its definitions don't map onto what's actually being claimed about the world—that's the definitional audit, and it applies to an artifact exactly as much as it applies to a credential. The difference isn't that artifacts are beyond question. It's that an artifact's failure mode is checkable by anyone willing to look, where a credential's failure mode usually isn't checkable at all—it just has to be trusted or not.

## The operating principle

Separate the claim from the claimant, and validate the claim on its own terms. A claim's truth doesn't move because of who is holding it. A well-supported claim from a smallholder farmer with no formal training carries exactly the same weight as the identical claim from a billionaire investor with a name everyone recognizes—and a poorly-supported claim from the second person is exactly as weak as the same claim from the first. The null-position rule states this as a procedure: evaluate as though the source were anonymous. This document states it as the reason the procedure exists.

## Where this shows up in the rules

| Observation here | Operationalized by |
|---|---|
| A credential doesn't transfer across domains | Rule 6: Institutions Do Not Confer Infallibility |
| Same-domain credentials still diverge by training | Rule 6, and Rule 4's requirement to classify evidence on its own tier regardless of who presents it |
| Prestige or affiliation invoked as a shield | Rule 5: Recognize Social Signals as Marketing, Not Truth |
| Artifacts outrank credentials, but aren't a free pass | Rule 4 (ceiling by claim type), gated by Rule 3: Audit the Definitions |
| The claim stands apart from the claimant | Rule 1: Assume the Null Position |

Rule numbers above follow the reordered ruleset, not the evidence audit's original numbering—the two documents number the same eight rules differently on purpose, since the audit preserves the order they were first presented in. A translation key at the top of the evidence audit converts between the two.

---

*This is the fourth and last of the supporting files: the evidence audit backs each rule with precedent, the ruleset states the rules, the application layer defines how they're invoked and reported, and this file is why any of it was worth building. Together they're what skill-creator would draw from—this document most naturally becomes the skill's own framing or description, rather than an instruction it executes at run time.*
