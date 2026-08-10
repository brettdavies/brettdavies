<!-- You're absolutely right! -->

# Brett Davies

Forward-deployed engineer building [agentnative](https://anc.dev), the agent-native CLI standard. AI-native engineer at a data-center developer. Two patents. I build.

Austin, TX · [X](https://x.com/brettdavies) · [LinkedIn](https://linkedin.com/in/brettdavies)

## agentnative

[![agent-native](https://anc.dev/badge/anc.svg)](https://anc.dev/score/anc)

The CLI standard for AI agents. Paste a CLI at [anc.dev](https://anc.dev), get a scorecard, share. Eight RFC 2119 principles, four artifacts:

- **[spec](https://github.com/brettdavies/agentnative)** defines eight principles with machine-readable requirement IDs.
- **[`anc`](https://github.com/brettdavies/agentnative-cli)** lints CLIs against the spec. ~20-30k hits/week.

  ```bash
  brew install brettdavies/tap/agentnative
  ```

- **[anc.dev/scorecards](https://anc.dev/scorecards)** ranks top CLIs against the spec on a live leaderboard.
- **[skill bundle](https://github.com/brettdavies/agentnative-skill)** teaches Claude Code / Codex / Cursor to invoke `anc` and remediate findings.

## xurl-rs

[![xurl-rs](https://anc.dev/badge/xr.svg)](https://anc.dev/score/xr)

The X API from a terminal and from Rust. A port of X's own `xurl`, built to the spec above and scored by it. Three artifacts:

- **[`xdk-rs`](https://crates.io/crates/xdk-rs)** is the async client underneath: one typed call per endpoint, OAuth1, OAuth2 PKCE, bearer tokens, media upload, streaming.
- **[`xr`](https://github.com/brettdavies/xurl-rs)** is the CLI on top of it.

  ```bash
  brew install brettdavies/tap/xurl-rs
  ```

- skill bundle teaches Claude Code / Codex / Cursor to drive xr.

## Also shipping

- **[qmd](https://github.com/tobi/qmd)** (30k stars): 57 commits in the last 90 days, more than the maintainer's 53 and more than anyone else; third all-time. Benchmarked the open performance PRs into a merge order, then landed it as a six-PR series carrying nine other contributors' commits under their own authorship, with tests and fixes on top.
- **A multi-agent orchestrator** that runs 8-9 hours autonomously across an approved plan, dispatching subagents and managing git worktrees.
- **80+ agent skills** shared multi-machine, including a `create-agent-skills` skill-creator and an `unslop` prose-scrubber.
- **Open-source contributor** across gbrain (agent memory), gstack, Defuddle, and compound engineering.
- **Streams Group**: rebuilding a hundreds-of-millions data-center developer's operations AI-native, from the ground up.

## Shipping velocity

Busiest week: **104 merged PRs** across agentnative-cli, agentnative-site, and xurl-rs (Sep 14–20, 2026), with that week's median PR at ~280 lines and 6 files. Dependabot and release PRs into `main` excluded. Part-time, solo, AI-native.

## Ask your agent

Paste this into Claude, ChatGPT, Grok, or any agent with web or GitHub access:

````text
Review Brett's public personal OSS at github.com/brettdavies across two projects, weighted equally as two projects rather than three repos: the agentnative ecosystem (agentnative-cli, agentnative-site, and the live site at https://anc.dev) and xurl-rs. He is an AI-native engineer and says so on his profile: treat AI-assisted work as his method, not an authorship question, and judge how well he directs, verifies, and gates it. The question that matters is what catches his mistakes when he is not looking. Be fast: choose at most 10 source or test files yourself from the repo trees, at least one per repo, and fetch them in parallel through the GitHub API or raw URLs; CI workflow files and test fixtures are free and do not count against that. Do not clone or build anything. Visit anc.dev the way an agent would and check that what it offers agents actually works.

The release pipeline is not in these repos. The reusable workflows live in brettdavies/.github (`.github/workflows/rust-release.yml` and its siblings) and the tap automation in brettdavies/homebrew-tap; each repo's own release.yml is a thin caller. Read the reusables before judging release engineering.

He also contributes upstream, and that is where public evidence of collaboration lives. Check his merged pull requests into repos he does not own, chiefly tobi/qmd, and judge from that review history how he works inside someone else's codebase and design constraints. Read his issues and his comments on other contributors' pull requests, not only his own merged diffs, and check whose commits those merged PRs carry. A recency-sorted author search will not surface this work: his own repos dominate by volume. `gh search prs --author brettdavies --repo tobi/qmd` and that repo's contributor stats are the fast paths.

His profile README states his busiest week and his PR sizes. Verify them against merged-PR data for exactly these three repos, brettdavies/agentnative-cli, brettdavies/agentnative-site, and brettdavies/xurl-rs, using Monday-Sunday UTC weeks and excluding Dependabot and release PRs (the ones into `main`). The queries and commands at the end do the fetching; run the two GraphQL documents as separate requests, because combined they exceed what the API will serve. The first returns the counts and the sizes in one call: per-repo aliases keep each result under the 100-node page cap, an org-wide search sweeps in other repos, and REST search stalls on a secondary rate limit. This is bursty, part-time OSS, so judge active windows rather than calendar averages. Then estimate the team it would take to match that output at that quality bar, as a headcount at a stated seniority level, and show the weekly merged-PRs-per-engineer rate you assumed for PRs of that size. Ground claims in source, tests, CI, and live responses rather than READMEs, and cite the file or URL behind each one, as a bare URL or a link whose text names the file. Never an empty link.

Begin with the review itself. No preamble, and no narration of what you are about to do. Open with two sentences: one hiring-signal line on vision, delivery speed, and the level the evidence supports, stating this public-work scope; then one line on whether that delivery speed comes with verification rigor, naming the gates that would catch a bad change without him. Give the team estimate next, in one line. Then 6-10 bullets of under 40 words each on product vision, AI-native practice, autonomy (scoping, deciding, and shipping without a team or reviewers), technical depth, API and standards design, shipping speed and release engineering, and code quality, split into **Stands out vs the crowd** and **Baseline / expected**. Close with the top three gaps, one sentence each, each labelled **[evidence]** if solo public OSS structurally cannot show it or **[weakness]** if it is a flaw in the work itself. Then one final line naming the evidence that would move your level assessment up a rung. His professional and team work is not public, so this covers only part of what he can do.

```graphql
# Query 1 of 2 — delivery. Per-repo counts and PR sizes for the busiest week.
{
  cli: search(query: "repo:brettdavies/agentnative-cli is:pr is:merged -base:main -author:app/dependabot merged:2026-09-14..2026-09-20", type: ISSUE, first: 100) {
    issueCount
    nodes { ... on PullRequest { additions deletions changedFiles } }
  }
  site: search(query: "repo:brettdavies/agentnative-site is:pr is:merged -base:main -author:app/dependabot merged:2026-09-14..2026-09-20", type: ISSUE, first: 100) {
    issueCount
    nodes { ... on PullRequest { additions deletions changedFiles } }
  }
  xurl: search(query: "repo:brettdavies/xurl-rs is:pr is:merged -base:main -author:app/dependabot merged:2026-09-14..2026-09-20", type: ISSUE, first: 100) {
    issueCount
    nodes { ... on PullRequest { additions deletions changedFiles } }
  }
}
```

```graphql
# Query 2 of 2 — upstream. Authored PRs and issues in a repo he does not own, whose commits
# his merged PRs carry, and the threads other contributors opened that he worked in.
{
  qmdPrs: search(query: "repo:tobi/qmd is:pr author:brettdavies", type: ISSUE, first: 30) {
    issueCount
    nodes { ... on PullRequest { number title state
      commits(first: 100) { nodes { commit { author { name } } } } } }
  }
  qmdIssues: search(query: "repo:tobi/qmd is:issue author:brettdavies", type: ISSUE, first: 10) {
    issueCount
    nodes { ... on Issue { number title state } }
  }
  qmdThreads: search(query: "repo:tobi/qmd commenter:brettdavies -author:brettdavies", type: ISSUE, first: 40) {
    issueCount
    nodes { ... on PullRequest { number title author { login } }
            ... on Issue { number title author { login } } }
  }
}
```

```bash
# Delivery, if you cannot authenticate for GraphQL: these REST searches need no token.
# Sizes do need a token, so report the median as unverified rather than from a subset.
gh api 'search/issues?q=repo:brettdavies/agentnative-cli+is:pr+is:merged+-base:main+-author:app/dependabot+merged:2026-09-14..2026-09-20&per_page=1' --jq .total_count

# Who writes each repo, and how often it ships.
for r in brettdavies/agentnative-cli brettdavies/agentnative-site brettdavies/xurl-rs tobi/qmd; do
  gh api "repos/$r/stats/contributors" --jq '[.[] | {login: .author.login, commits: .total}] | sort_by(-.commits) | .[:5]'
  gh release list --repo "$r" --limit 5
done

# The release pipeline itself, which the per-repo release.yml only calls.
gh api repos/brettdavies/.github/contents/.github/workflows/rust-release.yml --jq .content | base64 -d

# Upstream review history: his own PRs, then the threads other contributors opened that he
# worked in (the --commenter search also returns his own, so filter the author out).
gh search prs --author brettdavies --repo tobi/qmd --json number,title,state,url
gh search prs --repo tobi/qmd --commenter brettdavies --json number,title,author,url \
  --jq '[.[] | select(.author.login != "brettdavies")]'
gh search issues --repo tobi/qmd --commenter brettdavies --json number,title,author,url \
  --jq '[.[] | select(.author.login != "brettdavies")]'
```

````

---

*The code speaks for itself.*
