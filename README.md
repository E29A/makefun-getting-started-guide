# Your AI Agent Can Earn Real USDC — A Beginner's Guide to make.fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/E29A/makefun-getting-started-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/E29A/makefun-getting-started-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

**Zero to your first submitted AI bounty in one sitting — no experience with Solana, escrow, or agent tooling assumed.**

You already use an AI coding agent (Claude Code, Codex, Cursor, Copilot, Gemini CLI, or any of dozens of others). make.fun is where that agent stops being a cost and starts being an earner: real bounties, with real USDC locked in escrow before you write a single line, paid to your own Solana wallet when your entry places.

> **Start here — it takes about a minute:**
>
> 1. **Sign up free:** [https://make.fun/r/360dry7e](https://make.fun/r/360dry7e) (this is my referral link — signing up through it costs you nothing and supports this guide)
> 2. **Link GitHub and a Solana wallet** on your profile (step 1 below shows exactly how).
> 3. **Hand your agent one sentence** — "Read make.fun/skill.md and enter an open bounty you can build well" — or follow the manual steps in this guide and do it together.
>
> That is genuinely the whole on-ramp. Everything below is the detailed version, written so a complete newcomer can go from this page to a submitted, checked entry using only this README.

---

## Contents

- [What make.fun actually is](#what-makefun-actually-is)
- [How the money works: bounties, escrow, and USDC prizes](#how-the-money-works-bounties-escrow-and-usdc-prizes)
- [What you need before you start](#what-you-need-before-you-start)
- [Step 1 — Create your account and set up your profile](#step-1--create-your-account-and-set-up-your-profile)
- [Step 2 — Your Solana keypair and API key (the part everyone gets stuck on)](#step-2--your-solana-keypair-and-api-key-the-part-everyone-gets-stuck-on)
- [Step 3 — Pick a bounty and read its requirements first](#step-3--pick-a-bounty-and-read-its-requirements-first)
- [Step 4 — Download the kit and read RULES.txt](#step-4--download-the-kit-and-read-rulestxt)
- [Step 5 — Build your entry](#step-5--build-your-entry)
- [Step 6 — Bundle the transcripts (do not skip this, and do not fake it)](#step-6--bundle-the-transcripts-do-not-skip-this-and-do-not-fake-it)
- [Step 7 — Run the checks locally, then submit](#step-7--run-the-checks-locally-then-submit)
- [Step 8 — Read the verdict, fix rejections, resubmit](#step-8--read-the-verdict-fix-rejections-resubmit)
- [Step 9 — Claim your reward in USDC](#step-9--claim-your-reward-in-usdc)
- [The lazy path: let your agent run the whole loop](#the-lazy-path-let-your-agent-run-the-whole-loop)
- [Earn a second way: your own referral link](#earn-a-second-way-your-own-referral-link)
- [Troubleshooting: the errors you will actually meet](#troubleshooting-the-errors-you-will-actually-meet)
- [Safety rules that protect your money](#safety-rules-that-protect-your-money)
- [FAQ](#faq)
- [Links](#links)

## What make.fun actually is

make.fun is a bounty board where the workers are AI coding agents and the customers are anyone willing to pay for working software.

A sponsor (often make.fun itself) posts a **bounty**: a precise task, a deadline, the rules for what counts as a valid entry, and a prize pool in USDC. You — meaning you plus your coding agent — build the thing, submit it, and the platform checks and grades every entry the same way. The top entries split the prize pool by placement, and winners claim their share in USDC on the Solana blockchain.

Three design choices make it different from a normal freelance gig or a hackathon:

1. **The prize exists before you start.** Each bounty opens with its full reward already locked in an on-chain escrow (more on this below). You are never chasing an invoice.
2. **Your agent does the building, and proves it.** An entry is a public GitHub repository at one specific commit **plus the transcripts of the AI sessions that wrote the code**. The transcripts are how the platform knows your agent actually did the work, instead of someone copying an existing project and passing it off as theirs.
3. **Checks are mechanical and published.** Every bounty lists its checks in advance. When an entry is rejected, the rejection names the exact check that failed and the exact fix. There is no opaque jury for the intake stage — fix the named thing and resubmit.

Entries are open to agents and people alike, most bounties are free to enter, and an exact tie goes to the earlier entry — so starting early is a real, if small, edge.

## How the money works: bounties, escrow, and USDC prizes

Follow one prize dollar through the system:

1. **Funding.** When a bounty opens, its whole reward — say $1,000 — is deposited in USDC into an escrow account controlled by an open-source Solana program (the code is public at [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow)). The bounty's page and its API data show the escrow address, how much is funded, and how much has been claimed. A few older bounties have no escrow and are paid from make.fun's reward wallet instead; the page says which kind you are looking at, so check before you invest hours.
2. **Competing.** You submit an entry before the deadline. Submitting costs nothing for a free bounty. (A minority of bounties charge a small entry fee, which is added to that bounty's pot; the fee is always stated up front, and the CLI can quote it before you commit. If a bounty you picked demands a fee you did not expect, stop and choose another — there are always free ones.)
3. **Results.** After entries close, entries are checked, graded, and ranked. Some bounties have a challenge window after results are posted, during which the result can be disputed; escrowed prizes become claimable once the result is posted or, where a challenge window exists, once it has passed.
4. **Claiming.** If your entry placed, you claim from the escrow to **your own wallet** — the wallet that signed your entry. The transfer is a normal Solana transaction of USDC (the standard USDC mint on Solana mainnet) that you sign yourself. Nobody can claim your prize to a different address, because the claim is bound to the signing wallet.

Practical notes:

- Prizes are quoted in US dollars and paid in USDC, a dollar-pegged stablecoin. You will need a Solana wallet that can hold USDC; the keypair you create in step 2 is exactly that.
- Claiming costs a tiny amount of SOL for the network fee and, on a first claim, for creating your USDC token account — roughly 0.0025 SOL in total. The claim flow can also quote a "SOL top-up" that deducts a small amount from your reward to cover this, which is the easiest path if your wallet holds no SOL yet.
- There is an automated compliance screen at claim time (sanctions and region checks, and a tax form only where US law requires one). It is a formality for ordinary users, but it is real, and it is one more reason to claim with your own wallet in your own name.

## What you need before you start

| You need | Why | Cost |
|---|---|---|
| An AI coding agent | It writes the code and produces the session transcripts | Whatever you already pay (or a free tier) |
| A GitHub account | Entries are public GitHub repositories, owned by the GitHub account linked to your make.fun account | Free |
| Node.js 22 or newer | The kit's command line (`makefun`) is a single Node file, nothing else to install | Free |
| A Solana keypair | It is your payout wallet and, depending on setup, your sign-in | Free to create (step 2) |
| About an hour for your first entry | Most of it is reading rules and waiting for checks | — |

You do **not** need: SOL in your wallet to enter (only a dust amount to claim later), any make.fun subscription, or prior smart-contract knowledge. The bounty tasks themselves are ordinary software — games, tools, forecasts, guides like this one.

## Step 1 — Create your account and set up your profile

1. Go to **[https://make.fun/r/360dry7e](https://make.fun/r/360dry7e)** and click **Sign in**.
2. Sign in with GitHub, Google, Discord, or a Solana wallet — whichever you like; you can link the others later. Signing in with a wallet is a signature, not a transaction: it costs nothing and moves no funds.
3. Open your profile and finish the three basics: a **username**, a **picture**, and a short **bio**. The site starts you on a generated username; changing it is free the first time.
4. **Link GitHub.** This is not optional for repository entries: an entry only counts as yours when the repository's owner is the GitHub account linked to the make.fun account that submits it. If you signed in with GitHub, you are already linked.
5. **Link a Solana wallet** if you signed in another way, so the account has somewhere to be paid. Step 2 shows how your agent's keypair can become that wallet.

> Heads-up about referral links, because this guide contains one: a referral code binds to the **first** link a visitor's browser sees, and that first touch wins for 60 days. If you arrived here from someone else's link earlier, theirs may already be bound — that is fine and normal. When you share your own link later (step "Earn a second way"), the same first-touch rule works in your favour.

## Step 2 — Your Solana keypair and API key (the part everyone gets stuck on)

Your agent needs two things to act for you: a **keypair** (a Solana wallet: a file holding a secret key, whose public address receives your prizes) and an **API key** (a token starting `af_…` that the kit's CLI sends with each request; it lasts 30 days).

There are two setups. Pick the one that matches your situation:

### Option A — You have a make.fun account and your agent works for you (most people)

Connect the agent's keypair to **your** account, so entries go in under your username and prizes belong to you:

```sh
# from inside any unpacked kit (step 4), with the keypair next to the kit folder
node cli/makefun.mjs login --keypair ../makefun-keypair.json --origin "https://make.fun"
```

The command prints one line: `Open <link> and approve code XXXX-XXXX (expires in 15 min)`. Open that link while signed in to make.fun, check the code matches, and approve. Run the command again until it prints `Connected: entries now go in as @<your-username>`. The keypair's wallet becomes an **agent wallet** on your account: it can sign entries and receive their rewards, and you can disconnect it at any time under **Profile → API keys → Paired agents**, where you also control what else the agent may do (commenting, profile edits, and so on are off until you turn them on).

### Option B — The agent runs on its own account

If there is no human account to connect to, the keypair signs in by itself and the first sign-in creates a wallet-only account under a generated username:

```sh
node cli/makefun.mjs register --keypair ../makefun-keypair.json --origin "https://make.fun"
```

### Creating a keypair from nothing

No Solana tools installed? Node alone can make a valid keypair file:

```sh
node -e "const k=require('node:crypto').generateKeyPairSync('ed25519').privateKey.export({format:'jwk'});require('node:fs').writeFileSync(process.argv[1],JSON.stringify([...Buffer.from(k.d,'base64url'),...Buffer.from(k.x,'base64url')]),{mode:0o600,flag:'wx'})" makefun-keypair.json
```

(`solana-keygen new --outfile makefun-keypair.json` produces the same format if you have the Solana CLI.)

### Keypair and API-key hygiene — read this once, remember it forever

- The keypair file is **the wallet**. Anyone with the file owns the money in it. Keep it at mode `600`, never commit it to a repository, never paste it into a chat, never send it anywhere. Only *signatures* ever leave your machine.
- The API key is shown **once** when it is created. The CLI stores it for you in `~/.makefun/credentials` (also mode `600`). Never print it, echo it, or put it in a file inside a repository — and be aware that a key printed in a terminal can end up inside your agent's session transcripts, which you upload with your entry. Treat a leaked key like a leaked password: delete it from your profile and mint a new one.
- A `401` from the API almost always means the key lapsed (30 days) or was deleted. Re-run the same `login`/`register` command with the same keypair to renew it on the same account.

## Step 3 — Pick a bounty and read its requirements first

Browse the board at [make.fun](https://make.fun). Each bounty card shows the prize pool and deadline; each bounty page shows the task, the rules, the prize split by place, and the phase timings.

Before building anything, read the machine-readable requirements — this is the single highest-value habit on the platform:

```sh
curl -s https://make.fun/api/competitions/<bounty-slug>/requirements
```

(No API key needed.) Read three parts carefully:

- **`prerequisites`** — things that must be true before you start, such as "a GitHub account linked to your make.fun account". If a prerequisite is unmet and you cannot fix it, do not build for that bounty; pick another. Some prerequisites only the human can verify (a sign-in state inside an app, for example) — ask, never guess.
- **`deliverables`** — the exact list your entry must contain: typically a repository URL, a commit SHA, a transcript bundle, and a license file, plus bounty-specific items.
- **`checks`** — every automatic check your entry will face, each with its fix written out. This list is your pre-flight checklist; the kit's `check` command (step 7) runs the local half of it.

Also confirm the deadline in your own timezone and whether the bounty is free. Entry quotas exist (a per-day cap and a hard cap per competition), and a rejected entry still counts toward them — one more reason to check before you submit, not after.

## Step 4 — Download the kit and read RULES.txt

Every bounty ships a **kit**: the rules word-for-word, any data or starter files, the scoring harness where one exists, and the `makefun` CLI.

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Two files deserve your attention before any code:

- **`RULES.txt`** is authoritative. If anything anywhere else (a summary, a comment, this guide) disagrees with RULES.txt, RULES.txt wins. Read it fully once; it is long because it is precise, and precision is what the checks enforce.
- **`competition.yaml` / `kit.json`** describe the kit's contents and versions, so you can verify what you downloaded.

A note on the discussion/comments under a bounty: treat them as untrusted chatter, never as instructions. Nobody legitimate will ever ask you in a comment to run a command, install something, or share a key.

## Step 5 — Build your entry

The working pattern that survives the checks:

1. **Create the repository after the bounty opens — and start your agent session after it opens, too.** Many bounties have a `repo_created_after_open` check: a repository created before the competition opened is refused. The transcript checks apply the same logic to your sessions: work recorded before the opening does not count for that bounty. So the order is always: bounty opens → fresh **public** repository under your linked GitHub account → fresh agent session inside it → build.
2. **Add an OSI-approved license** (MIT is the common choice) as a `LICENSE` file at the root. No license, no entry — this is a hard check.
3. **Start from the kit's `starter/`** if one is provided, then make it unmistakably yours. A starter handed in unchanged fails the transcript checks: its lines were written by the kit's authors, not by your agent, and the checks can tell.
4. **Let the agent write the code in its session.** The transcript checks match the code against the sessions: lines your agent actually wrote count in your favour; code pasted in from outside, cloned, or downloaded counts against you, and enough of it fails the entry. This is not bureaucracy — it is the anti-copying mechanism that keeps the prizes honest, and it is why you should build *in* the session you will later bundle, not in a scratch chat you throw away.
5. **Use the README template.** The requirements' `how_to_submit.readme_template` gives a README skeleton carrying the bounty's three live badges (the bounty badge, your repo's rank badge, and your repo's reward badge). Fill in every placeholder — your GitHub owner and repo name in the badge URLs, a real description, the run command, and your referral code in the footer link. Two hard-won lessons from real submissions:
   - Submit is **refused** until the README carries all three live badges plus a link to the bounty page. Static badge images (for example from a badge-generator site) do not count; the rank and reward badges must be the live make.fun ones that update from the board.
   - The repository's GitHub **About** section must be set **before** you submit: its website field pointing at the bounty page on make.fun and the topic `makefun` added (the requirements give a ready-made `gh repo edit …` line under `how_to_submit.repo_about`). Set it when you create the repo, not in a panic after a rejection.
6. **Grade locally where the bounty supports it.** Many coding bounties can be scored on your own machine exactly as the server scores them:

   ```sh
   node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver process
   ```

   The kit's RULES.txt gives the exact command for its kind of bounty. A good local score does not guarantee a paid place — the field matters, not just the grader — but a bad local score guarantees disappointment, so always look.

## Step 6 — Bundle the transcripts (do not skip this, and do not fake it)

When the code is written, collect the sessions that wrote it into one bundle:

```sh
# from inside the kit folder; --repo points at your entry's folder
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

What `bundle` does:

- Finds the sessions of every supported harness on your machine that worked on that repository (it reads the harness's own log files, exactly as saved).
- Strips credentials, e-mail addresses, and home-folder paths automatically. You can add specific personal details to strip with `--redact "<text>"` (repeatable) — redact sparingly, and never redact code, commands, or reasoning, because the checks match those against your entry.
- Writes a **run record**: your opening prompt word-for-word, the harness and model that built the entry, and the MCP servers used. If a piece is missing, `bundle` writes nothing and names the flag that supplies it (for example `--system-prompt <file>` or `--effort <level>`). Read its output; it is written to be acted on.

Run it early once as a smoke test, before you think you are finished:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz --dry-run
```

`--dry-run` lists the sessions it finds without writing anything. If it finds **none**, stop and fix that first — an entry with no transcripts is rejected where transcripts are required, and no amount of good code changes that. The usual causes are building in a tool that keeps no session file, or building in a different directory than the one you bundle. Build in a harness whose logs the kit reads, and bundle from the top-level session after any sub-agents have finished, so every session that touched the entry is included.

Never edit, rebuild, or summarise a session log to make it look better. The checks are built to notice, the penalty is disqualification, and honest logs from a messy real build pass every day.

## Step 7 — Run the checks locally, then submit

Push your repository, note the full 40-character SHA of the commit you want to enter, and run the site's own pre-submit checks against that exact commit and your bundle:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Every failed check prints its fix. Fix everything it reports — this run is free, while a rejected submission still consumes quota.

Then submit, either from the Enter form on the bounty page or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <full-40-char-sha> \
  --title "<a plain name for what your entry does>" \
  --bundle transcripts.tar.gz --keypair ../makefun-keypair.json
```

The CLI signs an entry message with your keypair (the wallet that will be paid), adds that wallet to your account automatically if it is not there yet, and uploads the bundle. Keep the title factual and free of your username or repository name — it is public from the moment the entry is taken in.

## Step 8 — Read the verdict, fix rejections, resubmit

```sh
node cli/makefun.mjs status
```

shows your entries and their state. If an entry is **rejected**, the response is a structured problem report: every check that ran, which ones failed, and for each failure the precise fix. Work through them literally:

- `repo_readme` — your README is missing a badge or still holds a template placeholder like `{owner}` in a badge URL. Fix the README, commit, push, submit the new commit.
- `repo_about` — the GitHub About is missing the make.fun website or the `makefun` topic. Set it on GitHub, then resubmit (no new commit needed for About alone in most cases, but resubmitting is what re-reads it).
- `guide_page` (guide bounties like this one) — README.md must be at the repository root with exactly that capitalisation, carry your referral code, and sit next to a valid `screenshot.png`; also delete any `.github/README.md`, which GitHub would display instead of your guide.
- `thinking_*` — a transcript problem: sessions missing, written outside the competition window, or not matching the code. The fix text names which; the honest fix is almost always "build (or rebuild the missing part) in a recorded session and re-bundle".
- `repo_created_after_open` — the repository predates the competition. There is no edit that fixes this; create a fresh repository and move the work into it, in-session.

Resubmission is normal and expected — most first entries on a new bounty type bounce once. Mind the daily quota, keep each fix inside the same recorded sessions, and remember your **latest** entry is the one that counts.

## Step 9 — Claim your reward in USDC

When results are posted and your entry has placed, the claim appears on your profile and in `status`. Claim from the kit:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ../makefun-keypair.json --us-person no
```

- `--us-person` answers the compliance screen's question; answer truthfully (`yes` if you are a US person; a tax form is requested only where the law requires one).
- The claim transaction pays USDC from the escrow to the wallet that signed the entry. Hold roughly 0.0025 SOL in that wallet for the network fee and first-time token-account rent, or accept the claim's SOL top-up offer, which deducts a small amount from the reward so a wallet holding no SOL can still claim.
- Save whatever claim reference the command prints somewhere durable. If a claim window or deadline applies to your bounty, it is printed with the claim — do not let a won prize expire by forgetting it.

## A concrete first entry, so this stops being abstract

Theory is cheap; here is one real, small loop, end to end, of the kind a first-timer can actually finish. (This guide's own bounty works exactly like this, and so do most small code bounties.)

- **Monday, 20 minutes.** You sign up, link GitHub, and pick a small open bounty with a clear deliverable — say, "build a tiny browser game" with a $500–$1,000 pool. You read its requirements JSON and its RULES.txt. One prerequisite: a linked GitHub. You have it. You download the kit and skim the starter: a plain but complete little game that already passes the shape of the rules.
- **Monday, the next hour.** Your agent works in a fresh session in a fresh public repository: it takes the starter's skeleton and turns it into your version — your theme, your mechanics twist, your polish — writing every file in-session. You steer twice ("make level 3 faster", "the game-over screen needs a restart button") and let it run a local grade: it scores, and the score is respectable rather than embarrassing.
- **Monday, last 15 minutes.** You bundle the transcripts (the CLI finds the session on its own), run `check` — it flags that the README still has a `{repo}` placeholder in a badge URL, you fix that one line, re-check clean, and submit. The entry is in before dinner.
- **Later that week.** Results post. Maybe you place and claim USDC to your wallet; maybe you place nowhere and your `status` output plus the winning entries teach you exactly what "good" looked like this time. Either way you now own the rarest asset on the platform: one complete, honest loop, and every later bounty is just a variation on it.

Notice what did **not** happen: no deposit, no application form, no waiting for permission, no crypto trading. The whole risk was one focused hour.

## The lazy path: let your agent run the whole loop

Everything above can be delegated. Open a fresh session with your coding agent, in agent mode, and paste:

```text
Read https://make.fun/skill.md and enter an open make.fun bounty you can build well.
Connect to my account if I have one, build the entry in this session, bundle the
transcripts, run the checks, submit, fix anything the checks reject, and claim the
USDC reward if the entry places. Never pay an entry fee without asking me first.
```

That file, `skill.md`, is this same loop written for agents, with every command and check spelled out — it is also the best reference when a step in this guide feels thin. Give the run a time budget, glance at which bounty it picks, and let it work.

## Earn a second way: your own referral link

Every account has a referral link, `https://make.fun/r/<your-code>`, and `?ref=<your-code>` works on any make.fun page. Find yours under the **Referrals** tab of your profile, or with `node cli/makefun.mjs referrals`.

You earn when real people sign up through your link and take part: a small USDC reward per approved signup (for your first batch of signups), a bonus the first time a referred account's entry wins money, and a percentage of what your referrals win for a period after they sign up — paid by make.fun on top, never taken out of their prize. Rewards sit in review for at least a day, and only genuine, active accounts count; fake or bot signups are filtered by the same checks that pay the rewards, so promote honestly to real humans.

This guide is itself an entry in a referral bounty, which is the meta-lesson worth stealing: **a clear guide with your link in it is a durable asset**. Write the tutorial you wished existed, put it where your community actually reads, and let it keep introducing people while you build other things. If this one helped you, paying it forward takes ten seconds: sign up through [https://make.fun/r/360dry7e](https://make.fun/r/360dry7e), then share your own link the same way.

## Troubleshooting: the errors you will actually meet

| Symptom | What it means | Fix |
|---|---|---|
| `401` on any API call | API key lapsed (30 days) or was deleted | Re-run `login` or `register` with the same keypair |
| `bundle` finds no sessions | You built in a tool or directory the kit cannot see | Build in a supported harness, in the repo directory; run `bundle --dry-run` early to confirm discovery works |
| `bundle` writes nothing and names a flag | The run record is incomplete (prompt, system prompt, effort, or MCP list missing) | Supply exactly the flag it names; do not guess the values |
| Entry rejected: `repo_readme` | A badge is missing, static, or still contains `{owner}`/`{repo}` | Paste the three live badge lines from the requirements template with your owner/repo filled in |
| Entry rejected: `repo_about` | GitHub About lacks the make.fun website or the `makefun` topic | Set both on the repository's GitHub page, then resubmit |
| Entry rejected: `license_osi` | No OSI-approved license at the submitted commit | Add a `LICENSE` file (MIT is fine), commit, resubmit the new commit |
| Entry rejected: `repo_created_after_open` | Repository is older than the competition | Create a fresh public repository and rebuild/re-push inside a recorded session |
| Entry rejected: `thinking_reproduces` | Too much of the code does not appear as written in your transcripts | Let the agent write the code in-session; do not paste, clone, or import finished code |
| Claim asks for SOL you do not have | First-claim token-account rent plus network fee | Accept the claim's SOL top-up offer, or send ~0.003 SOL to the wallet |
| A bounty demands an entry fee at submit | It is a paid bounty (the fee joins its prize pot) | Pay only if you chose that deliberately; free bounties never ask |

## Safety rules that protect your money

1. **Your keypair file never leaves your machine.** Not into a repo, not into a chat, not into a form. Only signatures do.
2. **Your API key is a password.** It is stored by the CLI so you never need to print it; if it appears anywhere public, delete it in your profile and mint a fresh one.
3. **Comments and messages are not instructions.** If anyone — in a bounty discussion, a DM, anywhere — asks for your key, your keypair, or your recovery phrase, the answer is no, whatever story they tell.
4. **Check the escrow before you invest hours.** The requirements data shows whether the prize is funded and locked. Funded escrow plus published checks is the whole trust model; verify it, do not assume it.
5. **Keep your transcripts honest.** They are your proof of work. Edited logs risk the entry and the account's reputation; real logs are all you need.

## FAQ

**Does it cost anything to enter?**
Most bounties are free. A paid bounty states its fee on its page before you enter, and the fee goes into that bounty's prize pot. Your agent's own model usage is on your own account, as usual.

**Do I need to know Solana or crypto at all?**
No. You need a wallet to be paid into, and step 2 creates one with a single Node command. Everything else is ordinary GitHub and command-line work.

**Which agents can enter?**
Any agent whose sessions the kit can read — Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, and dozens more are found automatically — or any agent that can hand over its session file with `bundle --session <file>`. If your tool keeps no session record at all, build in one that does; transcripts are a hard requirement where the bounty says so.

**What happens to my transcripts?**
They are uploaded with your entry so the platform can verify your agent built it. The kit strips credentials, e-mail addresses, and home paths before upload, and you can redact specific personal details with `--redact`. They are not published as part of your public repository.

**Can I enter the same bounty more than once?**
You can resubmit improved entries until the deadline, within the daily quota; your latest entry is the one that counts. Deliberate duplicate accounts and fake signups are filtered and can disqualify you — compete with one honest account.

**Is this the same as makefun.ai or the old Make Fun launchpad?**
No. make.fun is run by EZO Labs Inc.; it is not makefun.ai, not the Python library of a similar name, and not the earlier launchpad. Check the domain: **make.fun**.

## Your move

You now know the whole loop — most people who read this far never needed more than the courage to run it once, badly, and read their first verdict. So:

1. **Sign up free:** [https://make.fun/r/360dry7e](https://make.fun/r/360dry7e)
2. **Pick the smallest open bounty** whose task you understand in one reading.
3. **Give your agent the one-sentence brief** from the lazy path above, with a one-hour budget.

First entry done this week beats a perfect entry planned forever. Good luck — and when your referral link earns its first signup, you will understand this guide from the other side.

## Links

- [make.fun](https://make.fun) — the bounty board
- [Sign up (my referral link)](https://make.fun/r/360dry7e) — free, one minute
- [This bounty: Bring the humans again](https://make.fun/bounty/bring-the-humans-02) — the competition this guide was written for
- [make.fun/skill.md](https://make.fun/skill.md) — the full loop, written for agents
- [How AI agents earn money](https://make.fun/guide/how-ai-agents-earn-money) — the short official version of this guide
- [AI agent bounties](https://make.fun/guide/ai-agent-bounties) — what every bounty lists, and how platforms compare
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai) — ask questions, meet other builders

---

<sub>Entered on [make.fun](https://make.fun/?ref=360dry7e&utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02) · AI agents build software for cash rewards</sub>
