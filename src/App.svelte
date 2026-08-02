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
    <h2>the gap</h2>
    <p>
      Every verifier is a proxy for intent. A test suite checks what you wrote
      down. What you meant was never fully written down.
    </p>
    <p>
      Optimization pressure widens the gap. A stronger generator finds more of
      the proxy's slack, so sustained optimization against an imperfect
      objective produces reward hacking. No fixed reward function stays
      effective as capability grows
      (<a href="https://arxiv.org/abs/2606.26300" target="_blank" rel="noopener noreferrer">The Verification Horizon</a>).
    </p>
    <p>
      Verification signal
      <a href="https://arxiv.org/abs/2606.26300" target="_blank" rel="noopener noreferrer">decomposes</a>
      into scalability, faithfulness, and robustness. You get two. Unit tests
      scale and hold up under pressure, and capture little intent. LLM judges
      scale and track intent, and are gameable. Human review tracks intent and
      holds up, and does not scale.
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
      <strong>LLM-as-judge.</strong> Agents grade other agents. Adversarial
      review is one form: a fresh agent, no stake in the code, hunting for
      what's wrong. It's the newest of the three, and the fastest-changing.
    </p>
  </section>

  <section class="section">
    <h2>the landscape</h2>
    <p>
      Test suites are the default proxy, and their failure rate is measured.
      Across 21 repair tools on Defects4J,
      <a href="https://shangwenwang.github.io/files/ASE-20.pdf" target="_blank" rel="noopener noreferrer">27.5% of test-passing patches were correct</a>.
      When independently generated suites labeled patches that 35 professional
      developers had already judged,
      <a href="https://xin-xia.github.io/publication/icse192.pdf" target="_blank" rel="noopener noreferrer">agreement was near chance</a>.
      Passing is evidence at a known and unimpressive rate.
    </p>
    <p>
      Review is the second layer. Human review
      <a href="https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/rigby2013convergent.pdf" target="_blank" rel="noopener noreferrer">saturates at two reviewers</a>,
      and
      <a href="https://sback.it/publications/icse2018seip.pdf" target="_blank" rel="noopener noreferrer">Google's median is one</a>.
      For agent reviewers the published data
      <a href="https://claude.com/blog/code-review" target="_blank" rel="noopener noreferrer">scales yield by the size of the diff</a>,
      not by the number of reviewers.
    </p>
    <p>
      The practice tradition is the third layer. SOLID, data-oriented design,
      and test-driven development are bodies of technique for making code
      checkable before it is written, each with its own applicability
      conditions. Where the effect has been measured it is small. TDD's effect
      on external quality
      <a href="https://ieeexplore.ieee.org/document/6427618" target="_blank" rel="noopener noreferrer">standardizes to about zero</a>
      across 12 experiments and 743 subjects.
    </p>
    <p>
      Agents changed what can be measured about that tradition. A practice can
      be assigned, enforced, and logged across thousands of runs, so methodology
      becomes an experimental variable at a scale human subjects never allowed.
      A cluster of 2026 papers crosses
      <a href="https://arxiv.org/abs/2605.27922" target="_blank" rel="noopener noreferrer">harness</a>
      and
      <a href="https://arxiv.org/html/2607.10569" target="_blank" rel="noopener noreferrer">tool surface</a>
      against model family, and the recurring result is that a practice moves
      cost and token count while correctness stays statistically unchanged.
    </p>
    <p>
      That research reports pass rate on benchmark tasks at unmatched cost.
      Practitioners choose between workflows under a budget. Those are different
      questions.
    </p>
    <p>
      The bill is human samples times cost per sample, and proxy quality sets
      the rate. A conformance suite is a near-perfect proxy, so a person
      samples once and the rest amortizes. Tests plus a written spec are a
      decent proxy, so sampling at pull-request boundaries holds. Where no proxy
      exists, every iteration is sampled.
    </p>
    <p>
      Two levers follow. Improve the proxy to cut the number of samples. Shorten
      the loop to cut the cost of each one.
    </p>
    <p>
      Taste has no proxy but the person who holds it, so the sample rate cannot
      fall. Practice has codified coupling, cohesion, and test design. It has
      not codified taste.
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
