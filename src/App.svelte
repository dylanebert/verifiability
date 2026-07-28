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
      Generating code is easy now. The hard part is knowing whether it's the
      code you want: fast, stable, secure, to your taste.
    </p>
    <p>
      How well you can know that is a task's <em>verifiability</em>.
    </p>
  </section>

  <section class="section">
    <h2>why now</h2>
    <p>
      Trust used to ride on authorship: a person wrote the code, reviewed the
      diff, chose the tests. Agents remove that.
    </p>
    <p>
      Reinforcement learning is how they got good: attempt a task, get rewarded
      when the result is right, repeat. You can only reward what you can check,
      so reward and verifiability are the same property.
    </p>
    <p>
      Code and math led because they grade themselves
      (<a href="https://arxiv.org/abs/2501.12948" target="_blank" rel="noopener noreferrer">DeepSeek-R1</a>,
      <a href="https://arxiv.org/abs/2411.15124" target="_blank" rel="noopener noreferrer">Tülu 3</a>).
      Some gains are model-family quirks, not reasoning
      (<a href="https://arxiv.org/abs/2506.10947" target="_blank" rel="noopener noreferrer">Spurious Rewards</a>).
    </p>
  </section>

  <section class="section">
    <h2>types of verifiability</h2>
    <p>
      There are three types of verifiability. Anthropic
      <a href="https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents" target="_blank" rel="noopener noreferrer">sorts graders</a>
      the same way: code-based, model-based, human.
    </p>
    <p>
      <strong>Human.</strong> The highest ceiling, and the most expensive. A
      person can judge anything, taste included. Taste especially: it has no
      oracle but the person, so you can't sample it cheaply or in parallel.
    </p>
    <p>
      <strong>Machine.</strong> Tests, typecheckers, static analysis. Fast,
      cheap, and objective, but only as correct as the assumptions you fed them.
      When the oracle is trustworthy, automation follows. Bun's
      <a href="https://bun.com/blog/bun-in-rust" target="_blank" rel="noopener noreferrer">rewrite from Zig to Rust</a>
      leaned on a language-independent test suite as its oracle: 60,624 tests,
      "0 skipped or deleted."
    </p>
    <p>
      <strong>LLM-as-judge.</strong> An agent grades the work: the most flexible
      of the three, judging what no test can express. Also the most expensive
      and non-deterministic, and foolable: a single junk token can trigger a
      false pass
      (<a href="https://arxiv.org/abs/2507.08794" target="_blank" rel="noopener noreferrer">One Token to Fool</a>).
      Bun used it adversarially. A second Claude saw only the diff, told to
      assume the code was broken, while the implementer never reviewed its own
      work. Adding judges can raise confidence, at rising cost. A field of its
      own; I'll point rather than cover.
    </p>
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
