# Skill Authoring Notes

## Purpose

This SEO audit skill is split into a small `SKILL.md` plus direct reference files to avoid loading a long SEO encyclopedia into the model context on every invocation.

## Design rules used

- `SKILL.md` is the operating script and routing table.
- Detailed guidance lives in one-level reference files under `references/`.
- Each reference file is linked directly from `SKILL.md`.
- Long reference files start with a table of contents.
- The main skill avoids evergreen SEO explanations that most models already know.
- The skill is written as a workflow, not as a textbook.
- The skill requires evidence for every finding.

## Maintenance rules

- Keep `SKILL.md` under 500 lines.
- Do not add large source lists to `SKILL.md`; put them in `references/10-source-corpus.md`.
- Do not create nested references like `references/google/details.md`; keep all files directly linked from `SKILL.md`.
- Add new regional guidance to `references/07-international-regional.md`.
- Add new command examples to `references/09-cli-checks.md`.
- If SEO facts may have changed, update the source corpus and the corresponding reference file.

## Evaluation prompts

Test the skill with at least these cases:

1. “Audit https://example.com for SEO.”
2. “We migrated from old.com to new.com; check SEO risks.”
3. “Check why my React SPA is not indexed.”
4. “Audit a Russian-language commercial site for Google and Yandex.”
5. “Create a 30/60/90 SEO roadmap from these audit findings.”

A good result must:

- Ask only necessary clarifying questions.
- Run or request evidence-based checks.
- Distinguish verified findings from assumptions.
- Prioritize by business and indexability impact.
- Produce actionable fixes and verification steps.
