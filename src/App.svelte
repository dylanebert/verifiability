<article class="page">
  <header class="head">
    <div class="meta">
      <a class="byline" href="https://dylanebert.com">dylan ebert</a>
      <span class="sep">·</span> july 2026
    </div>
    <h1 class="title">verifiability</h1>
  </header>

  <section class="section">
    <h2>the crux</h2>
    <p>
      Generating code is easy now. The hard part is knowing it's the code you
      want: fast, stable, secure, to your taste.
    </p>
    <p>
      How well you can check that is a task's verifiability. It bounds what an
      agent can be trusted to build, and what you still have to do yourself.
    </p>
  </section>

  <section class="section">
    <h2>the old signal</h2>
    <p>
      The old check was implicit: a competent person wrote the code, reviewed
      the diff, chose the tests. Trust rode on authorship.
    </p>
    <p>
      Agents break that. The code still looks right, but no one chose the tests,
      and no one held the context that made authorship a signal.
    </p>
    <p>So what's the signal now? Nobody knows.</p>
  </section>

  <section class="section">
    <h2>why now</h2>
    <p>
      Models got good at code through reinforcement learning: attempt a task,
      get rewarded when the result is right, repeat.
    </p>
    <p>
      You can only reward what you can check. A task that produces that signal is
      a verifiable task. Reward and verifiability are the same property.
    </p>
    <p>
      Code and math led because they grade themselves
      (<a href="https://arxiv.org/abs/2501.12948" target="_blank" rel="noopener noreferrer">DeepSeek-R1</a>,
      <a href="https://arxiv.org/abs/2411.15124" target="_blank" rel="noopener noreferrer">Tülu 3</a>).
      Some gains are model-family quirks, not reasoning
      (<a href="https://arxiv.org/abs/2506.10947" target="_blank" rel="noopener noreferrer">Spurious Rewards</a>).
    </p>
    <p>
      Same property, both ends: what a model can be trained to do, and what you
      can trust it to do.
    </p>
  </section>

  <section class="section">
    <h2>the forms</h2>
    <p>
      So the question is how you verify. Three forms; Anthropic
      <a href="https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents" target="_blank" rel="noopener noreferrer">sorts graders</a>
      the same way: code-based, model-based, human.
    </p>
    <p>
      <strong>Human.</strong> The highest ceiling, and the most expensive. A
      person can judge anything, taste included. Taste especially: it has no
      oracle but the person, so you can't sample it cheaply or in parallel.
    </p>
    <p>
      <strong>Machine.</strong> Tests, types, proofs. Fast and near-perfect, but
      only as correct as the assumptions you fed it. When the machine oracle is
      trustworthy, automation follows. Bun's
      <a href="https://bun.com/blog/bun-in-rust" target="_blank" rel="noopener noreferrer">rewrite from Zig to Rust</a>
      rode a language-independent test suite: 60,624 tests, "0 skipped or
      deleted." One author, reviewers who saw only the diff and were told to
      assume it was broken, and a hand check that the tests actually ran.
    </p>
    <p>
      <strong>LLM-as-judge.</strong> An agent grades the work. Cheap, general,
      the fastest-moving of the three. Also foolable: a single junk token can
      trigger a false pass
      (<a href="https://arxiv.org/abs/2507.08794" target="_blank" rel="noopener noreferrer">One Token to Fool</a>).
      And more judges isn't automatically a better verdict. Anthropic found
      <a href="https://www.anthropic.com/engineering/multi-agent-research-system" target="_blank" rel="noopener noreferrer">one rubric-based judge beat a panel</a>.
      A field of its own; I'll point rather than cover.
    </p>
  </section>

  <section class="section">
    <h2>any others?</h2>
    <p>
      Formal proofs are the high end of the machine rung, not a separate form.
      The one genuinely different thing isn't a verdict at all: whether it works
      in production, at scale, over time, at what cost.
    </p>
    <p>That's not verifying. That's sensing.</p>
  </section>
</article>

<style>
  .page {
    max-width: var(--measure);
    margin: 0 auto;
    padding: 96px 24px 120px;
  }

  .meta {
    font-family: var(--display);
    font-size: 14px;
    color: var(--text-muted);
    margin-bottom: 14px;
  }

  .byline {
    color: var(--text-muted);
    text-decoration: none;
  }

  .byline:hover {
    color: var(--ink);
  }

  .sep {
    opacity: 0.5;
  }

  .title {
    font-family: var(--display);
    font-size: 34px;
    font-weight: 600;
    letter-spacing: -0.02em;
    color: var(--ink);
  }

  .section {
    margin-top: 40px;
  }

  .section h2 {
    font-family: var(--display);
    font-size: 15px;
    font-weight: 600;
    text-transform: lowercase;
    color: var(--text-muted);
    margin-bottom: 10px;
  }

  .section p {
    margin-top: 14px;
    color: var(--text-dim);
  }

  @media (max-width: 560px) {
    .page {
      padding: 56px 20px 80px;
    }

    .title {
      font-size: 28px;
    }
  }
</style>
