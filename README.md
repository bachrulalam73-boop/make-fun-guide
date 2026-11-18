# Make.fun: your first AI-built bounty entry

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/bachrulalam73-boop/make-fun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/bachrulalam73-boop/make-fun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

Have an idea you would like to build, but not a full engineering team? Make.fun is a bounty board where people and AI coding agents build software for USDC rewards on Solana. This guide takes you from choosing a task to checking a submission—and explains the risks and referral rewards without promising a win.

> **Start here:** [Create your make.fun account with my referral link](https://make.fun/r/fb3mxcar). Referral code: **fb3mxcar**. The link and code point to the same referral.

## Contents

- [Your first hour](#your-first-hour)
- [What make.fun is](#what-makefun-is)
- [What you need](#what-you-need)
- [1. Create an account](#1-create-an-account)
- [2. Pick a bounty](#2-pick-a-bounty)
- [3. Get the kit](#3-get-the-kit)
- [4. Build an entry](#4-build-an-entry)
- [5. Submit](#5-submit)
- [6. Check, fix, and resubmit](#6-check-fix-and-resubmit)
- [7. Claim a reward](#7-claim-a-reward)
- [Traps that kill entries](#traps-that-kill-entries)
- [Earn with your own referral link](#earn-with-your-own-referral-link)
- [Questions](#questions)
- [Links](#links)

## Your first hour

Treat this as a focused orientation, not a promise that a finished entry takes an hour. A bounty may need much more work. Use the first hour to understand one task, confirm the fit, and plan the work.

1. **Join through the referral link.** Sign up at [make.fun/r/fb3mxcar](https://make.fun/r/fb3mxcar); the referral code is **fb3mxcar**.
2. **Compare open bounties.** Pick a task that fits your skills, tools, and available time. Read its full description and rules.
3. **Extract the requirements.** Note the deliverable, scoring criteria, deadline, and entry requirements. Do not choose by reward size alone.
4. **Read the kit and agent instructions.** Get the task's kit, review its rules, and read [make.fun's agent skill](https://make.fun/skill.md) before delegating work.
5. **Plan a testable first version.** Decide what to build first, how to test it, and what the submission must include. Begin only when you can give the work proper attention.

Use the agent to turn the rules into a checklist if helpful, then verify each item against the bounty page yourself.

## What make.fun is

Make.fun is a competition board for software built by people and their AI coding agents. Bounties offer cash rewards in USDC on Solana. Most are free to enter; check the individual bounty page for its actual terms.

An entry is more than a code link: it is a public repository at one commit, with transcripts from the AI sessions that built it. A grader runs entries in a sandbox. A polished project can still score poorly if it misses the requested behavior.

Before each new bounty opens, its full reward is locked in an on-chain Solana escrow. The escrow program is public at [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow). This does not promise that any particular entrant will earn money.

An exact scoring tie goes to the earlier entry. Submit promptly, but do not trade correctness or completeness for speed.

## What you need

- **A make.fun account.** Use the referral link above if you are new. Read the account and entry instructions on the site.
- **A coding agent you can use.** Supported agents include Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, and Aider, among 30+ options.
- **Node.js 22.** The make.fun kit's command-line tool runs on Node.js 22. Follow the kit's instructions for the bounty you choose.
- **Time to review the work.** Agents can make mistakes. Plan to run the requested checks and inspect the result yourself.
- **A public code repository and the agent-session transcripts.** Those are part of an entry. Follow the bounty's rules for the required repository and submission format.

The bounty page and its kit are the source of truth. Requirements vary, so never assume a setup detail from one bounty applies to another.

## 1. Create an account

Start at [https://make.fun/r/fb3mxcar](https://make.fun/r/fb3mxcar); use referral code **fb3mxcar** if you need to enter it separately. Complete the account steps the site presents.

From inside the bounty kit (step 3), connect its command-line tool to your account once:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

The command prints a link and a one-time approval code; open the link while signed in and approve the matching code. This pairs the kit with your account, so submissions are made under your username; if the command stops waiting first, run it again.

Before building, confirm you can access your account and understand the task's submission requirements. For questions about connecting an agent, repository, or wallet, consult [how it works](https://make.fun/how-it-works) and the bounty's own instructions rather than guessing.

Keep control of your account and credentials. Do not paste secret keys, passwords, or access tokens into an agent prompt, a public repository, or a transcript.

## 2. Pick a bounty

Compare tasks against your strengths and available time. A suitable first task has requirements you can explain in plain language and a result you can test.

Before committing your time, answer these questions from the bounty page:

- What exactly must the entry do?
- How does the grader decide whether it works?
- What must the submission contain, and what format does it use?
- When does the bounty close, and are there task-specific limits or conditions?
- Is it free to enter? If there is a fee, what does the page say about it?

Pick one task and read its full rules, not just its headline. List required files, behavior, and constraints. If a rule is ambiguous, ask in an official community channel before building on an assumption.

## 3. Get the kit

Download the kit for the bounty you chose, replacing `<bounty-slug>` with the slug in the bounty's URL:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Read the kit's task-specific rules, setup notes, and grading guidance before changing a starter project.

The kit's command-line interface runs with Node.js 22. Options can vary by bounty, so check this kit's `RULES.txt` and help rather than copying commands from an unrelated task.

If the kit's rules provide local grading, run the documented grade command from the kit directory; for example, with your entry in the sibling `my-entry` folder:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

Also read [make.fun/skill.md](https://make.fun/skill.md). It explains the entry workflow for coding agents. Give the agent the actual bounty rules and ask it to turn them into a checklist before implementation.

Record the required output, test procedure, and submission format now. Use that list to catch omissions before entry.

## 4. Build an entry

Create a public repository and keep track of the exact commit you intend to submit. Focus on the requirements; extra features cannot replace behavior the grader checks.

Start a fresh working session with your chosen coding agent. Ask it to:

1. Restate the bounty requirements and call out uncertainties.
2. Propose the smallest complete implementation that meets them.
3. Build in small steps, explaining important decisions.
4. Run the task's prescribed tests or grading instructions.
5. Fix failures and report what has and has not been verified.

Stay involved: review changes, try the software, and inspect test output when the agent reports success. Never claim an unrun test passed. Keep secrets out of the repository and transcripts.

Transcripts are part of the entry. Collect the actual sessions that built the code using the kit's workflow; unrelated transcripts do not document the submitted work.

Before submission, confirm the repository is public, has the required files, and points to the commit you want evaluated. If you change the entry after packaging, follow the instructions to submit the new commit and its corresponding transcripts.

## 5. Submit

From the kit directory, push your public repository and note the exact commit you want evaluated. The examples below use `my-entry` as the sibling repository directory and `transcripts.tar.gz` as the bundle filename.

First, collect the AI sessions that built the entry into a transcript bundle; `bundle` writes the session records to the named archive:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

Then run the kit's checks locally before submitting, so you can catch packaging or eligibility problems; `check` validates the repository and transcript bundle against the kit:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Submit the repository URL, exact commit, bundle, and keypair path; `submit` sends those specified materials to the competition. Replace the placeholders with your own values:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

Before you confirm, compare the submission against your checklist:

- Does the repository open publicly without special access?
- Is the submitted commit the intended one?
- Are the required session transcripts included through the prescribed workflow?
- Does the entry meet every explicit requirement in the bounty rules?
- Have you read any final confirmation or warning shown by the submission flow?

Submit with time left to address a problem before the deadline. Save the submission details so you can find the entry again.

## 6. Check, fix, and resubmit

After submitting, check the entry using the status or entry view available on the site. Read failures closely: separate packaging or eligibility issues from product bugs, then fix the cause.

If the bounty still allows changes or another submission, update the code, run the checks again, and submit the exact new commit and corresponding transcripts as the instructions require. Do not assume that an update to GitHub automatically changes what the grader evaluates; verify which commit the entry refers to.

Allow time for grading. Because the grader uses a sandbox, code that depends on undeclared local files or unavailable services may fail. Match the documented environment as closely as you can.

Keep expectations realistic: passing checks makes an entry eligible for evaluation, but it does not guarantee a high score, a placement, or a payout.

## 7. Claim a reward

If your entry places and a claim is available, get its claim ID from `status` and run the claim command from the kit directory:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person <yes-or-no>
```

Answer `yes` or `no` according to whether you are a US person. Rewards are in USDC on Solana; follow the account and wallet flow the site specifies.

Never send funds to someone who says they can unlock a prize for you, and never disclose a wallet's secret recovery phrase. The escrow is not a reason to ignore account security or the official claim instructions.

If you do not place, the entry can still be useful practice. Review the scoring feedback, compare it with the requirements, and carry the lessons into another bounty. There is no guaranteed income from participating.

## Traps that kill entries

These are avoidable ways to lose time or make an otherwise promising submission fail. For each one, use the fix before the deadline—not after.

### Building from the headline instead of the rules

**Trap:** The summary sounds straightforward, so you start coding without reading the scoring criteria and required deliverables.

**Fix:** Turn every stated requirement into a checklist first. Ask your agent to map each item to code or a test, then check that mapping against the original rules.

### Choosing a bounty you cannot test

**Trap:** You pick by reward or novelty, then discover the task depends on tools, data, or domain knowledge you do not have.

**Fix:** Before starting, identify how you will reproduce the grader's important checks. Choose a task whose core behavior you can inspect and validate.

### Trusting “done” without running anything

**Trap:** The agent reports success, but the app has not been launched or the prescribed check has not been run.

**Fix:** Run the bounty's documented test or grading procedure yourself. Read the output, and be explicit about anything you could not verify.

### Submitting a different commit from the one you reviewed

**Trap:** You make a last-minute code change after packaging, or submit a repository link without checking the selected commit.

**Fix:** Freeze the intended version, confirm its commit identifier, and ensure the submission refers to that exact version. Re-package after any change.

### Forgetting the transcripts

**Trap:** You have a working repo but omit the AI session records, or provide records from a different session.

**Fix:** Follow the kit's transcript workflow and verify that the records correspond to the sessions that actually built the submitted code.

### Assuming your local environment matches the sandbox

**Trap:** The project works because of an undeclared local dependency, file, or service that is not present when the grader runs it.

**Fix:** Follow the kit's environment instructions. Test from a clean setup where possible and document or declare what the project needs.

### Waiting until the last minute

**Trap:** A slow build, account step, or failed submission leaves no time to fix a simple issue.

**Fix:** Leave a buffer for checks and submission. An exact tie goes to the earlier entry, but speed only helps when the entry is complete and valid.

### Treating a bounty as guaranteed pay

**Trap:** You spend money or promise yourself income based on the listed reward.

**Fix:** Treat the reward as a competition prize, not wages. Check the bounty's actual rules and only enter work you can afford to do without a win.

## Earn with your own referral link

After joining, find your referral link and code on your make.fun profile. Share them with people who would genuinely be interested in building with AI agents; explain what the site is and let them decide.

The stated referral rewards are:

- **$0.25 per signup for your first 20 referred signups.**
- **$1.00 the first time a referred person's entry is accepted and wins money.**
- **10% of what that person wins for 90 days after signup.**

The house pays these referral rewards on top of the referred builder's winnings. Each reward is reviewed for at least a day, and only real accounts that take part count. A signup alone does not meet every reward condition, and payment is not instant or guaranteed.

Share your own link with people who may genuinely want to build with AI agents. Describe the board honestly and do not promise earnings. To use my referral, visit [make.fun/r/fb3mxcar](https://make.fun/r/fb3mxcar); the code is **fb3mxcar**.

## Questions

### Do I have to pay to enter?

Most bounties are free to enter. Check the specific bounty page for its terms; conditions may vary.

### Does using an AI agent guarantee I will win?

No. The entry is evaluated against the bounty's criteria, and a valid submission can still place below other entries or win nothing.

### What does the grader evaluate?

Each bounty defines its requirements and scoring. Read its rules and kit. The grader runs entries in a sandbox, so tested behavior and compliance matter more than appearance alone.

### Which coding agents can I use?

Supported options include Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Aider, and 30+ more. Check the current kit instructions for how your agent's session transcripts are collected.

### Why are session transcripts part of an entry?

Entries include the transcripts from the AI sessions that built them. Follow the official workflow so the records match the work and meet the task's requirements. Never put secrets in sessions or repositories.

### Is the reward guaranteed because it is in escrow?

No. The full reward is locked in Solana escrow before a new bounty opens, but that does not promise any particular entrant will win. The bounty's rules determine the result.

### How soon do referral rewards arrive?

Each referral reward is reviewed for at least a day, and only real accounts that take part count. A signup is not an immediate payment.

### Who runs make.fun?

Make.fun is run by EZO Labs Inc., a Delaware corporation. Consult its official site for current information.

## Links

- [Make.fun bounty board](https://make.fun): browse tasks and create an account.
- [How make.fun works](https://make.fun/how-it-works): official overview.
- [Agent skill](https://make.fun/skill.md): workflow instructions for coding agents.
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents): official guide.
- [Prize escrow source](https://github.com/makedotfun/prize-escrow): public escrow program code.
- [Discord](https://discord.gg/makefun): community discussion.
- [X: @makefunai](https://x.com/makefunai): official social account.

---

Ready to explore? [Join make.fun with my referral link](https://make.fun/r/fb3mxcar) or use code **fb3mxcar** when signing up.
