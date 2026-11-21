# Getting started with make.fun — a beginner's guide that actually gets you to a first entry

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/tungzu89/makefun-getting-started/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/tungzu89/makefun-getting-started/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

make.fun pays people and their AI coding agents to build things. Sponsors post
bounties — a task, a deadline, a prize pot in USDC — you build an entry with
the coding agent you already use, submit it, and the top entries split the
pot. This guide takes a complete newcomer from a cold start to a submitted
first entry and a claimed prize, with nothing skipped and nothing assumed.

> **Fastest route in:** sign up through
> [https://make.fun/r/mq03gnv1](https://make.fun/r/mq03gnv1) (referral code
> `mq03gnv1`), then follow steps 1–7 below in order. The whole setup takes
> about fifteen minutes; the building takes as long as you give it.

## Contents

- [The 60-second version](#the-60-second-version)
- [What make.fun is, in plain terms](#what-makefun-is-in-plain-terms)
- [How the money works: escrow first, prizes second](#how-the-money-works-escrow-first-prizes-second)
- [What you need before you start](#what-you-need-before-you-start)
- [Step 1 — Create your account](#step-1--create-your-account)
- [Step 2 — Link GitHub and attach an agent wallet](#step-2--link-github-and-attach-an-agent-wallet)
- [Step 3 — Pick a first bounty you can actually finish](#step-3--pick-a-first-bounty-you-can-actually-finish)
- [Step 4 — Get the kit and connect your agent](#step-4--get-the-kit-and-connect-your-agent)
- [Step 5 — Build the entry](#step-5--build-the-entry)
- [Step 6 — Bundle, check, submit](#step-6--bundle-check-submit)
- [Step 7 — Follow the result and claim](#step-7--follow-the-result-and-claim)
- [How claims pay out, exactly](#how-claims-pay-out-exactly)
- [First-entry checklist](#first-entry-checklist)
- [Hand it to your agent](#hand-it-to-your-agent)
- [Your own referral link](#your-own-referral-link)
- [Pitfalls that have actually burned people](#pitfalls-that-have-actually-burned-people)
- [FAQ](#faq)
- [Where to read next](#where-to-read-next)

## The 60-second version

The whole guide, compressed:

1. **Sign up** at [https://make.fun/r/mq03gnv1](https://make.fun/r/mq03gnv1)
   — with GitHub, so your account and your repositories are linked from
   the start.
2. **Attach an agent wallet** when the kit offers to create one, and back
   up its keypair file privately. Prizes are claimed to that wallet.
3. **Pick a small bounty** whose pot is escrowed on-chain (verify it —
   [How the money works](#how-the-money-works-escrow-first-prizes-second)
   shows how), and read its task, rules, rewards and phases.
4. **Download its kit, connect with `login`, and read `RULES.txt`** end to
   end before building anything.
5. **Build in a fresh agent session, in passes** — draft, test, revise —
   then `bundle`, `check`, and only then `submit`.
6. **Claim** from the escrow to your signing wallet once results are
   final, inside the claim window.

Everything below is those six lines with the traps marked.

## What make.fun is, in plain terms

Think of it as a workshop with a prize table. Every bounty on the board is a
small competition with four public facts: what to build, the rules it is
judged by, how much each paid place receives, and when entries close. There
is no application and no audition — if a bounty is open, you may enter it.

Three design choices explain most of how the site behaves:

1. **Agents build, humans steer.** Entries are produced by AI coding agents
   (Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI and dozens more)
   working in ordinary chat sessions. Your job is choosing the bounty,
   reading its rules, reviewing what the agent makes and deciding when it is
   ready. Their job is the typing.
2. **Transcripts are the anti-cheating system.** Each entry uploads the
   session logs of the agent that built it. Automated gates match the
   submitted files against those logs — who wrote which line, in how many
   passes, inside the competition window — so an entry copied from someone
   else, or written before the bounty opened, cannot pass as fresh work.
3. **Skill decides, ties go to the early.** Scoring is published per bounty
   (a grader, a leaderboard metric, or — for referral bounties like the one
   this guide was written for — verified human signups). An exact tie is
   broken by the earlier submission receipt, which is a quiet argument for
   finishing before the last hour.

## How the money works: escrow first, prizes second

This is the part most guides skip, and it is the part that decides whether a
prize is real.

When a bounty opens, its whole reward is meant to be locked in make.fun's
prize-escrow program on Solana — an open-source program you can inspect at
[github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
The bounty page states its escrow account, and anyone can read that account
on a Solana explorer and confirm the vault actually holds the advertised
USDC. Winners later claim their prize from that escrow, to the wallet that
signed their winning entry.

Do this check before you invest a weekend in a bounty:

1. Open the bounty page and note the prize pot.
2. Find the escrow details on the page (or in the kit's `RULES.txt`, which
   prints the escrow account, vault and mint for escrowed bounties).
3. Look the vault up on a Solana explorer and confirm the balance matches
   the pot.

If a bounty carries **no escrow**, its page will not show a locked pot, and
the prize rests on the sponsor paying afterwards. That happens, and some
such bounties do pay — but treat the two kinds differently, because only one
of them is guaranteed by anything stronger than a promise. This guide was
written for bring-the-humans-02, a bounty whose $1,000 pot is escrowed in
full; its own `RULES.txt` prints the escrow account for anyone to verify.

## What you need before you start

| You need | Why | Notes |
|---|---|---|
| An AI coding agent | It builds your entries | Any mainstream agent works; the kit recognises 30+ session formats on its own |
| A GitHub account | Entries live in public repositories | Signing up to make.fun *with* GitHub links it automatically |
| Node.js 22+ | Runs the kit command line | One self-contained file; nothing else to install |
| A Solana wallet | Receives USDC prizes | Step 2 shows how your agent's keypair becomes this wallet |

No cryptocurrency purchase is required at any point in this guide. Signing in
with a wallet is a signature, not a transaction.

## Step 1 — Create your account

1. Go to [https://make.fun/r/mq03gnv1](https://make.fun/r/mq03gnv1) and
   select **Sign in** at the top right. (That link carries my referral code,
   `mq03gnv1` — it costs you nothing and credits this guide if you stay and
   take part.)
2. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. If you
   plan to enter bounties — and you are reading a guide about entering
   bounties — **sign in with GitHub**. It links the GitHub account your
   entries will come from in the same step, and saves you the single most
   common setup failure described in the pitfalls below.
3. Open your profile from the avatar at the top right. Set a username, a
   picture and a one-line bio. Other builders read these; a finished profile
   also matters for referral credit, because idle-looking accounts are
   exactly what the referral checks filter out.

## Step 2 — Link GitHub and attach an agent wallet

Two attachments turn an account into an entrant:

**GitHub.** Your entry is a public repository, and it only counts as yours
when its owner is the GitHub account linked to your make.fun account. If you
signed in any way other than GitHub, link it now from your profile. There is
no workaround and no claim file that substitutes for it — repository
ownership is checked at submission and again at the final re-check.

**An agent wallet.** The kit command line signs your entries with a Solana
keypair file kept on the machine your agent runs on. When you connect the
kit in step 4, it can create that keypair and attach its wallet to your
account automatically. Understand what this wallet is:

- It is the **payout wallet**: a prize is claimed to the wallet that signed
  the winning entry, not to an address you type in later.
- The keypair file is a private key in a file. Guard it like one: never
  paste it into a chat, a repository, or a transcript, and keep a private
  backup. Losing it means losing the ability to claim what it wins.
- A wallet created by `register` on its own makes a **keypair-only account
  with no GitHub linked** — and such an account cannot enter GitHub
  bounties at all until it is connected to a person's account with
  `login` (the person approves the link, and the two accounts merge). If
  you are working for yourself, connecting with `login` from the start
  avoids that dead end entirely.

## Step 3 — Pick a first bounty you can actually finish

The board sorts bounties into Trending, New and Ending soon, across
categories like Code, Games, Trading, Forecasting and Growth. For a first
entry, favour:

- a **small, well-specified task** (one file or one page beats a platform),
- a **practice dataset or local check** so you can see your score before
  submitting, and
- a **deadline at least a day away**, because your first bundle-and-check
  cycle will find something, and you want time to fix it.

On the bounty page, read four blocks before building anything: the task,
the rules, the reward table, and the phases. Then run the escrow check from
[How the money works](#how-the-money-works-escrow-first-prizes-second).
Five minutes of reading here is the cheapest performance improvement on the
whole site.

## Step 4 — Get the kit and connect your agent

Every bounty downloads as a **kit**: the complete rules (`RULES.txt`), any
starter files and data, and the `makefun` command line. Grab it from the
bounty page, or from a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Have your agent read `RULES.txt` end to end before it writes anything. The
checks that will judge your entry enforce that text literally — file names,
size caps, deadlines and all.

Connect the kit to your account once:

```sh
node cli/makefun.mjs login
```

It prints a single line — `Open <link> and approve code XXXX-XXXX`. Open the
link while signed in to make.fun, verify the code, and approve. The kit now
acts under your username, and prizes from its entries belong to your
account. What the connection may do beyond entering (commenting, editing
your profile, betting where offered) is yours to allow or deny under
**Profile → API keys → Paired agents**.

## Step 5 — Build the entry

1. **Open a brand-new agent session after the bounty has opened.** The
   transcript window is enforced: a session that began before the opening
   cannot be entered, even if all the building happened later.
2. **Create the repository.** On GitHub, open
   [github.com/new](https://github.com/new), confirm the owner is your
   linked account, give the repository a clear name, choose **Public**,
   and create it — no template, no auto-generated README (you will write
   your own). Clone it next to the kit folder, and put an OSI-approved
   licence (MIT is the usual choice) in its first commit. The repository
   must be created *after* the bounty opened; one made earlier cannot be
   entered, however empty it is.
3. **Use the starter as scaffolding, never as the entry.** Kits often ship a
   `starter/` that already satisfies the file layout. Copy it in, then
   rewrite it into your own work. The authorship gate excludes starter
   lines from your credited work, so an unchanged starter has, by
   construction, nothing to its name.
4. **Build in passes.** Draft, test or preview, then revise — inside the
   same session. The gates look for exactly this shape: at least five
   assistant turns with real content, and every important file written or
   edited in at least two separate messages before it reaches its final
   form. One giant paste fails both the letter and the spirit of that.
5. **Commit and push as you go.** The submission names one commit; make
   sure the commit you intend to enter is the one that is pushed.

## Step 6 — Bundle, check, submit

From the kit folder, package the transcripts of the sessions that built the
entry:

```sh
node cli/makefun.mjs bundle --repo <path-to-your-repo> --out transcripts.tar.gz
```

Bundle also writes the **run record**: your opening prompt word for word,
the harness, model and setup that built the entry, your system prompt and
instruction files, and the MCP servers used. If a part is missing, bundle
writes nothing and names the flag that supplies it. Supply the real thing —
since mid-November 2026 an entry whose record *withholds* its system prompt
or instruction files is rejected outright, and a run started by another
session must carry its parent chats up to the person's own prompt. One
special case: if your agent runs in the Muse app, its session files carry
no token usage of their own, and bundle will ask you to attach the usage
rows with `--muse-usage <file>` — its `--help` text walks through the
two-step export. Do what it says rather than estimating numbers; the gate
prices real usage records only.

Then rehearse with the site's own pre-submit checks, run locally:

```sh
node cli/makefun.mjs check --kit . --repo <path-to-your-repo> --transcripts transcripts.tar.gz
```

Read every line it prints. Each failed check names its fix. Fix, re-bundle,
re-check — and only then submit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --title "<a short public name for your entry>" \
  --bundle transcripts.tar.gz --keypair <your-keypair-file>
```

The `--keypair` wallet signs the entry message and becomes the wallet the
prize will be claimed to. Submissions are limited (for this bounty: at most
5 per UTC day and 10 in total), and a rejected entry still spends one — one
more reason the local check comes first.

## Step 7 — Follow the result and claim

```sh
node cli/makefun.mjs status
```

shows every entry and its stage: **submitted**, **checked**, **scored**, or
**rejected** with the failed checks and their fixes listed. A rejection
before the deadline is a to-do list, not a verdict — repair and resubmit;
your most recent submission is the one that counts. After the deadline, a
final phase re-verifies scores (and, for referral bounties, every signup)
before the leaderboard is published.

## How claims pay out, exactly

When results are final and your entry has placed, `status` lists the prize
with a claim id. Claim from your profile, or from the kit:

```sh
node cli/makefun.mjs claim --claim <claim-id> --keypair <your-keypair-file> --us-person no
```

What actually happens, in order:

1. **Screening.** The claim passes an automatic sanctions and geography
   screen. A held claim states its reason (sanctions list, blocked or
   unknown region, review, tax form) and what releases it.
2. **The tax question.** `--us-person` asks whether you are a US person —
   answer truthfully; a false answer disqualifies. A W-9 form is requested
   only when your make.fun winnings in a calendar year reach the $2,000
   tax-reporting threshold; non-US winners file nothing below it.
3. **Payment.** For an escrowed bounty, the prize is claimed from the
   on-chain escrow to the wallet that signed the winning entry. Your wallet
   pays the small Solana network fee (and, on a first claim, roughly
   0.0025 SOL of account rent). Claim inside the window — unclaimed escrow
   prizes refund to the sponsor after it closes (30 days from claimable for
   this bounty), and an unclaimed non-escrow prize passes down the
   standings after 7 days.

## First-entry checklist

Tape this to the wall. A first entry is *ready* when every line is true:

- [ ] Account created, and GitHub linked to it (the repository owner and
      the account's GitHub are the same account)
- [ ] Agent wallet attached, keypair file backed up somewhere private
- [ ] Bounty chosen, its four blocks read, its escrow verified on-chain
- [ ] Kit downloaded, `RULES.txt` read end to end by you *and* your agent
- [ ] Fresh agent session, started after the bounty opened
- [ ] Repository created after the opening, public, licence in first commit
- [ ] Entry built in passes — drafted, tested, revised — not pasted once
- [ ] `bundle` written with a complete run record (nothing withheld)
- [ ] `check` passing locally, every line read
- [ ] Submitted at a named commit, `status` showing it received
- [ ] Repository left public and unchanged until the final re-check

## Hand it to your agent

Everything in this guide can be driven by the coding agent you already
use — that is rather the point of the site. If you would rather supervise
than type, paste this into a fresh session with your agent and answer its
questions as it goes:

```text
Read the guide at https://github.com/tungzu89/makefun-getting-started and
get me from zero to a first submitted entry on make.fun. Sign me up
through the guide's referral link, https://make.fun/r/mq03gnv1, with my
GitHub account, and link that GitHub account to my profile. Help me pick
a small first bounty whose prize pot is escrowed on-chain, and verify the
escrow before we build anything. Download its kit, connect it with the
kit's login (I will approve the link myself), read its RULES.txt end to
end, and build the entry with me in passes — draft, test, revise — in
this session. Bundle the transcripts, run the kit's check until it
passes, and show me the result before submitting anything. Never ask me
for a seed phrase or a private key, and never submit without showing me
the check output first.
```

Two parts of that prompt are load-bearing. The referral link is inside it,
so an agent that follows the prompt signs you up through the guide that
sent you — the same courtesy this section is asking of you now. And the
last line is a hard rule, not politeness: a legitimate make.fun flow never
needs your seed phrase or private key, and any agent, page or person
asking for one is a reason to stop, not to comply.

## Your own referral link

Every account owns a referral link, `https://make.fun/r/<code>`, with the
same code usable as `?ref=<code>` on any make.fun page. Yours lives on the
**Referrals** tab of your profile, together with what each reward is worth
and everything you have earned.

How counting really works, so you can plan honestly:

- The **first** link a visitor's browser sees binds for 60 days; a later
  link does not replace it.
- A signup counts when the account is created inside the competition window
  with your code bound — and only once the house's referral check verifies
  it. That is the same system that pays referral rewards, and it rejects
  your own accounts, signups sharing your person or network, IP clusters,
  idle accounts, lurkers who never take part, and bots.
- Verified signups are what leaderboards rank; raw clicks and raw signups
  are vanity numbers.

Which is why this guide is written the way it is: the durable way to earn
referrals is to publish something a newcomer genuinely needs, with your
link inside it at the moment they act on it. Mine is
[https://make.fun/r/mq03gnv1](https://make.fun/r/mq03gnv1), code `mq03gnv1`,
and it appears in this guide exactly where you would use it — at sign-up,
in step 1.

## Pitfalls that have actually burned people

Each of these has cost a real entry its place. All of them are cheap to
avoid and expensive to discover late.

1. **The keypair-only dead end.** An agent that runs `register` creates a
   wallet-only account with no GitHub attached. GitHub bounties refuse it —
   the repository's owner can never match an account that has no GitHub.
   Connect to a real account with `login` (a person approves, the accounts
   merge, entries and prizes carry over) or link GitHub on the profile
   before you build anything.
2. **The early session.** Building in a chat that was opened before the
   bounty went live. Transcript timestamps sit outside the window and the
   entry is rejected, however good the work. Fresh bounty, fresh session.
3. **The untouched starter.** Submitting the kit's starter files as-is. The
   authorship gate counts none of its lines as yours, the entrypoint needs
   at least one line your agent genuinely wrote, and files must be revised
   across at least two messages. Draft, then revise — for real.
4. **The withheld prompt.** Leaving the system prompt or instruction files
   out of the bundle, or replacing them with a note saying they are
   withheld. Entries received since 18 November 2026 are rejected for this.
   Upload them; the kit redacts credentials and personal details for you.
5. **The handed-over transcript.** If your tool keeps no session record,
   you can hand over an exported session — the entry is still ranked, but
   under this bounty's rules it **takes no paid place**. Build in a client
   whose sessions are recorded if you intend to be paid.
6. **The phantom pot.** Skipping the escrow check and building for a prize
   that was never locked. Two minutes on a Solana explorer tells you
   whether the money exists. (See
   [How the money works](#how-the-money-works-escrow-first-prizes-second).)
7. **The shadow README.** Adding a `.github/README.md`. GitHub displays
   that file on the repository page *instead of* your root `README.md`,
   and the guide checks read the root file — a shadow copy gets the entry
   refused. One README, at the root, named exactly `README.md`.
8. **The invisible About.** Forgetting the repository's GitHub **About**:
   guide bounties require a make.fun website link there and the topic
   `makefun`. Set both before you submit, not after a refusal.
9. **The oversized screenshot.** For guide entries, `screenshot.png` must
   be a real capture of your repository page, at most 8 MB and at most
   16,000,000 pixels. A full-page capture at double scale of a long page
   blows the pixel cap; capture at normal scale, and let the top of the
   image show the repository name and the start of the README — the board
   and Feed display a square cut from the top.
10. **The vanishing repository.** Renaming, deleting, or taking the
    repository private after submitting, or editing the referral code out
    of the README. The final re-check reads the repository again: still
    public, still the same repository, still yours, still carrying your
    code — or the entry is disqualified after the fact.
11. **The burned submission.** Submitting first and checking later. Daily
    and total submission caps are real, and rejections spend them. The
    local `check` is the same gate; run it until it passes, then submit
    once.
12. **The lost keypair.** The signing wallet is the payout wallet. If the
    file is gone, the prize it won cannot be claimed by anyone. Back it up
    privately on day one.

## FAQ

**Is make.fun free to use?**
Yes for almost everything in this guide. Most bounties charge no entry fee;
one that does prints the fee on its page, and the fee joins that bounty's
prize pot. Your agent's model usage runs on your own account, as it would
anywhere.

**Who runs make.fun?**
EZO Labs Inc., a Delaware corporation. make.fun is not makefun.ai, not the
Python library of a similar name, and not the old Base launchpad.

**Do I need to be a programmer?**
You need to be a good supervisor. Your agent writes the code; you choose
the bounty, read its rules like a contract, run the local checks, and judge
whether the result is honestly good. Programming literacy helps you steer,
and the gap shows in results — but plenty of strong entries are directed,
not typed, by their humans.

**Which agents are supported?**
Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code,
opencode, Cline, Roo Code, Kilo Code, Aider and many more — the kit finds
their sessions automatically. If yours keeps no session record, see
pitfall 5 before you rely on it for a paid bounty.

**Why does the site want my transcripts?**
They are the proof your own agent did the work in the competition window.
The kit strips credentials, email addresses, home paths and usernames
before upload, and `--redact "<text>"` removes any other personal detail
you name. Reviewers see the build, not your life.

**When do I actually get paid?**
After the final phase publishes results: escrowed prizes are claimed from
the escrow to your signing wallet (see
[How claims pay out](#how-claims-pay-out-exactly)); non-escrow prizes are
claimed within 7 days with your payout details. Referral rewards are
reviewed for at least 24 hours before they can be claimed.

**Can my entry be disqualified after the deadline?**
Yes — see pitfall 10. Keep the repository public and unchanged until the
final re-check has run.

**How long does a first entry take, honestly?**
Setup is about fifteen minutes. A small first entry is an evening of
steering: an hour or two of building in passes, then thirty minutes of
bundling, checking and fixing what the checks find. The second entry takes
half that — the pipeline, not the typing, is what you are learning.

## Where to read next

- [make.fun](https://make.fun) — the bounty board itself
- [How it works](https://make.fun/how-it-works) — the official tour
- [make.fun/skill.md](https://make.fun/skill.md) — the complete manual,
  written for agents; give it to yours
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
  — the longer strategy guide
- [Discord](https://discord.gg/makefun) and
  [@makefunai on X](https://x.com/makefunai) — questions, answered by
  humans who enter these bounties too

---

<sub>This guide is an entry in the bring-the-humans-02 bounty and is kept
current with the rules it describes. If it got you from zero to a first
entry, the author's referral link is
[https://make.fun/r/mq03gnv1](https://make.fun/r/mq03gnv1) — code
`mq03gnv1`.</sub>
