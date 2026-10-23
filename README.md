# English Less AI Tone

[中文说明](README.zh-CN.md)

An agent skill for conservative editing of completed English drafts. It reduces formulaic, padded, or unnecessarily defensive phrasing while preserving meaning, facts, qualifications, citations, register, and document structure.

**Change only clear rule matches. Leave everything else unchanged.**

## Install

With the [Skills CLI](https://github.com/vercel-labs/skills):

```bash
npx skills add chows3539-droid/english-less-ai-tone
```

For a global Codex installation:

```bash
npx skills add chows3539-droid/english-less-ai-tone --global --agent codex
```

Alternatively, clone the repository into a skills directory supported by your agent. For a standard Codex setup:

```bash
git clone https://github.com/chows3539-droid/english-less-ai-tone.git "${CODEX_HOME:-$HOME/.codex}/skills/english-less-ai-tone"
```

Use this command only if the destination does not already exist. Managed ChatGPT Work environments may require their own skill import or persistence workflow. Restart or refresh your agent's skill list if it does not discover the skill immediately.

## Use

```text
Use $english-less-ai-tone to edit the following English draft.
Preserve its meaning, facts, citations, qualifications, structure,
and level of formality. Return only the revised text.

[paste your draft]
```

For an explanation, add: `Show each change with its rule ID.`

For grammar corrections, add: `Also proofread the grammar and identify those edits separately.` Grammar correction is outside the default style-only scope.

## Editing rules

| Rule | What it targets |
| --- | --- |
| E1 | Empty announcements or importance wrappers |
| E2 | Redundant multiword expressions |
| E3 | Light-verb constructions that hide an action |
| E4 | Adjacent sentences repeating the same proposition |
| E5 | Additive grand framing that can be simplified without losing emphasis |
| E6 | Repeated additive transitions within one paragraph |
| E7 | Repeated mechanical sentence frames |
| E8 | Empty self-protective wrappers |
| E9 | Direct scope statements that retain substantive exclusions |
| E10 | Duplicate uncertainty without stronger claims |

Each rule includes conditions and exceptions. Read [SKILL.md](SKILL.md) for the actual instructions.

The skill preserves meaningful uncertainty, negations, conditions, technical terms, quotations, citations, headings, paragraphs, and lists. It does not ban em dashes, passive voice, academic vocabulary, or particular words. Formal writing stays formal.

## Examples

### Shorten without changing facts

Before:

> It is worth noting that the survey included 42 participants. The team met in order to review the responses.

After:

> The survey included 42 participants. The team met to review the responses.

### Keep qualifications and comparisons

Unchanged:

> The findings may indicate an association, not a causal effect.

### Keep technical language

Unchanged:

> The team conducted a sensitivity analysis. The result could potentially reflect selection bias.

Examples are illustrative, not evidence of authorship or effectiveness against a detector.

## Anti-defensive writing

The skill also integrates selected principles from [Kiterlin/anti-defensive-writing](https://github.com/Kiterlin/anti-defensive-writing). It removes empty self-protective wording, leads with the stated scope while retaining exclusions, and reduces duplicate uncertainty without increasing certainty. It preserves genuine apologies, conceptual contrasts, methodological limits, negative findings, and safety or legal restrictions.

For example, `The difference may perhaps reflect selection bias` can become `The difference may reflect selection bias`. `The study does not establish causality` stays unchanged.

The integration remains local: it does not import upstream paragraph restructuring, move caveats into other sections, or replace uncertainty with unsupported confidence.

## Scope and limitations

- Designed for English academic drafts, IELTS essays, emails, reports, and other completed prose.
- In mixed-language drafts, only English prose is in scope.
- Not a general proofreader, translator, fact checker, or automatic rewriting script.
- Not an AI detector. It cannot determine who wrote a passage or guarantee any detector result or IELTS score.
- The English rules are editorial heuristics, not empirically validated findings. Results depend on the model applying the skill and still need human review.

## Origin and license

This is an independent English adaptation of the whitelist-and-preservation approach in [larashero3-dotcom/lieflat-less-ai-tone](https://github.com/larashero3-dotcom/lieflat-less-ai-tone). It is not an official English release or a translation of that project's Chinese rules. The upstream Chinese corpus statistics do not validate the English rules here.

Created with assistance from ChatGPT. Published under the [MIT License](LICENSE), retaining both upstream copyright notices. The anti-defensive source was reviewed at commit `f516147d017a3fe43ae99192cb89d8261b0c8679`; E8–E10 are a selective adaptation, not the complete upstream skill or an official release.
