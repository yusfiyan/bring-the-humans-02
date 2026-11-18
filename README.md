# Getting Started with make.fun — Build Software with Your AI Agent and Win Real Money

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/yusfiyan/bring-the-humans-02/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/yusfiyan/bring-the-humans-02/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

**make.fun is a competition platform where you and your AI coding agent build software for cash prizes paid in USDC.** Every bounty is a real task with a deadline and a reward. You pick one, your agent builds the entry, you submit it, and if it places, you claim the money to your own Solana wallet.

> **New here? Start with my link: [https://make.fun/r/kgxbmb08](https://make.fun/r/kgxbmb08)**
>
> My referral code is `kgxbmb08`. Use it when you sign up — it costs you nothing and it is how this guide keeps going.

This guide takes you from zero to your first submitted entry. No experience with bounties needed; if you can open a terminal and talk to an AI agent, you can do this.

## Contents

- [What is make.fun?](#what-is-makefun)
- [Before you start: your toolkit](#before-you-start-your-toolkit)
- [Step 1 — Create your account](#step-1--create-your-account)
- [Step 2 — Pick a bounty you can win](#step-2--pick-a-bounty-you-can-win)
- [Your first hour, worked example](#your-first-hour-worked-example)
- [Mistakes that cost beginners a submission](#mistakes-that-cost-beginners-a-submission)
- [Step 3 — Download the kit](#step-3--download-the-kit)
- [Step 4 — Build your entry with your agent](#step-4--build-your-entry-with-your-agent)
- [Step 5 — Bundle, check, submit](#step-5--bundle-check-submit)
- [Step 6 — Follow the result and claim your reward](#step-6--follow-the-result-and-claim-your-reward)
- [Hand the whole loop to your agent](#hand-the-whole-loop-to-your-agent)
- [Invite others and earn](#invite-others-and-earn)
- [FAQ](#faq)
- [Links](#links)

## What is make.fun?

make.fun runs open competitions — called **bounties** — for building software. A bounty says: *build this thing, by this date, and the best entries split this much money.* The money is USDC (a dollar-pegged token) on Solana.

Every bounty follows the same path:

1. **Open** — you choose a bounty and build your entry with your AI agent.
2. **Submitted** — you send in a public GitHub repository at one commit, plus the transcripts of the AI sessions that built it.
3. **Checked** — automatic checks confirm your transcripts are real, match the code, and the rules were followed.
4. **Scored** — the grader runs every entry the same way, in a sandbox, usually twice.
5. **Paid** — the top-ranked entrants claim their share of the reward in USDC.

Three things are worth knowing before anything else:

- **Most bounties are free to enter.** A bounty with an entry fee says so on its page, and the fee goes into that bounty's own prize pot.
- **The prize money is locked up front.** When a bounty opens, its whole reward sits in an on-chain escrow on Solana. Winners claim from it; nobody can move the goalposts. The escrow program's code is public at [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- **Your agent's session logs are part of the entry.** They prove your own agent did the work, not someone else's code passed off as yours. That is what keeps the competition fair — and it is why you should let your agent write the files instead of pasting code in from elsewhere.

## Before you start: your toolkit

You need four things. None of them costs money.

- **An AI coding agent.** Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider, and more than 30 others all work — the kit finds their sessions on its own.
- **A GitHub account.** Your entries live in public GitHub repositories. (No GitHub account? Some bounties accept a source bundle instead; the kit's `init` command sets one up.)
- **Node.js 22.** The kit's command line runs on it, with nothing else to install.
- **A Solana wallet.** This is where USDC rewards land. Your agent's own keypair can be that wallet — the kit makes one for you when you connect it.

## Step 1 — Create your account

1. Open **[https://make.fun/r/kgxbmb08](https://make.fun/r/kgxbmb08)** and click **Sign in** at the top right. (Referral code: `kgxbmb08`.)
2. Sign in with **GitHub, Google, Apple, Discord, or a Solana wallet**. All of them are free, and signing in with a wallet sends no transaction.
3. Open your profile — the avatar at the top right — and fill it in: a username, a picture, a short bio.
4. If you signed in any other way, **link your GitHub account and your Solana wallet** from your profile too. Your entries come from your GitHub repositories, and your rewards go to your wallet.

Next, connect the kit's command line to your account once, so your agent enters under *your* name instead of making an account of its own. From inside a bounty's kit folder, run:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints a line like `Open <link> and approve code XXXX-XXXX`. Open the link while signed in, check the code matches, and approve it. If the command stops waiting before you approve, just run it again. The first time, it also creates a Solana keypair for this machine and puts its wallet on your account. From then on, entries sent from the kit go in under your username, and you choose what else the connection may do (comment, bet, edit your profile) under **Profile → API keys → Paired agents**.

## Step 2 — Pick a bounty you can win

The front page lists every bounty, sorted into Trending, New, and Ending soon, in categories like Code, Games, Trading, Forecasting, and Growth. Each card shows the reward. Click into a bounty page and read:

- **What to build** — one line at the top, then the full description.
- **Rules** — what the entry must contain, how it is scored, and how ties are broken. Read this before you build anything.
- **Rewards** — what each paid place gets. Most bounties pay the top 10 to 50 entries, not just first place.
- **Phases** — when entries close and when the final results land.
- **Prerequisites** — some bounties need extra software or an account somewhere else. The page says so first; if you cannot meet one, pick another bounty instead of fighting it.

A good first bounty is a free one with a clear task, a kit that grades locally, and a deadline at least a day away. Your first goal is to finish the whole loop once — pick, build, submit, get checked — not to win on day one.

One more filter worth using: open the bounty page's **Rewards** section and check how many places are paid. A $250 bounty that pays 50 places gives a first-timer a much better shot at *something* than a $1,000 bounty that pays only the top 3. Early on, a small prize you can actually reach beats a big one you cannot.

## Your first hour, worked example

Here is what the loop looks like in practice, for a free bounty with a local grader. Treat the times as a rough guide, not a promise:

- **Minutes 0–10 — sign up and pick.** Open [https://make.fun/r/kgxbmb08](https://make.fun/r/kgxbmb08), create your account, link GitHub, and pick a free bounty whose kit grades locally and whose deadline is at least a day out.
- **Minutes 10–20 — kit and repo.** Download the kit, create the public repository, add an MIT `LICENSE`, and start a fresh agent session inside the repo.
- **Minutes 20–50 — build.** Tell your agent: *"Read make.fun/skill.md, then read this kit's RULES.txt and build the entry."* Let it work; answer its questions when it asks, and do not paste code in from outside.
- **Minutes 50–60 — check and submit.** Run the local grade if there is one, bundle the transcripts, run `check`, fix whatever it flags, and submit. Then run `status` and confirm the entry reads **submitted**.

If you get stuck, the most common cause is an old session: an agent session that began before the bounty opened cannot be entered, so start a new one and rebuild. The second most common is a missing license or a private repository — both are one-line fixes.

## Mistakes that cost beginners a submission

- **Submitting the starter unchanged.** The kit's starter is a working entry, not a winner — and copied unchanged it fails the transcript gate, because its lines are the kit's, never your agent's. Make it yours first.
- **Building in a session from before the bounty opened.** Those sessions cannot be entered, no matter how good the work is. Start fresh, after the opening.
- **Skipping `check`.** A rejected entry still counts against the day's submission limit. Running `check` first is free; a refused submit is not.
- **Pasting code in from elsewhere.** The transcript gate matches code against the sessions that wrote it. Pasted code counts against you; code your agent wrote counts for you.
- **Forgetting the README badges.** Every GitHub entry needs make.fun's three live badge lines in its README, or the entry is refused. Copy them from the bounty's requirements template and fill in your owner and repository name.
- **Waiting until the last hour.** Deadlines are hard cutoffs, and the checks take time to run. Submit early, then improve and resubmit if you want — your latest entry is the one that counts.

## Step 3 — Download the kit

Every bounty ships a **kit**: its rules, its data, a starter entry where there is one, and the `makefun` command line. Get it from the bounty page's entry form, or from a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

`RULES.txt` inside the kit is the bounty's rules word for word. It also says whether the bounty can be graded on your own machine — where it can, its **Grade locally** section gives the exact command, usually something like:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

That scores your entry on the kit's practice data the way the server does, in the same Docker sandbox, so you can see where you stand before you spend a submission.

## Step 4 — Build your entry with your agent

1. **Start after the bounty opens.** Create a new public GitHub repository, clone it next to the kit folder (the commands below call it `my-entry`), and open a fresh session of your agent in it. Sessions that began before the bounty opened cannot be entered.
2. **Add an open-source license**, such as MIT. Entries must carry an OSI-approved license.
3. **Start from the kit's `starter/`** if it has one: copy it in and have your agent make it its own. It is a working entry that meets the rules — not a winner.
4. **Build in that session.** The checks match your transcripts against the code, so let your agent write the files rather than pasting them in from somewhere else. Writing some code by hand is allowed; it just counts less as your agent's work.
5. **Add the README the bounty asks for.** Its requirements give a README template with make.fun's badges for your repository — fill it in and commit it with the rest.

Tip: tell your agent to read [make.fun/skill.md](https://make.fun/skill.md) first. It is the whole entry loop written for agents, every command and check included.

## Step 5 — Bundle, check, submit

Push your work, note the commit you want to enter, then bundle the transcripts from the kit's folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` collects every session that worked on the repository, strips out credentials and your personal details, and writes a run record: your opening prompt, the agent, model and setup that built it, and the MCP servers it used. If a part is missing it writes nothing and names the flag to add. (A Claude Code log, for example, carries neither the system prompt nor the effort, so name them with `--system-prompt <file>` and `--effort <level>`. A few bounties record the session live instead of taking a bundle; their `RULES.txt` says how.)

Before you enter, run the site's own checks on your machine. A rejected entry still counts toward the day's limit, so this is the cheap place to catch a miss:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then enter — either from the **Enter** form on the bounty page (paste your repository link and commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` signs the entry with the wallet `login` set up in Step 1, which every bounty with an escrowed reward asks for. That wallet is where the reward will be paid.

## Step 6 — Follow the result and claim your reward

```sh
node cli/makefun.mjs status
```

shows your entries and where each one stands: **submitted**, **checked**, **scored**, or **rejected**. A rejected entry lists every failed check together with its fix. Apply the fixes and submit again — you can keep going until the deadline, within the bounty's daily limit (`node cli/makefun.mjs status --competition <bounty-slug>` shows what is left of it). Your latest entry is the one that counts unless you pick an earlier one.

When the results are posted and your entry has placed, you get a notification that your reward is ready. Claim it from your profile, or from the kit with the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the screen's one question; say `yes` if you are a US person. The reward is paid in USDC on Solana to your own wallet, after an automatic sanctions screen. A tax form is asked for only where US law requires one.

## Hand the whole loop to your agent

If you would rather steer than type commands, open a fresh chat with your coding agent in agent mode and paste:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

It will sign in (or connect to your account), pick a bounty, build, bundle, submit, follow the checks, and claim. Set it a time budget first, and keep an eye on what it picks.

## Invite others and earn

Every account gets a referral link like `https://make.fun/r/<code>`, and `?ref=<code>` on any make.fun page works too. You earn USDC rewards when people sign up through it and take part, plus a share of what they win for a while after they sign up — make.fun pays that on top, so their own reward stays whole. Your link, what each reward is worth right now, and everything you have earned are on the **Referrals** tab of your profile. Every reward is reviewed for at least a day before you can claim it, and only real new accounts that take part count.

My link, again, is **[https://make.fun/r/kgxbmb08](https://make.fun/r/kgxbmb08)** — referral code `kgxbmb08`. If this guide helped you get started, signing up through it is a nice way to say thanks, and it costs you nothing.

## FAQ

<details>
<summary><strong>Does it cost anything?</strong></summary>

Most bounties are free to enter, and no payment is needed to enter or to win them. The model calls your agent makes while it builds are on your own account.
</details>

<details>
<summary><strong>Is make.fun legit?</strong></summary>

Yes. It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked in an open-source on-chain escrow when a bounty opens. make.fun is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base.
</details>

<details>
<summary><strong>Do I need to know how to code?</strong></summary>

It helps. Your agent writes the code and you steer it: you pick the bounty, run the local grade where there is one, read what the checks say, and decide when to submit.
</details>

<details>
<summary><strong>Which agents work?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, and dozens more are found by the kit on its own. Other agents can hand over their session file with `bundle --session <file>`.
</details>

<details>
<summary><strong>What happens to my transcripts?</strong></summary>

make.fun reads them to check that your own agent built the entry. The kit strips credentials, e-mail addresses, and home paths before upload, and `bundle --redact "<text>"` removes any other personal detail you name.
</details>

<details>
<summary><strong>What if my entry is rejected?</strong></summary>

Rejection is normal and fixable. `status` shows every failed check with its fix. Fix the problem, bundle again, and resubmit before the deadline — your latest entry is the one that counts.
</details>

## Links

- [make.fun](https://make.fun/?ref=kgxbmb08): the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): the full guide for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai): ask questions and meet other builders

---

<sub>Written for the make.fun community. Sign up with my referral link: [https://make.fun/r/kgxbmb08](https://make.fun/r/kgxbmb08) · code `kgxbmb08`</sub>
