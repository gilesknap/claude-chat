# Prompt aid — 2 Sep, 1150–1205

## The prompt
- Asked Claude for my top 5 — it matched my own list
- Trawled GitHub + its own memory
- Good at summarising across sources (e.g. PRs I've not reviewed)

## The raw material
- 802 PRs since March, mostly in production
- Downside comes at the end

## 1 · Claude Sandbox
- Every day, every project. DLS making it mandatory
- **(VS CODE)** dev container → Claude always sandboxed
- Blocks: credentials, filesystem, local network
- Run **`/verify-sandbox`** — Claude invents escapes, all fail
- Unsandboxed = full access; bad prompt or injection is disastrous
- So I can leave it running unattended
- Written by Claude; I trust it because I can demo it

## 2, 3 · Skills and Memory, builder2ibek
- Three stores: home `.claude` · project `.claude` · enterprise config
- builder2ibek = old XML IOCs → containerised IOCs
- Ask it the genSub → aSub question
- **(VS CODE — skills b2i folder)**
- I wrote none of them: have the conversation, then ask for a skill
- Now does half my old manual work
- Auto-memory only lands in `$HOME`, on its own cadence
- **`/memo`** → pulls it into project skills, travels with the source

## 4, 5 · podbench — counter-example
- Debugs a live k8s service from VS Code. Works, sort of
- Meant to be a prototype → 6 hours → fully realised project
- Every iteration dragged the scaffolding: slow, expensive, huge PRs
- **Say you're prototyping.** Minimal version, iterate, scaffold later

## Wrapping up
- Sandbox it, so you can leave it running autonomously
- Promote learnings into skills — `/memo`
- Tell the agent when you're prototyping
- PR count is not a measure of success
