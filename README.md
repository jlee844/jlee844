## Jonathan Lee

I build small tools and measure whether they work. Most of what I publish is
the measurement — including the parts that came back negative, which is usually
where the useful finding is.

M.S. Computer Science, Johns Hopkins. Currently working on AI engineering:
retrieval, evaluation, and tooling for coding agents.

---

### Tools for people working with coding agents

**[blindspot](https://github.com/jlee844/blindspot)** — *which lines in this
change would a test actually catch a bug in?*
Coverage tells you a line **ran**. It doesn't tell you anything asserted on it.
blindspot breaks each changed line on purpose and re-runs only the tests that
cover it — a line counts as verified when a test actually fails. Mutation
testing scoped to the diff, so it finishes in about a second on a real PR.

**[receipt](https://github.com/jlee844/receipt)** — *what did that agent session
actually do, and what did it cost?*
Reads the session transcript instead of trusting the agent's own summary: files
changed, real test runs, failed calls, and completion claims checked against the
filesystem. Also shows where the context went — on one session, **97% of input
tokens were the model re-reading its own context**.

**[transcript-audit](https://github.com/jlee844/transcript-audit)** — *profile a
corpus of agent transcripts before you compute a statistic over it.*
Agent log directories look like clean data. Mine turned out to be **9 usable
sessions, not 434** — the rest were empty, too short, or an automated bot whose
presence moved a headline number from 0.57 to 1.00. Contamination doesn't show
up in a count; it moves your statistic.

---

### Start here

**[I checked 1,135 things an AI agent said it had done](https://github.com/jlee844/receipt/blob/main/FINDINGS.md)**

Fifteen weren't true, and one had been quietly wrong for four weeks. The
write-up covers the five earlier attempts that failed first — including two
where I predicted in writing that the fix would work and was wrong — and the
much simpler question that worked instead.

The short version of what I learned:

> Only build a checker when the evidence it needs already exists outside
> anyone's opinion.

*"Is this the right work?"* needs a judgment call, and every attempt built on
that premise failed. *"Does this file contain what you said you put in it?"*
doesn't, and it worked on the first try.

---

### How I work

- **Write the acceptance test before the thing it tests.** My first one was
  passed by every configuration I swept — a gate nothing can fail is not a gate.
- **Predict in writing, then spend.** It's the only thing that stops you
  redefining success after seeing the result.
- **A negative result with a diagnosis beats a positive one without.**
- **Check the cheap thing first.** One filesystem read outperformed sixty model
  calls and a benchmark, and it was available on day one.

More work — retrieval evaluation, quantization, distillation, chart
understanding — is in private repos for now. Happy to walk through any of it.
