# Claude Code Output Styles

A small collection of [output styles](https://docs.claude.com/en/docs/claude-code/output-styles) for Claude Code. Each style changes how Claude *talks* to you in the terminal: tone, length, structure, and vocabulary. None of them change how carefully Claude works or verifies its results.

## Install

Copy the styles into your user-level output styles folder:

```bash
git clone https://github.com/elsung/claude-code-output-styles.git
mkdir -p ~/.claude/output-styles
cp claude-code-output-styles/output-styles/*.md ~/.claude/output-styles/
```

For a single project, copy them into `.claude/output-styles/` inside that project instead.

Then pick one inside Claude Code:

```
/output-style            # opens the picker
/output-style clear-terminal
```

You can also set a default in `~/.claude/settings.json`:

```json
{ "outputStyle": "Clear Terminal" }
```

## The styles at a glance

| Style | Best for | Length | Jargon |
|---|---|---|---|
| [Clear Terminal](output-styles/clear-terminal.md) | Day-to-day engineering work | Short, grows when needed | Kept exact, explained if unfamiliar |
| [Plain & Clear](output-styles/plain-clear.md) | Working in an unfamiliar codebase | Short chunks, scannable | Translated on first use |
| [Busy CEO](output-styles/busy-ceo.md) | Status updates and decisions | Very short, bullet-heavy | Minimal |
| [Aircraft Manual (STE100)](output-styles/aircraft-manual.md) | Procedures and runbooks | Short sentences, numbered steps | Defined once, one word per meaning |
| [Explain Like I'm 12](output-styles/explain-like-12.md) | Learning a new concept | Medium, built in layers | Real terms, defined gently |
| [ELI5](output-styles/eli5.md) | First intuition for a hard idea | Very short | None |

## How each style communicates

### Clear Terminal

The everyday default. Replies lead with the answer, result, or decision needed, with no preamble or narration of effort. Plain language surrounds exact technical details: paths, commands, model IDs, and error text are preserved verbatim in inline code.

What makes it distinct:

- **One point per sentence.** Active voice, named actors, no long parenthetical chains.
- **Smallest useful structure.** A paragraph for a simple answer, a flat list for distinct items, a table only when comparing the same fields.
- **Precise status.** Implemented, tested, committed, pushed, and deployed are kept separate. Confirmed causes are kept separate from hypotheses.
- **Scoped to chat only.** The rules apply to terminal replies, not to code, docs, or prompts Claude writes for you.

### Plain & Clear

Written for a sharp colleague who doesn't live inside your codebase. It prioritizes being understood over sounding precise.

- Translates every term, tool, flag, or identifier the first time it appears.
- Explains *why* something matters, not only *what* happened.
- Uses short sections with bold labels and allows a brief, accurate analogy.
- Closes with a checkpoint: the next step, or what to dig into.

### Busy CEO

Bottom line up front for a time-poor decision-maker.

- The first line is the answer, status, or ask.
- Every bullet stands alone. Numbers beat vague words ("3 boxes, 74% failure" over "several, high").
- Makes a recommendation instead of only listing options.
- Default shape: the line → why it matters → options or next step → the ask.

### Aircraft Manual (STE100)

Based on ASD-STE100 Simplified Technical English, the controlled language used in aircraft maintenance manuals. The goal is zero ambiguity for a tired reader.

- One instruction per sentence, imperative mood, active voice.
- Procedure sentences of 20 words or fewer; descriptions of 25 or fewer.
- One word for one meaning, with simple approved words ("use", not "utilize").
- Numbered steps, with WARNING and CAUTION before the step they protect and NOTE after.

### Explain Like I'm 12

For a bright, curious learner who can handle real ideas.

- Uses the real term, then defines it in the same sentence.
- Builds up one layer at a time, with analogies from games, sports, and phones.
- Covers cause and effect and trade-offs, but skips heavy formalism.

### ELI5

For a first "ohhh, I get it" moment.

- Tiny words and everyday analogies like LEGO, mail, and kitchens.
- One idea at a time, a few short sentences each.
- The analogy must still be true. Simple never means wrong.

## Shared principle

Every style ends with a "keep the substance" rule. Simpler or shorter language never means dropping caveats, risks, or decisions the reader needs. Each style changes the delivery, not the rigor.

## Writing your own

An output style is a Markdown file with frontmatter:

```markdown
---
name: My Style
description: One line shown in the /output-style picker
---

Instructions for how Claude should communicate.
```

Note that a custom output style replaces the coding-focused parts of Claude Code's default system prompt unless you add `keep-coding-instructions: true` to the frontmatter. See the [official docs](https://docs.claude.com/en/docs/claude-code/output-styles) for details.

## License

MIT
