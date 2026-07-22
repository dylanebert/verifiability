<article class="page">
  <header class="head">
    <h1 class="title">Verifiability</h1>
    <p class="deck">Creating software got cheap. Knowing it works didn't.</p>
  </header>

  <section class="section">
    <p>
      Writing code used to be the hard part. You had an idea, and the work was
      turning it into something that ran. That's no longer where the time goes.
      An agent can produce a working version of most things you can describe,
      about as fast as you can describe them.
    </p>
    <p>
      So the bottleneck moved. The question isn't "can I build it" anymore. It's
      whether it'll work the way I want: fast enough, stable under load, secure,
      and to my taste. That property has a name. Verifiability is how well you
      can confirm that a piece of software does what you meant it to.
    </p>
    <p>
      Verifiability now decides what an agent can own. A task you can check is a
      task an agent can be trusted with. A task you can't check is one you still
      have to do yourself.
    </p>
  </section>

  <section class="section">
    <h2>The old signal is dead</h2>
    <p>
      For a long time we had a good proxy for verifiability, and we never had to
      name it. The signal was simple: a person wrote this. A competent engineer
      designed it, reviewed the diff, picked the tests, and put their name on it.
      The craft and the process were the evidence. If someone you trusted wrote
      it and said it worked, it usually did.
    </p>
    <p>
      Agents break that proxy. The code still reads like a person wrote it,
      because a model trained on people's code did. But nobody chose those tests,
      weighed the tradeoffs, or carried the context that made the old signal
      worth anything. The shape of the evidence is intact. What it stood for is
      gone.
    </p>
    <p>
      So what's the best signal now? Nobody has a good answer yet. That's not a
      setup for a pitch. It's a genuine open question, and it's what this piece
      is about.
    </p>
  </section>

  <section class="section">
    <h2>Why now: reinforcement learning</h2>
    <p>
      It helps to know why this happened now. Models got good at code because of
      how they're trained. You hand the model a task, let it try, and reward it
      when the result is right. Repeat that across enough tasks and the model
      improves at anything you can reward.
    </p>
    <p>
      The catch is in that last word. You can only reward what you can check.
      Training needs a signal that scores an attempt as right or wrong,
      automatically and cheaply, over and over. A task that can produce that
      signal is exactly what we've been calling a verifiable task.
    </p>
    <p>
      Reward and verifiability turn out to be one property seen from two sides.
      The work models are best at is the work that was verifiable enough to train
      on in the first place. Code and math led because they grade themselves: a
      test suite passes or it doesn't, a proof resolves or it doesn't. This is
      the recipe behind the recent reasoning models
      (<a href="https://arxiv.org/abs/2501.12948" target="_blank" rel="noopener noreferrer">DeepSeek-R1</a>,
      <a href="https://arxiv.org/abs/2411.15124" target="_blank" rel="noopener noreferrer">Tülu 3</a>),
      and it comes with a caveat worth keeping: some measured gains are quirks of
      a particular model family rather than real reasoning
      (<a href="https://arxiv.org/abs/2506.10947" target="_blank" rel="noopener noreferrer">Spurious Rewards</a>).
    </p>
    <p>
      This is why verifiability isn't a footnote. The same property that decides
      what a model can be trained to do decides what you can trust it to do
      afterward.
    </p>
  </section>
</article>

<style>
  .page {
    max-width: var(--measure);
    margin: 0 auto;
    padding: 112px 24px 120px;
  }

  .title {
    font-family: var(--display);
    font-size: 34px;
    font-weight: 600;
    letter-spacing: -0.02em;
    color: var(--ink);
  }

  .deck {
    margin-top: 10px;
    font-style: italic;
    font-size: 20px;
    color: var(--text-muted);
  }

  .section {
    margin-top: 44px;
  }

  .section h2 {
    font-family: var(--display);
    font-size: 20px;
    font-weight: 600;
    letter-spacing: -0.01em;
    color: var(--ink);
    margin-bottom: 4px;
  }

  .section p {
    margin-top: 16px;
    color: var(--text-dim);
  }

  @media (max-width: 560px) {
    .page {
      padding: 64px 20px 80px;
    }

    .title {
      font-size: 28px;
    }

    .deck {
      font-size: 18px;
    }
  }
</style>
