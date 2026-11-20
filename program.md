# program.md

**Status: draft.** The instructions the research loop follows. Humans edit this file; the agent does not. The placeholders in angle brackets are filled once the README's open questions are answered.

## Setup, once per session

1. Read the knowledge base: `index.md`, `tracks/<track>.md` and every finding that names the track. Note what has already been tried, especially what failed.
2. Clone the target `<repo>` at `<commit>`. You may edit only `<file>`. Everything else is read-only.
3. Run the baseline: `<command>`. Record the metric `<metric>` and confirm every check in `<checks>` passes. If the baseline fails, stop and report.
4. Start the run log `runs/<date>-<target>.tsv` with the header:
   `run	commit	hypothesis	metric	checks	outcome	note`

## Loop

Repeat until `<max runs>` runs or `<max hours>` hours:

1. **Hypothesis.** One sentence: what you change and why you expect the metric to move. Do not repeat a hypothesis a finding already ruled out unless you say what is different.
2. **Change.** Edit `<file>`. Commit with the hypothesis as the message.
3. **Run.** `<command>`, killed after `<budget>` of wall-clock.
4. **Judge.** Keep the commit only if the metric improves on the best kept run **and** every check passes. Otherwise `git reset --hard` to the best kept commit.
5. **Log.** One line in the run log, whatever happened: kept, reverted, crashed or timed out.

## After the loop

1. Push the run log and the kept commits to a branch in this repository.
2. For each result worth sharing, including a hypothesis that clearly failed, draft a finding from the knowledge base's `templates/finding.md` with `strength: measured` unless the run supports more, and open a pull request there.
3. Write a summary: runs, kept changes, best metric against baseline, and what you would try next.

Never merge. Never weaken a check. Never edit outside `<file>`.
