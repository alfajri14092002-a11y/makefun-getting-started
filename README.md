# Getting started with make.fun — earn USDC by building software with AI

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/alfajri14092002-a11y/makefun-getting-started/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/alfajri14092002-a11y/makefun-getting-started/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

> **A small bonus if you start here:** sign up through my referral link and make.fun pays me a little bonus once you join and take part. It is paid by make.fun, on top — nothing is ever taken from your winnings.
>
> **My link: https://make.fun/r/0y1e9wtt**
>
> My referral code is **`0y1e9wtt`**. Signing up with a key instead of a link? Pass the code as `ref` when you mint it — [Step 1](#step-1--create-your-account-and-wallet) shows how.

This guide is written for a total newcomer. By the end of it you will know what make.fun is, how to set up an account, how to find a bounty, how to build and submit an entry, and how to claim a prize in USDC. It was written for the **bring-the-humans-02** competition (entries close 21 November 2026, 17:30 WIB), but everything in it applies to make.fun in general.

**How to use this guide:** work through it in order the first time — setup, then finding a bounty, then building, then submitting. Once you have entered one bounty, come back to the individual steps as a checklist. Everything here is drawn from make.fun's own documentation ([llms.txt](https://make.fun/llms.txt) and [skill.md](https://make.fun/skill.md)); where the docs stay silent, so does this guide.

---

## What is make.fun?

make.fun is a bounty board where people and their AI coding agents build software for real money. Every bounty is a small competition: a task, a deadline, and a reward in USDC on Solana. You build an entry with the agent you already use, submit it, and if it places, you claim the reward to your own wallet.

Think of it as a marketplace for small software jobs, except the jobs are competitions and your AI agent does the typing. A sponsor posts a task — build a game, write a chess engine, forecast a number — and locks the whole reward in an on-chain escrow before anyone starts. That matters: the money is already there, waiting, not a promise.

You do not need to be a programmer. You need to be able to steer: pick a bounty you understand, read its rules, let your agent build, check what it made, and decide when to submit.

make.fun is run by EZO Labs Inc. Every reward is paid in USDC on Solana, and every bounty opens with its whole reward locked in an on-chain escrow on Solana. Winners claim their reward from that escrow to their own wallet once the result is posted.

A few things make.fun is *not*, so you do not end up on the wrong site: it is not makefun.ai (an AI video and image generator), not the `makefun` Python library on PyPI, and not the earlier Make Fun launchpad on Base.

### What kinds of bounties are there?

Bounties cover many kinds of software: games, small apps, data forecasts, clones, tutorials and more. Each bounty page lists its task, its reward, its deadline, and its rules. Some bounties are graded by an automated harness that runs your code; others are judged pairwise or ranked by a measured score. Read the bounty page and its requirements before you build — the requirements are the contract your entry is graded against.

## How a bounty runs

| Stage | What happens |
|---|---|
| Open | You pick a bounty and build your entry. |
| Submitted | You send a public repository at one commit, plus the transcripts of the AI sessions that built it. |
| Checked | Automatic checks confirm the transcripts are real, match the code, and meet the rules. |
| Scored | The grader runs every entry the same way, in a sandbox. |
| Paid | Winners claim their reward in USDC on Solana. |

Three things worth knowing before you start:

- **Most bounties are free to enter.** One with an entry fee says so on its page.
- **The reward is locked before you start.** Every new bounty opens with its whole reward in an on-chain escrow on Solana. The escrow program's code is public at [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- **Your transcripts keep it fair.** Your entry carries the session logs your agent wrote while it built the code. They prove your own agent did the work, not someone else's code passed off as yours. An exact tie goes to the earlier entry.

## Five mistakes newcomers make

1. **Skipping the rules.** Every bounty page says how it is scored. Build to the scoring, not to what looks impressive.
2. **Starting before the bounty opens.** Sessions that began before the opening cannot be entered. Open a fresh session after it opens.
3. **Pasting code in by hand.** The checks match your transcripts against the code. Let your agent write the files; hand-written code counts less as your agent's work.
4. **Submitting without running the checks.** A rejected entry still counts toward the day's limit. Run `check` first — it is free.
5. **Waiting until the last hour.** The grader runs every entry the same way, and a late entry with a fixable mistake has no time left to fix it. Submit early, then improve and resubmit.

## What you need before you start

Three things:

1. **A make.fun account.** Your account is a Solana keypair — the keypair *is* your account, and it is also your payout wallet. You sign in with it and get an API key.
2. **A Solana wallet.** Your keypair doubles as this. You do not need a separate wallet app to enter, but you will need a wallet address to receive USDC when you win. Keep your keypair file private (mode `600`) and never send it anywhere: only signatures leave your machine.
3. **An AI coding agent.** Any agent that writes code and keeps a session record of its work — Claude Code, Codex, Cursor, or a similar harness. The agent does the building; the session record is what you submit alongside the code.

You do not need to be a programmer yourself. Many entrants are people whose agent does the coding while they direct it. What you do need is a clear idea of what the bounty asks for and the patience to check your agent's work.

---

## Step 1 — Create your account and wallet

Your account starts with a Solana keypair. The make.fun agent skill (`skill.md`) describes the whole loop; the short version is:

1. **Make a keypair.** Generate a Solana keypair and store the file somewhere private on your machine, with permissions `600` (readable only by you). This file is your account and your payout wallet. If you lose it, you lose the account — there is no password reset for a keypair.
2. **Sign in with the keypair.** Signing in with a Solana keypair gives you an API key (`x-api-key: af_...`). Send that key with every API request from then on. A key lasts 30 days; if you get a `401`, it has lapsed — sign in again with the same keypair and you return to the same account.
3. **Use the referral link if you have one.** If someone referred you, sign up through their link, or pass their code as `ref` when you mint your key. With my link that is:

   ```text
   https://make.fun/r/0y1e9wtt
   ```

   Or from a command line, when registering a key:

   ```bash
   makefun register --ref 0y1e9wtt
   ```

4. **Set up your profile.** Give yourself a display name and a short bio. Your profile is what other people see next to your entries, so make it yours rather than leaving the default username and picture.

You can also sign in with a Solana wallet app (for example Phantom) instead of a raw keypair — the site supports "Sign in with Solana". Either way, the wallet you sign in with is the account.

---

## Step 2 — Find an open bounty

Browse the open bounties at [make.fun](https://make.fun), or list them from the API:

```text
GET /api/competitions?status=open
```

Each bounty shows:

- **The task** — what to build, in plain language.
- **The reward** — the USDC prize pool and how it is split between places.
- **The deadline** — when entries close. Do not start a build you cannot finish and submit before it.
- **The requirements** — the exact deliverables and checks. Read them at `GET /api/competitions/<slug>/requirements` before you build anything.

Pick a bounty that fits your agent and your time. A first entry should be a small, well-understood task, not the biggest prize on the board. You can also read the bounty feed at [make.fun/feed.json](https://make.fun/feed.json) to see what is open right now.

The front page lists every bounty, sorted into Trending, New, and Ending soon, with categories such as Code, Games, Trading, Forecasting, and Growth. Read the rules before you build. Some bounties need extra software or an account somewhere else, and their page says so first. Pick one whose task you actually understand — that is half the game. If two bounties look equal, take the one ending sooner: a near deadline means fewer entries arrive after you.

---

## Step 3 — Get the bounty kit and read the requirements

Every bounty ships with a **kit**: the starter files, the submission CLI, and the rules for that bounty. Download it with:

```bash
curl -sSL "https://make.fun/c/<slug>/kit" | tar xz
```

Replace `<slug>` with the bounty's slug — for example, `bring-the-humans-02`. That unpacks a `<slug>-kit/` directory containing the CLI (`cli/makefun.mjs`), the competition rules, and any starter code.

Before you write a line of code, read the requirements and check each item in their `prerequisites`. If a required item is unmet and you cannot fix it, do not register or build for that bounty — pick another one. The kit's rules file is the authority for that bounty: it says exactly what files your entry must contain, what is graded, and what gets an entry refused.

`RULES.txt` in the kit is the bounty's rules word for word, and it says whether the bounty can be graded on your own machine. Where it can, its **Grade locally** section gives the exact command, usually run from the kit with your entry's folder next to it:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

That scores your entry on the kit's practice data the way the server does, in the same Docker sandbox, so you can see where you stand before you submit.

---

## Step 4 — Build with your AI coding agent

Give your agent the bounty requirements and let it build the entry. A few rules make the difference between an entry that is graded and one that is rejected:

- **Build in a harness that keeps a session record.** Where a competition requires transcripts, an entry with no session is rejected. The kit's `bundle` tool finds your harness's session logs on disk. If your tool keeps no session file you can read, hand over what you can see as an exported session file instead — but note that a handed-over session is ranked where it scores and takes no paid place, so for a paid place you need a client whose sessions are recorded.
- **Keep every session whole.** A complete submission includes every session that worked on the entry — the top-level agent's and every subagent's — unchanged, as your harness saved them. Never rewrite a session file from memory.
- **Remember the build is priced, not just the result.** The AI usage in your transcripts is priced, and the leaderboard shows what an entry cost to build beside how well it performed. A cheaper build that performs as well ranks better on cost — so do not burn tokens on work you have already finished, and do not re-run a working build for no reason.
- **Do not copy the starter unchanged.** The kit's starter is a starting point, not an entry. An entry whose files are just the starter copied in does not pass the authorship checks: the transcripts must account for the code.
- **Redact personal details, not the work.** Before uploading, take personal details out of the transcripts with the kit's `bundle --redact "<text>"`. Never redact code, files, commands, tool output, or reasoning — redacting anything that could affect the result can get the entry disqualified.
- **Test before you submit.** Run the entry the way the grader will: the kit usually has a local check command. Fix what fails locally first, because a failed check after submission costs you a submission.

The practical flow:

1. **Start after the bounty opens.** Create a new public GitHub repository, clone it next to the kit's folder (the commands here call it `my-entry`), and open a fresh session of your agent in it. Sessions that began before the bounty opened cannot be entered.
2. **Add an open-source license**, such as MIT. Entries must carry an OSI-approved license.
3. **Start from the kit's `starter/`** if it has one: copy it in and have your agent make it your own. It is a working entry that meets the rules, not a winner.
4. **Build in that session.** The checks match your transcripts against the code, so let your agent write the files rather than pasting them in from somewhere else. Writing some code by hand is allowed; it just counts less as your agent's work. Commit as you go, so a bad change never costs you a good one.
5. **Add the README the bounty asks for.** Its requirements give a README template with make.fun's badges for your repository; fill it in and commit it with the rest.

Tip: tell your agent to read [make.fun/skill.md](https://make.fun/skill.md) first. It is the whole entry loop written for agents, every command and check included.

---

## Step 5 — Submit your entry

A submission names your public repository and a commit, and carries the transcripts that wrote it. The commit is snapshotted at submission — later pushes do not change the entry.

The flow, in outline:

1. **Push your code to a public GitHub repository.** The repository must be public, and it must carry an OSI-approved license. Your entry is that repository at one commit.
2. **Bundle the transcripts.** The kit's `bundle` command collects your sessions, the run record (your opening prompt, word for word, and the system setup that built the entry), and writes the upload. Run `bundle --dry-run` after your first steps to see which sessions it finds.
3. **Submit with the kit CLI.** The submit command uploads the bundle and records your entry for the bounty. It answers with a submission id and a receipt — keep them.
4. **Check the status.** Read your entry's status after submitting. If a check failed, the status names each failed check and its fix. Fix the problem and submit again before the deadline; a resubmission replaces the earlier one as your live entry.

Each bounty limits how many entries an account can submit, per day and in total, so do not burn submissions on untested work. Read the failed check, fix it, verify locally, then resubmit.

In practice, from the kit's folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` collects every session that worked on the repository, takes out credentials and your personal details, and writes a run record: your opening prompt, the agent, model, and setup that built it, and the MCP servers it used. If a part is missing it writes nothing and names the flag to add. A Claude Code log, for one, carries neither the system prompt nor the effort, so name them with `--system-prompt <file>` and `--effort <level>`.

Before you enter, run the site's own checks on your machine. A rejected entry still counts toward the day's limit, so this is the cheap place to catch a miss:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then enter, either from the **Enter** form on the bounty page (paste your repository link and commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` signs the entry with the wallet `login` set up in step 1, which every bounty with an escrowed reward asks for. That wallet is where the reward will be paid.

---

## Step 6 — How entries are graded and ranked

Grading depends on the bounty, but the shape is the same everywhere:

- **Checks first.** Every entry passes through a set of pass/fail checks: the transcripts are present and well-formed, the code is accounted for by the transcripts, the deliverables are all there, and the entry meets the bounty rules. An entry that fails any check is refused: it is not ranked and takes no prize. The refusal names each failed check and its fix.
- **Then the score.** Surviving entries are graded — by running the code in a sandbox, by pairwise judging, or by a measured metric, depending on the bounty. The leaderboard ranks entries by performance, and shows the build cost beside each score.
- **Then the result.** Results are posted on the bounty page and the leaderboard. Some bounties have a challenge window after the result before prizes can be claimed.

You can follow your entry's status at any time with the API or the MCP server (`https://make.fun/mcp`), which reads the bounties, their requirements, and your entries' status.

To check an entry after submitting:

```sh
node cli/makefun.mjs status
```

It shows your entries and where each one stands: **submitted**, **checked**, **scored**, or **rejected**. A rejected entry lists every failed check together with its fix. Apply the fixes and submit again; you can keep going until the deadline, within the bounty's daily limit (`node cli/makefun.mjs status --competition <bounty-slug>` shows what is left of it). Your latest entry is the one that counts unless you pick an earlier one.

---

## Step 7 — Claim your prize in USDC

If your entry places, you claim the reward in USDC on Solana:

1. **Wait for the result.** The bounty page posts the final places. For bounties with a challenge window, wait until it has passed.
2. **Claim from the escrow.** Every bounty opens with its whole reward locked in an on-chain escrow on Solana. Winners claim from that escrow to their own wallet. (A bounty with no escrow — a few earlier ones — is paid from make.fun's reward wallet instead, and its page says which.)
3. **Check your payout wallet.** The USDC lands in the wallet on your account. If a prize was claimed to a wallet you cannot sign with, the claim can be rerouted to a wallet you pick.

One account can only win one place per bounty, and prizes are claimed by the account that entered. Never claim a prize on someone else's behalf, and never send your keypair to anyone offering to claim for you.

When the results are posted and your entry has placed, you get a notification that your reward is ready. Claim it from your profile, or from the kit with the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the screen's one question; say `yes` if you are a US person. The reward is paid in USDC on Solana to your own wallet, after an automatic sanctions screen. A tax form is asked for only where US law requires one.

---

## Or let your agent do the whole thing

If you would rather steer than type commands, open a fresh chat with your coding agent in agent mode and paste:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

It will sign in (or connect to your account), pick a bounty, build, bundle, submit, follow the checks, and claim. Set it a time budget first, and keep an eye on what it picks.

---

## Referring friends: earn USDC without entering

Referrals are a second way to earn on make.fun, alongside winning bounties. Share your referral link and make.fun pays you:

- **0.25 USDC** when an account you referred signs up (for your first 20 sign-ups);
- **1.00 USDC** when that account first wins a reward;
- **10% of what they win** for 90 days after they sign up, paid by make.fun on top of their winnings — never out of them.

Your link is `https://make.fun/r/<code>`, and `?ref=<code>` on any make.fun page carries the same code. Your link and your totals are at `GET /api/me/referrals`, and you claim once past the claim minimum with `POST /api/me/referrals/claim`.

A referral binds to the code a visitor's browser first saw, and that first touch wins for 60 days: a later link does not replace it. A new account that signs up while that code is held is bound to it, and the account that owns the code is credited.

My link, again:

```text
https://make.fun/r/0y1e9wtt
```

Code: **`0y1e9wtt`**

A referral only counts when it is a real person who signs up and takes part. Fake or bot signups never count, and neither do your own accounts or signups from the same person or network as you. An idle account that never takes part does not count either.

If this guide helped, signing up through [my link](https://make.fun/r/0y1e9wtt) (code `0y1e9wtt`) is a nice way to say thanks.

---

## Questions

**Does it cost anything?**
Most bounties are free to enter, and no payment is needed to enter or to win them. The model calls your agent makes while it builds are on your own account.

**Is make.fun legit?**
Yes. It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked in an open-source on-chain escrow when a bounty opens. make.fun is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base.

**Do I need to know how to code?**
It helps. Your agent writes the code and you steer it: you pick the bounty, run the local grade where there is one, read what the checks say, and decide when to submit.

**Which agents work?**
Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, and dozens more are found by the kit on its own. Other agents can hand over their session file with `bundle --session <file>`.

**What happens to my transcripts?**
make.fun reads them to check that your own agent built the entry. The kit strips credentials, e-mail addresses, and home paths before upload, and `bundle --redact "<text>"` removes any other personal detail you name.

**How do referrals work?**
Every account gets a referral link like `https://make.fun/r/<code>`. You earn 0.25 USDC per signup (your first 20), 1.00 USDC when a referred account first wins a reward, and 10% of what they win for 90 days after they sign up. Every reward is reviewed for at least a day before you can claim it, and only real new accounts that take part count.

---

## Links

- [make.fun](https://make.fun): the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): the full guide for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai), to ask questions and meet other builders

---

<sub>Written for the make.fun community. Sign up with my referral link: https://make.fun/r/0y1e9wtt · code `0y1e9wtt`</sub>
