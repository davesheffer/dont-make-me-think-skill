# dont-make-me-think

A Claude Code skill that applies usability principles to your app development workflow. It is built on Steve Krug's *Don't Make Me Think, Revisited* and *Rocket Surgery Made Easy*, with the core UX canon added: Nielsen's 10 heuristics and severity scale, Laws of UX, NN/g research on forms, errors and mobile, and the numbers from WCAG 2.2 AA.

## What it does

It runs in one of four modes, each with a fixed output format:

| Mode | When it triggers | What you get |
|---|---|---|
| **Review** | "review this screen", a screenshot, a component | Severity-ranked table (0–4) with the principle behind each finding, markup bugs that change behavior, missing states, delete list, trunk test, top 3 fixes, and a validation task. Has a brief variant. |
| **Design** | "design / build a screen or flow" | The screen's one job, what was left out, layout in hierarchy order, copy, states (empty, loading, error, success), a five-move self-check, and a paper-prototype test task |
| **Copy** | Button labels, errors, empty states, instructions | Each string followed by a one-line *why*. It may answer "no text" and say what replaces it. |
| **Test** | "how do we test this?" | A filled-in Krug-style DIY test plan: 3 users, scenario tasks, session script, same-day debrief |

All four modes run the **five Krug moves**: delete before you fix, the scan test, the trunk test, counting mindless clicks, and a goodwill ledger.

RTL (Hebrew/Arabic) checks and gender-neutral Hebrew copy guidance are built in.

## Install

**As a plugin** (Claude Code):

```
/plugin marketplace add davesheffer/dont-make-me-think-skill
/plugin install dont-make-me-think@dont-make-me-think
```

**As a personal skill** (copy only the skill folder):

```bash
git clone https://github.com/davesheffer/dont-make-me-think-skill
cp -r dont-make-me-think-skill/skills/dont-make-me-think ~/.claude/skills/
```

Claude loads the skill automatically when you design, review or write copy for UI. You can also invoke it directly with `/dont-make-me-think`.

## Layout

```
skills/dont-make-me-think/
  SKILL.md               modes, five moves, output contracts
  references/krug.md     Krug's principles as runnable checks
  references/canon.md    Nielsen, Laws of UX, forms/errors/mobile, WCAG 2.2, RTL
  references/copy.md     microcopy recipes (EN + HE)
  references/testing.md  DIY usability test loop, script, debrief
```

## How it was tested

The skill was built test-first: the same scenarios (a mobile form review, a new screen design, UI copy, and a usability test plan) were run against agents without the skill and then with it. Without the skill, agents wrote the instruction text Krug would delete, gave findings no principle or severity rationale, skipped the trunk test, and proposed a heavyweight test plan. With the skill, those gaps closed, and markup bugs that change behavior were caught in 3 out of 3 repeated runs.

## Credits

The principles are summarized and paraphrased from Steve Krug's books, which are worth buying and reading. This project is not affiliated with or endorsed by Steve Krug, Nielsen Norman Group, or Jon Yablonski (Laws of UX).
