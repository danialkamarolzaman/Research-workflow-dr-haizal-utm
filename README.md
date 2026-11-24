# Researcher Workflow

A reusable AI skill for critically reviewing research manuscripts across disciplines. It connects literature synthesis, gap assessment, scholarly writing, peer-review critique, and evidence verification in one seven-stage workflow.

The skill supports quantitative, qualitative, mixed-methods, theoretical, computational, humanities, and evidence-synthesis research. Checks are selected for the study's design and evidence.

## Workflow

| Stage | Purpose |
| --- | --- |
| 1. Interrogate | Challenge the research problem, assumptions, evidence, and alternative explanations. |
| 2. Synthesize | Connect literature patterns, differences, trade-offs, and unresolved issues. |
| 3. Identify the gap | Assess the gap and contribution against the available prior work. |
| 4. Structure | Build an evidence-linked argument from problem to contribution. |
| 5. Write | Diagnose, organize, and revise the requested section. |
| 6. Attack | Critique novelty, methodology, validation, and significance. |
| 7. Verify | Audit claims, citations, calculations, interpretations, and consistency. |

A full review feeds the final critique and verification back into the draft, then provides prioritized research actions and a readiness judgement limited to the reviewed evidence. Focused requests can use individual stages without implying a complete review.

## Install in Codex

Place this repository's contents in a folder named `researcher-workflow` under your Codex skills directory. The default location is `~/.codex/skills`; use `$CODEX_HOME/skills` if you have configured a different Codex home.

For a fresh installation using PowerShell:

```powershell
$researchSkillsRoot = if ($env:CODEX_HOME) {
    Join-Path $env:CODEX_HOME 'skills'
} else {
    Join-Path $HOME '.codex/skills'
}
New-Item -ItemType Directory -Path $researchSkillsRoot -Force | Out-Null
git clone https://github.com/danialkamarolzaman/researcher-workflow.git (Join-Path $researchSkillsRoot 'researcher-workflow')
```

If the destination already contains an installed skill, keep your existing copy and review changes before replacing it. A private repository requires GitHub access to clone.

## Use

Attach or provide access to your manuscript and relevant sources, then invoke:

```text
Use $researcher-workflow to review my manuscript and supporting literature.
Apply all seven stages, revise the Introduction, and produce a prioritized
evidence-based action plan.
```

For a narrower task:

```text
Use $researcher-workflow to assess the research gap using these supplied
papers. Do not rewrite the manuscript.
```

```text
Use $researcher-workflow to verify the claims in my Results and Discussion.
Separate reported findings, supported interpretations, and unresolved claims.
```

Useful inputs include the manuscript, research question, proposed contribution, supporting literature or primary sources, data and analytic records, target section, and any journal or formatting requirements. The Introduction is the default writing target for a full review.

## Evidence boundaries

- Uses supplied sources by default; external searching requires user authorization.
- Links consequential findings to identifiable source locations.
- Distinguishes reported evidence, inference, hypotheses, and missing information.
- Never treats internal consistency as independent validation.
- Does not invent citations, findings, or completed research activities.
- Preserves original files unless edits are requested.
- Keeps research decisions and submission approval with the author.

The workflow assists critical review; it does not certify research validity or guarantee publication. Missing evidence remains visible in the output.

## Repository structure

```text
researcher-workflow/
  SKILL.md                         Skill entry point and shared rules
  agents/openai.yaml               Display metadata and example invocation
  references/seven-step-workflow.md Full procedure and output requirements
```

Start with [SKILL.md](SKILL.md), or read the [full seven-step procedure](references/seven-step-workflow.md).
