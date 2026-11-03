# Code Reading 3: Memory in Codex

This is my Code Reading 3 assignment for CSE 598 Agentic AI at ASU (Fall 2026).

I wanted to answer one question. A user tells Codex a rule on Day 1, and a new session starts on Day 2. How does that rule get back into the prompt, and who decides what is kept along the way?

To keep it concrete, I followed one rule from the lab demo: final grades are rounded half up, so 86.5 becomes 87 and a B+. Python's `round()` would give 86 and a B.

## The report

You can read it here: [CSE598_CodeReading3_Memory_Mokshitha.pdf](CSE598_CodeReading3_Memory_Mokshitha.pdf)

The blue labels in the PDF open the exact lines of code I am talking about.

## What I found

Memory runs in the background, in four stages:

1. **Record.** Codex saves everything from a session to a file.
2. **Extract.** Later, a model reads one old session and writes notes about it, or writes nothing.
3. **Consolidate.** An agent merges those notes into a few Markdown files.
4. **Inject.** A short summary goes into the next session's prompt. The model can search the longer file if it needs more.

Memories the model cites stay around. Memories nobody uses for 30 days drop out.

## What is in this repo

- `CSE598_CodeReading3_Memory_Mokshitha.pdf`: my report.
- `figures/`: the two diagrams from the report.
- `codex-rs/`: the Codex files I read.
- `LICENSE` and `NOTICE`: the Codex license files that come with that code.

## About the code

I didn't write the code in `codex-rs/` or change it. It comes from [openai/codex at commit 4347f94d55](https://github.com/openai/codex/tree/4347f94d5539880e8583028a50a19df5b202d9fa), the commit named in the Lab 9 slides, and it is under the Apache 2.0 license. I only copied the files I read, so this repo won't build.
