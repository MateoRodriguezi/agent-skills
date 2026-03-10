# Agent Skills

A collection of reusable AI skills designed to improve decision-making, analysis, and documentation workflows for Product Managers, analysts, and operators.

These skills extend AI agents (Claude Code, Cursor, Codex, Gemini CLI, etc.) with structured frameworks and domain-specific guidance.

---

# Available Skills

## prd-enforcer

A strict PRD auditing framework that ensures product documents are **measurable, decision-ready, and operational**.

The skill reviews a PRD and validates that it includes:

- Quantified problem context  
- Measurable objectives (baseline + target)  
- Clear scope (in / out of scope)  
- Success metrics  
- Risks and mitigations  
- Rollout plan  
- Post-launch monitoring  

If key information is missing, the skill flags the gaps and generates concrete questions to complete the PRD.

It can also generate a **rewritten PRD draft** using a structured execution-ready template.

---

## formula-advisor

A spreadsheet formula expert that recommends the best **Excel or Google Sheets formula** to solve a user’s problem.

It is designed for both simple and advanced use cases such as:

- revenue calculations
- KPI and metric analysis
- conditional aggregations
- lookups across sheets
- data cleaning and text manipulation
- date logic and time windows
- complex nested formulas
- dynamic array formulas

The skill:

- proposes the most appropriate formula
- explains how it works
- prefers simple and maintainable solutions
- can generate complex formulas when needed
- avoids invented or unsupported functions

This makes it useful for analysts, operators, and PMs working with data in spreadsheets.

---

# Installation

Install a specific skill:

```bash
npx skills add github.com/<your-username>/agent-skills --skill prd-enforcer
npx skills add github.com/<your-username>/agent-skills --skill formula-advisor