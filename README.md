## Jonathan Lee

I build small tools for people working with AI coding agents, and I measure
whether they work — including when the answer is no.

M.S. Computer Science, Johns Hopkins.

---

**[blindspot](https://github.com/jlee844/blindspot)** — which lines in a change
would a test actually catch a bug in? Coverage says a line *ran*; it doesn't say
anything asserted on it. Breaks each changed line and re-runs only the tests
that cover it.

**[receipt](https://github.com/jlee844/receipt)** — what a session actually did
and what it cost. Reads the transcript instead of the agent's own summary. On
one session, 97% of input tokens were the model re-reading its own context.

**[transcript-audit](https://github.com/jlee844/transcript-audit)** — profile a
corpus of agent transcripts before computing a statistic over it. Mine turned
out to be 9 usable sessions, not 434.

---

### Start here

**[I checked 1,135 things an AI agent said it had done](https://github.com/jlee844/receipt/blob/main/FINDINGS.md)**

Fifteen weren't true; one had been wrong for four weeks. The write-up covers the
five attempts that failed first — including two where I predicted in writing
that the fix would work and was wrong — and the simpler question that worked:

> Only build a checker when the evidence it needs already exists outside
> anyone's opinion.

More work — retrieval evaluation, quantization, distillation — is in private
repos. Happy to walk through any of it.
