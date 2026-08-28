## The Prompt

I thought it would be amusing to shape this chat around a Claude prompt, so I asked it what my top 5 talking points should be.

To answer, Claude trawled through all of my activity on GitHub and all of its own memory, and came up with the exactly same points I'd already planned to discuss.

But this really is an example of how I use Claude, it's really good at summarizing information from multiple sources. I often use it to remind me which PRs I've forgotten to review for example.

# The raw material

The headline in its response is that I have made 802 PRs since I started using Claude in March. Much of that represents useful work that is currently in production at DLS. But there is also a down side that I'll get to at the end.

# 1. Claude Sandbox

The first highlight is claude-sandbox. I use this every day for all of my projects. DLS is adopting it as a mandatory tool so that we can safely give claude access to all developers.

(VSCODE) Here I have a vscode developer container with claude sandbox installed. When I launch claude its always in the sandbox.

This restricts its access to credentials, filesystems and local network devices.

The project comes with some 'slash' commands and I'm just going to run /verify-sandbox. This tells Claude to try and break out of the sandbox using 10 novel methods it can think of.

The reason we need this is that when you run claude code directly on your host machine, it has full access to your credentials, filesystem and network. It can basically do anything you can do. If you make a mistake in your prompt or a bad actor gets control via prompt injection, it could be disastrous.

Because I have claude sandbox I can happily leave claude to do long running tasks without worrying about the blast radius if things go wrong.

All of claude sandbox is written by claude. I've looked at the code but this is not my area of expertise. I trust it because I can demonstrate that claude cannot break out of the sandbox.

The /verify-sandbox results show that the 18 measures used by the sandbox are confirmed in place, and that the 10 invented escape methods all failed.


# 2, 3 Skills and Memory, builder2ibek

To get the most out of agentic coding you need a handle on how skills and memory systems work.

Claude has 3 places it saves information:
- .claude in your home directory for shared skills, config and auto-memory
- .claude in your project directory for project specific skills and config
- enterprise config for global overrides: useful for enforcing sandbox use for example.

My favourite skill set is builder2ibek. This is a python tool originally hand written that converts DLS old XML based IOCs into our new containerised IOCs.

When I'm running claude is this project it knows lots of details about our old and new controls infrastructure. So I can ask it questions like this: [asub conversion](https://claude.ai/code/artifact/a844d62a-f95f-4920-9a33-1b280ab80a78?org=730ada2f-09f9-446c-be32-eeb31fe85cd7)

(VSCODE - show skills b2i folder)
So again, I didn't write any of these skills. I merely had a conversation e.g. 'take a look in this folder and then find all the subfolders with the highest version number'. Then once we had found what we wanted, I asked claude to write a skill that would do the same thing automatically in future. Repeating this process has built up into an incredibly useful skill set that can do half of the work I used to do manually.

One thing to be clear on is that claude automatically saves memories of what you have been up to on a per project basis. However that always goes into the $HOME/.claude folder. Also it only saves memories on its own cadence. For this reason I developed the /memo command. This makes sure your memories are up to date and then extracts relevant memories into skills in the project folder.

That means useful learnings can be carried along with the project source and used by other developers.


# 4, 5
podbench is my counter example. I've been spending a lot of time on it recently and its all gone a bit wrong.

It debugs a live service running in a Kubernetes cluster, from VS Code. And it works sort of.

The trouble is I started this project as a prototype to prove out some ideas about how this could work. I gave the agent the ideas and access to my personal Kubernetes cluster. The result was 6 hours of agent activity that created a fully realized project with CI, container and helm chart publishing, documentation and a huge test suite. It worked well for some scenarios.

Next I came to iterate on the initial version, but every iteration was pulling all the scaffolding along with it. Every PR was expensive, slow and had a huge change list.

So the lesson is make sure you tell the agent you are prototyping. Get a minimal working version and then iterate on that. Add all the scaffolding later.

# Wrapping up

- Sandbox it, so you can leave it running autonomously.
- Promote what you learn into skills, so you only learn it once. Use /memo to help.
- Make sure the agent knows you are prototyping if that's what you are doing!
- Obvious but worth saying: lines of code and PR count are not measures of success.
