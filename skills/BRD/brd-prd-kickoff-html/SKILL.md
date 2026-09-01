---
name: brd-prd-kickoff-html
description: Create reusable Traditional Chinese kickoff, initial meeting, project briefing, or developer handoff HTML pages from BRD and PRD Markdown files. Use when AM, PM, or delivery teams need to convert the first chapters of BRD/PRD documents into a single-file HTML meeting page with business background, product overview, users, stakeholders, core requirements, open items, and schedule/cost placeholders.
---

# BRD PRD Kickoff HTML

## Purpose

Create a reusable, single-file HTML meeting page from BRD and PRD source documents. The output should help AM, PM, product, and engineering teams align on project background, scope, users, permissions, business requirements, and early delivery concerns before implementation starts.

This skill is intentionally project-agnostic. Do not assume a specific client, brand, industry, product name, color system, or source folder.

## Bundled Template

Use `assets/kickoff-demo-template.html` as the default structural and visual reference when the user does not provide a better project-specific HTML sample. This bundled template uses the Aiii default brand color system from `create-meeting-html/references/default-aiii-color-guidelines.md`.

Treat the bundled template as a starting point, not as final content:

- Replace every `{{placeholder}}` with source-derived content or `待補` / `待確認`.
- Keep the section IDs and class names unless a project-specific template uses different names.
- Reuse the CSS structure for compact cards, source notes, tables, feature blocks, and collapsible long sections.
- Adjust colors only when the user provides brand guidance or an existing reference HTML. If no brand guidance exists, keep the Aiii default tokens from the bundled template.

If the user provides a reference HTML, inspect that file and prefer its CSS tokens, typography, section order, and component patterns over the bundled demo template.

## Required Inputs

Inspect local files directly when paths are available. Ask only for inputs that cannot be inferred safely.

- BRD Markdown path.
- PRD Markdown path.
- Output HTML path.
- Optional reference HTML path.
- Optional meeting context: meeting date, audience, purpose, desired sections, brand rules.

If the user only gives a project folder, locate likely files by filename patterns:

- BRD: `*_BRD.md`, `*BRD*.md`, or files under a BRD-related folder.
- PRD: `*_PRD.md`, `*PRD*.md`, or files under a PRD-related folder.
- Reference HTML: files under `handoff/`, `meeting/`, `reference/`, or filenames containing `說明`, `handoff`, `kickoff`, `meeting`, `briefing`.

## Source Scope

Build the first draft mainly from the first three major chapters of BRD and PRD:

- BRD: `## 1` through before `## 4`.
- PRD: `## 1` through before `## 4`.

Use later chapters only when they are needed for sections commonly expected in a kickoff page:

- Stakeholders / owners.
- Cost days.
- Timeline, milestones, launch target.
- Risks, constraints, and open items.
- Appendix notes that clarify a core requirement.
- Prototype or demo status, if the user requests it or the reference HTML contains it.

Do not let later technical chapters turn the kickoff page into a full PRD, STD, SDD, or implementation spec.

## Extraction Workflow

1. Read the BRD and PRD table of contents or heading list first.
2. Extract BRD chapter 1 as target audience, role definitions, access rules, and permission summary.
3. Extract BRD chapter 2 as project background and business pain points.
4. Extract BRD chapter 3 as core business requirements and business rules.
5. Extract PRD chapter 1 as project goals, business value, and product scope.
6. Extract PRD chapter 2 as user personas, tasks, permissions, and usage scenarios.
7. Extract PRD chapter 3 as functional requirements and user stories mapped to BRD chapter 3.
8. Extract optional stakeholder, cost, timeline, risk, appendix, or demo notes only when relevant.
9. Generate the HTML by filling the chosen template structure with concise summaries.
10. Validate links, anchors, responsive tables, and missing-data labels.

## Default Output Sections

Use this section order unless the user or reference HTML asks for a different order:

1. Header: project name, meeting purpose, source note.
2. Navigation: anchors to every major section.
3. `1. 專案背景與痛點`: summarize BRD chapter 2. Present each pain point as a card with problem and impact.
4. `2. 專案簡介`: summarize PRD chapter 1. Include project goals, business value, product scope, and out-of-scope items if available.
5. `3. 使用者簡介`: combine BRD chapter 1 and PRD chapter 2. Include role cards and a permission table.
6. `4. 利害關係人`: use stakeholder chapters or source notes if available; otherwise mark as `待補`.
7. `5. 核心業務需求`: map BRD chapter 3 to PRD chapter 3.
8. `6. 待確認事項與風險`: include conflicts, missing inputs, source ambiguity, risks, or open items.
9. `7. 專案成本與時程`: use source content if available; otherwise mark as `待補`.

## Requirement Mapping Rules

For `核心業務需求`, create one feature block per BRD `3.x` section.

Each feature block should contain:

- Requirement title with original numbering.
- BRD business summary: who can do what, under what business rules.
- PRD user stories: grouped under the matching PRD `3.x` heading.
- Permission/state/logging rules, if they affect delivery or acceptance.
- Source notes for appendix/demo/prototype supplements, only when real source text exists.
- `待確認` notes for conflicts or missing decisions.

Matching heuristics:

- Prefer exact numbering matches, for example BRD `3.2` to PRD `3.2`.
- If numbering differs, match by heading names, role names, user journey, or shared nouns.
- If no PRD user story exists for a BRD requirement, keep the BRD requirement and add `PRD User Story：待補`.
- If PRD contains a user story not supported by BRD chapter 3, place it under `待確認事項與風險` unless the user asks to include product-only scope.

## HTML Rules

Generate a single self-contained `.html` file:

- Use `<!doctype html>` and `<html lang="zh-Hant">`.
- Embed CSS in `<style>`.
- Do not add remote fonts, third-party scripts, build steps, analytics, or framework dependencies.
- Use semantic elements: `header`, `main`, `nav`, `section`, `table`, `details`, `summary`.
- Escape source text for HTML.
- Keep all navigation anchors valid.
- Make wide tables horizontally scrollable on small screens.
- Use `details` blocks for long requirement sections so the first view stays scannable.
- Use the active template's radius tokens. For the bundled Aiii default template, cards and blocks use `12px` to match the default Aiii UI guidance.
- Do not use decorative hero pages, marketing layouts, or visual effects that distract from meeting content.

## Writing Rules

- Write in Traditional Chinese unless the source terminology is intentionally English.
- Use concise business-facing language, not implementation-heavy prose.
- Preserve important role names, permission names, status names, audit/log fields, compliance constraints, and open items.
- Merge duplicate BRD/PRD content instead of pasting the same idea twice.
- Do not invent stakeholder names, owners, cost, schedule, legal decisions, system architecture, API behavior, or data retention rules.
- Use `待補` when information is missing and expected.
- Use `待確認` when the source is ambiguous, conflicting, or requires a business decision.
- If BRD and PRD conflict, add a short conflict note rather than silently choosing one.

## What To Ask AM

The first three BRD/PRD chapters are usually enough for a usable kickoff HTML draft. Ask AM for the following only when needed for completeness:

- Meeting date, audience, and purpose.
- Output folder and filename convention.
- Stakeholder names, teams, owners, approvers, and escalation contacts.
- Cost days, milestone dates, expected UAT date, and launch target.
- Required sections to include or exclude.
- Whether prototype/demo status, screenshots, or current implementation notes should be included.
- Any exact brand, legal, regulatory, or compliance wording.

## Validation

After creating or updating the HTML:

1. Confirm the generated file contains all expected major sections.
2. Confirm each nav link points to an existing section ID.
3. Confirm tables remain readable on mobile or are inside a scrollable wrapper.
4. Confirm no unreplaced `{{placeholder}}` tokens remain.
5. Confirm intentional missing data uses `待補` or `待確認`.
6. If a browser or screenshot tool is available and visual QA is expected, capture desktop and mobile screenshots and fix overlap, unreadable text, or broken layout.
