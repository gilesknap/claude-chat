---
name: giles-voice
description: Write prose in Giles Knap's voice - plain, first-person, short paragraphs, concrete numbers, dry understatement, honest about limits. Use when drafting or rewriting any prose that Giles will put his name to - talk scripts, demo notes, README and docs prose, slide text, issue and PR descriptions, blog posts, conference abstracts - or when asked to "write this in my voice" / "make this sound like me".
---

# Giles' voice

Derived from `transcript.md` (a talk script) in this repo. That is a small sample, so treat
these as strong defaults rather than laws, and prefer any longer sample the user gives you.

## The shape

**One idea per paragraph, and the paragraph is one or two sentences.** Blank line between
every one. No walls of text, no bullet lists where sentences will do.

**Claim, then the concrete thing, then the so-what.** "I use claude-sandbox every day for
all of my projects. DLS is adopting it as a mandatory tool so that we can safely give
claude access to all developers."

**Ruthlessly short.** He says a thing once and moves on. Never restate a point in fresh
words, never add the sentence that explains the sentence before it. If a paragraph could be
deleted without losing a fact, delete it. For spoken material, budget roughly 100 words per
minute of stage time and count them: a 15 minute demo is under 900 words, because the demo
is doing most of the talking.

**Number everything you can count.** 802 PRs, 18 measures, 10 escape methods, 3 places
Claude saves information. Numbers do the persuading; adjectives do not.

## The register

- First person and present tense. "I use", "I often use it to", "I'm just going to run".
- Contractions throughout: it's, I'd, I've, don't.
- Start sentences with But, So, and And when the thought turns. "But there is also a down
  side that I'll get to at the end."
- Address the reader directly when there is a risk to explain: "When you run claude code
  directly on your host machine, it has full access to your credentials and filesystem."
- One vivid, borrowed-from-engineering metaphor per piece, no more: "blast radius".
- British spelling by default: favourite, containerised, artefact. He is inconsistent
  about -ise/-ize, so don't correct him either way.
- Quote your own prompts in single quotes, verbatim and unpolished: 'take a look in this
  folder and then find all the subfolders with the highest version number'.

## The stance

**Understate the good news.** "This is an example of how I use Claude, it's really good at
summarizing information from multiple sources." Never "revolutionary", "game-changing",
"incredibly powerful".

**Say what you don't know.** "I've looked at the code but this is not my area of expertise."
Credibility comes from the admission, so don't cut it.

**Trust is earned by demonstration, not assertion.** "I trust it because I can demonstrate
that claude cannot break out of the sandbox."

**Flag the counter-example.** Every piece that praises something also names where it went
wrong: "podbench is my counter example... it's all gone a bit wrong." Signpost it early,
deliver it at the end.

**Dry, deadpan humour, never a joke that announces itself.** "I thought it would be amusing
to shape this chat around a Claude prompt, so I asked it what my top 5 talking points
should be."

## Don't

- No marketing voice: leverage, unlock, seamless, empower, robust, cutting-edge.
- No em dashes for drama, no rhetorical questions, no "Let's dive in".
- No three-part lists of adjectives. No sentence that could open a press release.
- Don't tidy away hedges into confidence he didn't express.
- Don't inflate a demo into a claim. The demo is the claim.

## Before and after

Flat: "Claude Sandbox provides a robust, enterprise-grade security boundary that empowers
developers to leverage agentic coding with confidence."

In voice: "I use claude-sandbox every day. It restricts Claude's access to my credentials,
my filesystem and the local network."

"Because I have claude sandbox I can happily leave claude to do long running tasks without
worrying about the blast radius if things go wrong."

## Check before you hand it over

- Word count is inside the budget. Cut before you polish.
- Longest paragraph is three sentences or fewer.
- At least one real number and one real example.
- At least one honest limitation.
- Read it aloud. If it sounds like it's selling, rewrite it.
