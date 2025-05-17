## The Philosophy of the Command Line

> “*Simple should be simple.
> Complex should be possible.*” —Alan Kay

### Software Products are Complex

AI is radically changing the way we build and use software.
On top of that, it's changing *who* is building software, since more people are able to
build more things AI-powered developer tools.

In technology, some things change fast—and some don't change at all.
The hard part is in knowing which parts are which.

Technology is the solution to *human* problems.
Human problems tend to be complex.

Engineering is the process of exploring solutions to these problems with precision, in a
practical way.

In software, because both problems and software solutions to them tend to be complex,
good software engineering is the art of exploring and building solutions to customer
problems in a way that doesn't get bogged down in irrelevant details.

So good engineering means exploring the *intrinsic* complexity of a problem and possible
solutions without adding too much *accidental* complexity.

This is true whether you're a human developer or an LLM.

So one thing that *doesn't* change with progress in AI is the intrinsic complexity of
applications and tools.

### Apps Never Solve All Your Problems

There's another thing that doesn't change with AI.

Today, if you want to solve a problem you have, you have three options:

1. Use powerful, general-purpose new AI tools (ChatGPT, Claude, Perplexity, etc.)

2. Use specific tools that are built for the problem you want to solve (Notion, Figma,
   Descript, etc.)

3. Build or assemble a new app or workflow by writing new software yourself (with
   AI-powered tools like Cursor, Windsurf, Bolt, etc.)

Before we talk more about Option 3, let's talk bout the limitations of Options 1 and 2.

We all know numerous situations where our problems aren't easily solved by ChatGPT or
Notion, Google Docs, Slack, Excel, and Zapier.

There many reasons for this.
For small companies, some of them are:

- They believe it is relatively less profitable than working on other products and
  features

- They don't have the resources

- They don't understand your problem

For large and successful companies, one of the key reasons is
[Conway's Law](https://en.wikipedia.org/wiki/Conway%27s_law): their organizational
structure prevents it.
It's a key reason many large, successful companies don't add specific features you want,
even if they are obviously a good idea.

None of these reasons fundamentally go away with AI tools.
So while AI tools are changing software and even radically changing the jobs of people
building software, we will still always want things faster than developers, product
managers, designers, and entrepreneurs design and ship solutions.

What does this mean?
Well, it is *users* who understand their problems best.
The problem is, they usually can't build their own tools.

That's why Option 3 is important and will remain important.

So what does all this have to do with the command line?

### Why Do We Need an AI-Native Command Line?

> “*Civilization advances by extending the number of important operations which we can
> perform without thinking about them.*” —Alfred North Whitehead

The classic Unix-style command line has been the Swiss Army knife for savvy developers
for decades. (The bash shell, still used widely, was released 35 years ago!)

Like many developers, I love the terminal (I even wrote a popular
[guide on it](https://github.com/jlevy/the-art-of-command-line), with millions of
readers).

A fraction of developers do a lot in a terminal because it is the most efficient way to
solve many problems.
But among most normal people, the command line has pretty bad reputation.
This is a fair criticism.
Command-line shells generally still suffer from three big issues:

- Old and arcane commands, full of obscure behaviors that relatively few people remember

- A text-based interface many find confusing or ugly

- No easy, “native” support for modern tools, apps, and APIs (especially LLMs—and using
  `curl` to call OpenAI APIs doesn't count!)

Even worse, command lines haven't gotten much better.
Few companies make money shipping new command-line tooling.
(In the last few years this has slowly starting to change with tools like nushell, fish,
and Warp.)

Nonetheless, for all its faults, there is a uniquely powerful thing about the command
line: With a command line, you can do complex things that were never planned by an app
developer, a designer, or an entrepreneur building a product.

*You* know your problems better than anyone else.
Any tool that lets you solve complex problems yourself, without waiting for engineers
and designers, can radically improve your productivity.

I think it's a good time to revisit this idea.

In a post-LLM world, it should be possible to do more things without so much time and
effort spent (even with the help of LLMs) on coding and UI/UX design.

If we have an idea for a script or a feature or a workflow, we should not have to spend
weeks or months to iterate on web or mobile app design and full-stack engineering just
to see how well it works.

### The Goals of New Shell-Style Interfaces

This brings us to the goals behind building a new, AI-native shell:

- **Make simple tasks simple:** Doing a simple thing (like transcribing a video or
  proofreading a document) should be as easy as running a single command (not clicking
  through a dozen menus).
  We should be able to tell someone how to do something simply by telling them the
  command, instead of sharing a complex prompt or a tutorial video on how to use several
  apps.

- **Make complex tasks possible:** Highly complex tasks and workflows should be easy to
  assemble (and rerun if they need to be automated) by adding new primitive actions and
  combining primitive actions into more complex workflows.
  You shouldn't need to be a programmer to use any task—but any task should be
  extensible with arbitrary code (written by you and an LLM) when needed.

- **Augment human skills and judgement:** Many AI agent efforts aim for pure automation.
  But even with powerful LLMs and tools, full automation is rare.
  Invariably, the best results come from human review wherever it's needed—experimenting
  with different models and prompts, looking at what works, focusing expert human
  attention in the right places.
  The most flexible tools augment, not replace, your ability to review and manipulate
  information. It should help both very technical users, like developers, as well as less
  technical but sophisticated users who aren't traditional programmers.

- **Accelerate discovery of the workflows that work best:** We have so many powerful
  APIs, models, libraries, and tools now—but the real bottleneck is in discovering and
  then orchestrating the right workflows with the right inputs, models, prompts, and
  human assistance. Anyone should be able to discover new steps and workflows without
  waiting on engineers or designers.

- **Understand and build on itself:** A truly AI-native programming environment should
  improve itself! A shell should read its own code and docs, assist you with its own
  commands, and help you write new actions.
  Better languages and scripting tools can in fact make LLMs smarter, because it allows
  them to solve problems in ways that are simpler and less error prone.

A shell and better command line is like a first step toward an item-based information
operating system—an alternate, more flexible UX and information architecture for
knowledge workflows.
It is the tool you need when you don't know what tool you need.

### Design Principles

What are the key design choices in building shell-style tools and interfaces?

I've been thinking about this a while and have come up with these:

1. **Flexibility and power arise from simple tools that can be recombined in complex
   ways** (like the old Unix model)

2. **Data formats should be simple, local, and transparent** (text files, Markdown,
   YAML, filenames with intuitive names, not opaque formats, sprawling JSON, or only
   stored in the cloud)

3. **Play well with other tools and APIs** (including local and cloud-based LLMs; edit
   content with external tools whenever necessary; use any APIs or libraries)

4. **Keep content human reviewable and editable at any stage** (never just assume
   automation will work; use formats that make diffs as easy and clear as possible)

5. **Make prompts, context, models, and changes transparent** (use formats that make LLM
   context and edits, diffs, and history as clear as possible, let the user pick the
   models they want at any time)

6. **Make interactive exploration easy but support automation and scripting when
   desired** (prefer chat or command-line interactions over a formal codebase at first,
   but also support scripts and use as a Python library, and tools to smooth the
   transition)

7. **Maintain context in workspaces** (keep files organized by project or effort in a
   folder that can be persisted, won't get lost, and includes content, metadata,
   actions, settings, selections, caches, history, etc.)

8. **Maintain metadata on files** (so you always know where each piece of content comes
   from (and keep this close to the content, as YAML frontmatter)

9. **Make operations idempotent** (resuming a task or workflow or restarting after a
   failure should be as simple as running again)

10. **Cache slow or costly operations** (track dependencies and content hashes and know
    when things need to rerun, like a makefile)

11. **Docs, code, and examples should be self-explanatory to both LLMs and humans** (so
    it is easy to add new capabilities—an AI-native coding environment should enhance
    itself!)

12. **User interfaces should be data-driven and gradually improve** (visuals and
    workflows should not be designed up front, but emerge naturally as data is
    manipulated and use cases become clearer)

## Feedback?

This little manifesto is something I wrote in late 2024. I plan to revise it with more
ideas as I'm building some tools related to this.
If you'd like to give feedback or have thoughts, I'd love to hear from you.
I'm easiest to reach [on X/Twitter](https://x.com/ojoshe).

## License

© 2024-2025 by Joshua Levy

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International
License](http://creativecommons.org/licenses/by-sa/4.0/).

[![Creative Commons License](https://i.creativecommons.org/l/by-sa/4.0/88x31.png)](http://creativecommons.org/licenses/by-sa/4.0/)
