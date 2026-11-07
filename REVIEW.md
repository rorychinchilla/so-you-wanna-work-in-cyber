# Quick-fix review: So You Wanna Work in Cyber

**Reviewed:** 7 November 2026, branch `review/quick-fixes`
**Line numbers** point to `main` at commit `9ba76b7`, before any edits.
**Scope:** a quick-fix pass so the repo is safe to link from a resume. The v2 rewrite is out of scope.

**How links were checked:** `markdown-link-check` ran from a sandbox whose network policy blocks most outside sites, so it returned 403 for nearly every link. Those 403s do not mean the links are dead. Each link was then opened in a real browser, and the final URL and HTTP status were recorded.

**Bottom line:** the guide is in good shape. It doesn't promise outcomes, and the advice about certs holds up. What needs fixing is mostly housekeeping: one dead news site, one 404, a personal email address, a truncated license, and four lines of markdown that render as accidental headings.

---

## Tier 1 · Fix now (about 15 minutes)

Items marked **[in patch]** are already made on this branch, uncommitted, waiting for your review.

| # | File:line | What's wrong | Suggested fix | Source |
|---|---|---|---|---|
| T1-1 | guide.md:43 | **Threatpost has stopped publishing.** The newest stories on its homepage are dated 31 Aug 2022. | Swap it for **The Record** (Recorded Future News), which is active and good for beginners. **[in patch]** | [threatpost.com](https://threatpost.com/), [therecord.media](https://therecord.media/) |
| T1-2 | guide.md:72 | **WCAPS link returns 404.** The current Praxis Groups page has no cyber or emerging-tech group. | Point it at the WCAPS homepage and shorten the label to "WCAPS" **[in patch]**, or remove it if it no longer fits a cyber list. | [wcaps.org/praxisgroups](https://www.wcaps.org/praxisgroups) |
| T1-3 | guide.md:221 | **Your personal Gmail address is published.** It's easy for spammers to harvest. | Removed the line. The LinkedIn link stays as the contact route. **[in patch]** | — |
| T1-4 | CODE_OF_CONDUCT.md:17 | **The same personal Gmail is the reporting contact.** | **Decided:** your company-domain address replaces the Gmail. **[in patch]** | — |
| T1-5 | git history | **Privacy scan results.** Your personal Gmail shows up in the author field of commits `bc3ce1c` and `2565a93`, and in the first version of `CODE_OF_CONDUCT.md` and the guide (`bc3ce1c`). **No** phone numbers, home address, API keys or tokens were found. History was **not** rewritten. | Removing the email from the current files doesn't remove it from history, and anyone who clones can still see it. It's been public since April 2025, so rewriting history gains little; that's your call. To stop it recurring: GitHub → Settings → Emails → turn on *Keep my email addresses private* and *Block command line pushes that expose my email*, then set git's `user.email` to your GitHub `noreply` address. | — |
| T1-6 | guide.md:13, 19, 175, 207 | **Broken markdown.** A `---` directly under a line of text makes that text a heading. GitHub currently shows 4 extra H2s, for example "Cybersecurity doesn't have to be your delulu…". | Added a blank line before each `---`. **[in patch]** Checked with a CommonMark parser afterwards: no stray headings. | Rendered on github.com |
| T1-7 | guide.md:212 vs 83 | **The bio contradicts itself.** "Broke into the industry **without a CS degree**" sits against "Had a degree in Computer Systems from CUNY". A careful reader will notice. | Changed to your wording: "…who broke in through a CUNY tech degree, certs and community, without insider connections." **[in patch]** | — |
| T1-8 | LICENSE | **License file is cut short with `...`.** GitHub can't detect it: the sidebar shows "License" with no license name. | Replaced with the full official CC BY-SA 4.0 text, from the SPDX license list. **[in patch]** | [CC BY-SA 4.0 legal code](https://creativecommons.org/licenses/by-sa/4.0/legalcode) |
| T1-9 | CODE_OF_CONDUCT.md:5, 13 | **Code of conduct is cut short with `...`.** | Kept your opening and standards, and adopted Contributor Covenant 2.1 by link for the full text. **[in patch]** | [Contributor Covenant 2.1](https://www.contributor-covenant.org/version/2/1/code_of_conduct/) |
| T1-10 | `gitignore` | **The filename is missing its leading dot**, so git ignores the file. | Renamed it to `.gitignore`. **[in patch]** | — |
| T1-11 | guide.md:75, 78 | **Tech By Choice and Natives in Tech wouldn't load.** Both gave "connection closed" twice from your browser. Natives in Tech's GitHub org still lists its domain. | **Confirmed unreachable** by you on 7 Nov. Tech By Choice removed; Natives in Tech now links its GitHub org. **[in patch]** | — |
| T1-12 | guide.md:161–165, 220 | **Reddit (×5) and LinkedIn couldn't be checked automatically** because they block bots. | Subreddits confirmed working by you on 7 Nov. | — |

---

## Tier 2 · Fix soon (stale but not wrong)

| # | File:line | What's wrong | Suggested fix | Source |
|---|---|---|---|---|
| T2-1 | guide.md:55 | **Security+ V8 (SY0-801) launches 17 Nov 2026.** Your link redirects to the V7 page. | Use `https://www.comptia.org/en-us/certifications/security/`. Optional one-liner: *"Heads-up: a new version (SY0-801) launches November 2026, so make sure your study materials match the exam version you book."* | [CompTIA Security+ V8](https://www.comptia.org/en-us/certifications/security/v8/) |
| T2-2 | guide.md:56 | Network+ link redirects. | `https://www.comptia.org/en-us/certifications/network/` | [CompTIA Network+](https://www.comptia.org/en-us/certifications/network/) |
| T2-3 | guide.md:33 | The Security Engineering page has moved to an archive path. The chapters are still free. | `https://www.cl.cam.ac.uk/archive/rja14/book.html` | [book page](https://www.cl.cam.ac.uk/archive/rja14/book.html) |
| T2-4 | guide.md:34 | The **OWASP Top 10:2025** is out. Also, OWASP describes the list as the "most critical" risks, not the "most common". | Link `https://owasp.org/Top10/`, which opens the 2025 edition. Suggested wording: "The reference list of the most critical web app security risks (2025 edition)". | [OWASP Top 10:2025](https://top10.owasp.org/2025/) |
| T2-5 | guide.md:35 | Cybersecurity Canon has moved from Ohio State to its own site (the old link redirects). | `https://cybercanon.org/` | [cybercanon.org](https://cybercanon.org/) |
| T2-6 | guide.md:46 | Bloomberg link redirects. | `https://www.bloomberg.com/technology/cybersecurity` | — |
| T2-7 | guide.md:141 | Malwarebytes blog has moved. | `https://www.malwarebytes.com/blog` | — |
| T2-8 | guide.md:134 | LeetCode link redirects. | `https://leetcode.com/problemset/` | — |
| T2-9 | guide.md:143 | **Daniel Miessler's career post dates from 2008**, last updated in 2019. | Keep it with a "(classic, 2019)" label, or replace it in v2. | Page title: "[2019 Update]" |
| T2-10 | guide.md:58 | **"Bookmark it, live by it" pulls against your own "Pick One, Not Ten".** The roadmap lists hundreds of certs. | *"Bookmark it to see how certs connect. It's a map, not a to-do list."* | — |
| T2-11 | guide.md:119, 124 | **"Not needed for GRC" is dated.** GRC engineering and automation (policy-as-code, evidence scripts) now use code routinely, and that's your own specialty. | Line 124: *"❌ Not needed to start: GRC, policy, training (scripting is a plus in GRC automation)"*. Soften line 119 the same way. | — |
| T2-12 | guide.md:214 | **Hiring managers will read this bio.** It mentions SOC and vulnerability management but not your current focus or your certs. | Add one line, for example: *"Today they work in corporate security engineering, focused on data governance and GRC automation (GCIH, Security+)."* | — |
| T2-13 | CONTRIBUTING.md:7–8 | It asks for "tests", but this docs repo has none. | *"Check that any links you add still work."* | — |

---

## Tier 3 · Save for v2

- **Table of contents.** The guide is 220 lines; a TOC under the intro helps skimmers. (Emoji in headings make anchor links ugly, so worth handling at the same time.)
- **Remove duplicates.** TryHackMe and OverTheWire each appear twice (lines 132–133 and 152–154). The coding key takeaways (line 119) repeat the TL;DR (lines 124–126).
- **Infosec Prep Discord (line 169) has no link.** Add an invite link.
- **Keep links fresh automatically.** A small GitHub Action (`lychee-action`) on a monthly schedule would catch dead links before a hiring manager does.
- **Paths by role** (SOC, GRC, AppSec, cloud) instead of one flat resource list.
- **Free / paid markers** on each resource, for readers on a budget.

---

## Checked, no change needed

- **Cert advice:** "Certs ≠ job guarantees", "Pick One, Not Ten" and "Certs aren't magic" are well framed. Nothing promises outcomes.
- **Gatekeeping:** none found. Line 64 ("…not straight-white-male-coded") was considered. It sits in a section written for underrepresented folks, and it's your voice, so it stays.
- **Images:** the badges have alt text, and there are no other images.
- **Heading order:** H1 → H2 → H3 is correct once T1-6 is fixed.
- **Links that work:** Krebs, CSO Online, Risky Biz, Wired, TL;DR Sec, AWS Cloud Practitioner, Paul Jerimy, Diversify Tech, WSC, Out in Tech, QTBIPOC Design, Tech Sisters, Diversability, Codecademy, Explainshell, TryHackMe, OverTheWire, Troy Hunt, PortSwigger, USD blog list (now a 2026 edition), Trail of Bits CTF guide (updated Nov 2024), Cybrary, HTB Academy.

## Resume line

> "Author, So You Wanna Work in Cyber, a public GitHub guide for people starting security careers."

**This is accurate.** An optional, slightly stronger version:
> "Author, *So You Wanna Work in Cyber* (2025), a public GitHub guide for people starting security careers, especially from non-traditional backgrounds."

## README note (drafted, in patch)

> _Last updated November 2026 · a refreshed version is in progress_
