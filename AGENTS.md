# AGENTS.md

Instructions for coding agents and humans working in this repository. `CLAUDE.md` imports this file, so every agent reads the same rules.

## Project

Agent loops that run AI verification experiments and record findings. `README.md` holds the two loops, the open questions and the rules. `program.md` is what the research loop follows. Where an open question is still blank, ask a maintainer before building on an assumption.

## No stack yet

Agent harness, language, hardware and first target are not chosen. Do not pick them yourself. Once decided, record the decision and its reason in `README.md` § Decisions, then fill in § Commands below.

## Rules

1. **Humans edit `program.md`.** An agent running the loop never edits it. An agent may propose changes to it by pull request, outside a loop.
2. **Never merge your own pull request**, here or in any other repository.
3. **Never weaken a check to improve a metric.** Negative controls and tamper tests in the target must pass after every kept change.
4. **Log every run**, including crashes and timeouts, with hypothesis, commit, command and metric. Never delete a run from a log.
5. **Never fabricate or round away results.** Report ranges and sample sizes, never a single best run, when a finding claims more than one run.
6. **No secrets, hosts or personal data** in code, logs, results or commit messages.
7. **Large artifacts stay out of git.** Referenced by hash with the command that regenerates them.
8. **Precise language.** Say bound, attested, sampled, timed or measured, and state the assumption.

## Knowledge base

Shared findings live in https://github.com/ai-verification-observatory/knowledge-base.

- Before starting a task, read `index.md`, the track of the target project and the findings that name it. Do not repeat an approach a finding already ruled out without saying what is different.
- When a run produces a result, positive or negative, draft a finding from `templates/finding.md` and open a pull request to the knowledge base, following its `AGENTS.md`. Link the commit and run log that produced it.

## Commands

None yet.

## Layout

| Path | What |
|---|---|
| `README.md` | the idea, open questions, rules, decisions |
| `program.md` | instructions for the research loop, edited by humans |
| `AGENTS.md` | this file |
| `CLAUDE.md` | imports this file |

Add a row for each top-level folder you create, such as `runs/` once the first loop runs.

## Writing style

Plain, dense, active voice, short sentences. Numbers carry units and conditions.
