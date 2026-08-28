# Prompt aid — OSL AI Workshop

**Wed 2 Sep 2026 · 1150–1205 · Møller Institute, Cambridge · 15 min · item 5**
Framing: previously an AI sceptic, now using Claude exclusively. Demo, not slides.

---

## The prompt

- Shaped this chat around a Claude prompt — asked it for my top 5 talking points
- It trawled all my GitHub activity + all its own memory
- Came back with **exactly the points I'd already planned** to discuss
- That *is* the example: good at summarising across multiple sources
- Everyday use: reminding me which PRs I've forgotten to review

## The raw material

- **802 PRs since March**, when I started using Claude
- Much of it useful work, in production at DLS now
- But there's a downside — coming back to it at the end

---

## 1 · Claude Sandbox

- Use it every day, all projects. **DLS adopting it as mandatory** so we can safely give Claude to all developers
- **(VS CODE)** dev container with claude-sandbox installed — launching Claude always puts it in the sandbox
- Restricts access to: credentials · filesystems · local network devices
- Run **`/verify-sandbox`** — tells Claude to try to break out using 10 novel methods it invents itself
- **The contrast:** Claude on your host has full access to your credentials and filesystem — anything you can do. A bad prompt or a prompt injection could be disastrous
- Because of the sandbox I can **leave it on long-running tasks** without worrying about blast radius
- **All of claude-sandbox is written by Claude.** I've read the code, but it's not my area of expertise — I trust it because I can *demonstrate* Claude can't break out
- Result to point at: **18 measures confirmed in place, all invented escape methods failed**

> If the live run differs from the script: today's run was 18/18 checks and 14 probes — 13 blocked, 0 escaped, 1 inconclusive. The inconclusive one is host loopback via the shared network namespace, which the threat model documents as out of scope. Fine to say out loud — it reports what it can't defend, not just what it can.

---

## 2, 3 · Skills and Memory, builder2ibek

- To get the most out of agentic coding you need a handle on **how skills and memory work**
- Claude saves information in **three places**:
  - `.claude` in your **home** dir — shared skills, config, auto-memory
  - `.claude` in your **project** dir — project-specific skills and config
  - **enterprise config** for global overrides — e.g. enforcing sandbox use
- Favourite skill set: **builder2ibek** — Python tool, originally hand-written, converts DLS's old XML IOCs into the new containerised ones
- In that project Claude knows our old *and* new controls infrastructure, so I can ask it things like the **genSub → aSub** question
  - → https://claude.ai/code/artifact/a844d62a-f95f-4920-9a33-1b280ab80a78
- **(VS CODE — show the b2i skills folder)**
- **I didn't write any of these skills.** I had a conversation — "look in this folder, find all the subfolders with the highest version number" — then asked Claude to write a skill that does it automatically next time
- Repeating that has built a skill set that does **half the work I used to do by hand**
- One thing to be clear on: Claude saves memories per project automatically, **but always into `$HOME/.claude`**, and only on its own cadence
- So I built **`/memo`** — brings memories up to date, then extracts the relevant ones into skills **in the project folder**
- **Point:** learnings travel with the source, and other developers get them

---

## 4, 5 · podbench — the counter-example

- Been spending a lot of time on it recently and **it's all gone a bit wrong**
- What it does: debug a live service running in a Kubernetes cluster, from VS Code. And it works — *sort of*
- Started as a **prototype** to prove out some ideas. Gave the agent the ideas and access to my personal k8s cluster
- Result: **6 hours of agent activity → a fully realised project** — CI, container and Helm chart publishing, documentation, a huge test suite. Worked well for some scenarios
- Then I came to iterate. **Every iteration dragged all the scaffolding along.** Every PR expensive, slow, huge change list
- **Lesson: tell the agent you are prototyping.** Get a minimal working version, iterate on that, add the scaffolding later

---

## Wrapping up

- **Sandbox it**, so you can leave it running autonomously
- **Promote what you learn into skills**, so you only learn it once — `/memo` helps
- **Tell the agent you're prototyping**, if that's what you're doing
- Obvious but worth saying: **lines of code and PR count are not measures of success**
