<div align="center">

# Autoresearch

**Can coding agents run AI verification experiments in a loop and produce findings that hold up under human review?**

[![Status: scaffold](https://img.shields.io/badge/status-scaffold-lightgrey)](#status)
[![Stack: undecided](https://img.shields.io/badge/stack-undecided-lightgrey)](#decisions)
[![Licence: Apache-2.0 + CC BY 4.0](https://img.shields.io/badge/licence-Apache--2.0%20%2B%20CC%20BY%204.0-D22128)](#repository)
[![AI Verification Observatory](https://img.shields.io/badge/org-AI%20Verification%20Observatory-0a3d62)](https://github.com/ai-verification-observatory)

</div>

Agent loops that run experiments for the organisation's projects: read what is already known, propose a change, run it under a fixed budget, keep it or discard it, and record the outcome as a finding in the [knowledge base](https://github.com/ai-verification-observatory/knowledge-base), failures included.

The pattern comes from Karpathy's [autoresearch](https://github.com/karpathy/autoresearch): an agent edits one file, runs a fixed five-minute experiment, keeps the change if one metric improves and reverts it otherwise. A human edits only `program.md`, the instructions the agent follows. Here the loop runs against verification projects instead of a training script, and its output is reviewed findings, not a better number alone.

## Status

Scaffold. There is no code, no target and no chosen stack. The [open questions](#open-questions) are answered before any loop runs.

## Contents

- [Two loops](#two-loops)
- [Open questions](#open-questions)
- [Rules](#rules)
- [Where this fits](#where-this-fits)
- [Decisions](#decisions)
- [Repository](#repository)

## Two loops

**Research loop.** Runs against one target project with one metric. Each iteration: read the track and its findings, state a hypothesis, change the target, run the experiment within the budget, compare against the baseline, keep or revert, log the run, and draft a finding when the result is worth one. [`program.md`](program.md) is the draft of what the agent follows.

**Workflow loop.** Runs against the organisation's own rules: `AGENTS.md` files, templates and workflows. It reads merged and rejected findings, review comments and failed checks, and proposes changes that would have prevented the friction. Every proposal is a pull request a human accepts or rejects.

## Open questions

Each answer becomes its own section of this README.

| # | Question | What the answer must say | Answer |
|---|---|---|---|
| 1 | First target | Which project and which file the agent may edit. It needs a metric and a baseline, so it is probably not a scaffold. | open |
| 2 | Metric | One number, how it is measured, and why improving it means the verification got better rather than the check got weaker. | open |
| 3 | Gaming | How the loop is stopped from improving the metric by weakening the claim: the negative controls or tamper tests that must still pass after every change. | open |
| 4 | Budget | Wall-clock per run, runs per session, hardware, and who pays for it. | open |
| 5 | Harness | Which agent runs the loop, where, with which permissions and which secrets kept out of reach. | open |
| 6 | Review | Who reviews what the loop produces, how fast, and what makes a run worth a finding rather than a log line. | open |

## Rules

The loop follows the organisation's rules, plus these.

1. **Humans merge.** The loop opens pull requests. It never merges its own, in any repository.
2. **The claim cannot get weaker.** Every negative control and tamper test the target has must pass after a change, or the change is reverted, whatever the metric did.
3. **Every run is logged.** Kept, reverted, crashed or timed out: one line each, with the hypothesis, the commit, the command and the metric. The log is the evidence for any finding.
4. **Findings say they came from a loop.** The finding names the agent and the human who reviewed it in `authors`.
5. **No new dependencies, secrets or network access** beyond what the target project already uses, unless a decision below allows it.

## Where this fits

| Repository | Role |
|---|---|
| [knowledge-base](https://github.com/ai-verification-observatory/knowledge-base) | What the loop reads before each run and writes findings to |
| Projects such as [poc-memory-exhaustion](https://github.com/ai-verification-observatory/poc-memory-exhaustion) or [inference-proofs](https://github.com/ai-verification-observatory/inference-proofs) | What the research loop runs against, with the maintainer's agreement |
| This repository | The loop instructions, the harness and the run logs |

## Decisions

Every choice of target, stack, hardware and budget lands here, with its reason.

| Date | Decision | Why |
|---|---|---|
| | | |

## Repository

Part of the [AI Verification Observatory](https://github.com/ai-verification-observatory). Code is licensed under [Apache-2.0](LICENSE); text and run logs under [CC BY 4.0](LICENSES/CC-BY-4.0.txt). Coding agents read [AGENTS.md](AGENTS.md) first.

Want the loop to run against your project, or have a metric that cannot be gamed? [Open an issue](https://github.com/ai-verification-observatory/autoresearch/issues).
