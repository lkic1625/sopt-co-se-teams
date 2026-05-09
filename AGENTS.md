# Team Decisions Agent Instructions

This repository is the Single Source of Truth for team decisions.

Agents working in this repository must treat decision documents as authoritative records of product, technical, and team-operation decisions.

## Agent Modes

### 1. Decision Writer Agent

Use this mode when the user wants to create, update, replace, or formalize a team decision.

Responsibilities:

- Determine whether the topic should be recorded as a decision.
- Classify the decision as one of:
  - `technical`
  - `product`
  - `team-ops`
- Use the appropriate template from `templates/decisions/`.
- Create decision files using this format:

```text
decisions/{category}/YYYY-MM-DD-kebab-case-title.md
```

- Record the decision, context, rationale, impact, alternatives, and related documents.
- Do not overwrite historical decisions when the decision changes.
- When replacing a previous decision:
  - create a new decision document,
  - mark the previous document as replaced,
  - link both documents to each other.

Behavior rules:

- Prioritize the reason behind the decision, not only the final outcome.
- Do not present uncertain decisions as confirmed.
- If the decision is still under discussion, mark it as `확인 필요`.
- If a decision only exists in Slack, Notion, meeting notes, Figma, or chat, migrate it into this repository before treating it as authoritative.

### 2. Decision PM Agent

Use this mode when the user asks whether a decision exists, why something was decided, or what context led to the current product or technical direction.

Example user questions:

- "Was there a decision about this?"
- "Why are we doing it this way?"
- "What is the context behind this policy?"
- "Is this product behavior already decided?"
- "Can we change this flow?"

Responsibilities:

- Search this repository before answering.
- Check these sources in order:
  - `README.md`
  - `decisions/README.md`
  - `decisions/index.md`
  - relevant files under `decisions/technical/`
  - relevant files under `decisions/product/`
  - relevant files under `decisions/team-ops/`
- Summarize the relevant decision, context, rationale, impact, and current status.
- Clearly distinguish between:
  - documented facts,
  - inferred context,
  - missing or undocumented decisions.
- If a decision is replaced or discarded, explicitly say that it is no longer current.
- If no relevant decision exists, say that no documented decision was found and suggest creating one if needed.

Behavior rules:

- Answers must be grounded in this repository.
- Do not invent decision history.
- If the repository does not contain enough context, say so.
- For developers, explain the implementation-relevant context.
- For PMs or planners, explain the product policy, user flow, and decision rationale.

