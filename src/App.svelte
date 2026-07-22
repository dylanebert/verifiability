<article class="page">
  <header class="head">
    <div class="meta">
      <a class="byline" href="https://dylanebert.com">dylan ebert</a>
      <span class="sep">·</span> july 2026
    </div>
    <h1 class="title">verifiability</h1>
    <p class="dek">what an agent can be trusted to build.</p>
  </header>

  <section class="section">
    <h2>the crux</h2>
    <p>
      Generating code is easy now. The hard part is knowing it's the code you
      want: fast, stable, secure, to your taste.
    </p>
    <p>
      Call that verifiability. It decides what an agent can be trusted to build,
      and what you still have to do yourself.
    </p>
  </section>

  <section class="section">
    <h2>the old signal</h2>
    <p>
      We had a proxy for verifiability, and never had to name it: a person wrote
      this. Someone competent designed it, reviewed the diff, chose the tests.
      The craft was the evidence.
    </p>
    <p>
      Agents break the proxy. The code still looks right. But no one chose those
      tests, or held the context that made "a person wrote it" worth anything.
    </p>
    <p>So what's the signal now? Nobody knows. That's the open question.</p>
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

  .dek {
    margin-top: 8px;
    font-style: italic;
    font-size: 19px;
    color: var(--text-muted);
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

    .dek {
      font-size: 17px;
    }
  }
</style>
