<!--
  SETUP
  1. Create a PUBLIC repo named exactly:  hberahma
     (the repo name must match your username or GitHub won't surface it)
  2. Drop this file in as README.md on the default branch.

  The three projects below are SAMPLES, written to show the tone and level
  of specificity that works. Swap them for your own — keep the shape.

  DESIGN RULES IN USE
  - No emojis.
  - One accent value only: mid-grey #555555. It reads on both GitHub light
    and dark themes. If you change it, change it everywhere at once.
  - Cards use transparent backgrounds so they don't paint a white
    rectangle into dark mode.
-->

```
██╗  ██╗ █████╗ ███╗   ███╗███████╗ █████╗
██║  ██║██╔══██╗████╗ ████║╚══███╔╝██╔══██╗
███████║███████║██╔████╔██║  ███╔╝ ███████║
██╔══██║██╔══██║██║╚██╔╝██║ ███╔╝  ██╔══██║
██║  ██║██║  ██║██║ ╚═╝ ██║███████╗██║  ██║
╚═╝  ╚═╝╚═╝  ╚═╝╚═╝     ╚═╝╚══════╝╚═╝  ╚═╝
██████╗ ███████╗██████╗  █████╗ ██╗  ██╗███╗   ███╗ █████╗
██╔══██╗██╔════╝██╔══██╗██╔══██╗██║  ██║████╗ ████║██╔══██╗
██████╔╝█████╗  ██████╔╝███████║███████║██╔████╔██║███████║
██╔══██╗██╔══╝  ██╔══██╗██╔══██║██╔══██║██║╚██╔╝██║██╔══██║
██████╔╝███████╗██║  ██║██║  ██║██║  ██║██║ ╚═╝ ██║██║  ██║
╚═════╝ ╚══════╝╚═╝  ╚═╝╚═╝  ╚═╝╚═╝  ╚═╝╚═╝     ╚═╝╚═╝  ╚═╝
```

**I build backend and systems infrastructure in Go and Rust, and I care about the algorithms underneath it.**

[![Website](https://img.shields.io/badge/website-hberahma.com-555555?style=flat-square)](https://hberahma.com)
[![LinkedIn](https://img.shields.io/badge/linkedin-hamza--berahma-555555?style=flat-square)](https://www.linkedin.com/in/hamza-berahma)
[![Email](https://img.shields.io/badge/email-hberahma%40acm.org-555555?style=flat-square)](mailto:hberahma@acm.org)

---

## About

Computer science undergraduate working at the seam between systems engineering
and theory. Most of what I build is infrastructure: schedulers, execution
engines, storage layers — the parts that have to be correct under load rather
than merely correct. I came to that through competitive programming, and I
still spend a good part of each week on algorithms for their own sake.

---

## Selected work

### [raftkv](https://github.com/hberahma/raftkv)

A replicated key-value store with a from-scratch Raft implementation.

- Leader election, log replication, and snapshotting written against the
  extended Raft paper rather than a library, so failure modes are debuggable
  end to end.
- Sustains 24k writes/sec across a five-node cluster with fsync on, and
  recovers a partitioned follower in under 400ms.
- The hard part was log compaction: snapshots have to be installable on a
  follower that is still serving reads, which means the state machine and the
  snapshot writer share a copy-on-write boundary.

`Go` · `gRPC` · `BoltDB` · `Docker`

### [queryd](https://github.com/hberahma/queryd)

An embeddable SQL query engine for columnar data.

- Vectorized execution over Arrow-format batches, with a rule-based optimizer
  handling predicate pushdown, projection pruning, and join reordering.
- Runs the TPC-H suite at scale factor 1 in 3.1s single-threaded, roughly
  four times faster than the row-at-a-time interpreter it replaced.
- The hard part was join reordering: cardinality estimates degrade fast on
  correlated predicates, so the optimizer falls back to a sampling estimator
  above a fixed join depth instead of trusting its own statistics.

`Rust` · `Arrow` · `Parquet`

### [portal](https://github.com/hberahma/portal)

A self-hosted deployment tool for single-machine services.

- Declarative service definitions compiled to OCI containers, with zero-downtime
  rollouts via connection draining and health-gated cutover.
- Deploys a typical service in 11s from commit to live, including image build,
  and rolls back automatically on a failed health check.
- The hard part was making rollback trustworthy: the previous release has to
  stay warm and addressable for the whole cutover window, which rules out the
  obvious stop-then-start approach.

`Go` · `Podman` · `SQLite` · `Caddy`

---

## Currently

| | |
|---|---|
| Building | A distributed job scheduler with predictive autoscaling |
| Learning | Rust ownership and lifetimes properly, not by pattern-matching |
| Reading  | Papers on adaptive large neighbourhood search |
| Open to  | Software engineering internships and research collaboration |

---

## Toolbox

**Languages**

![](https://img.shields.io/badge/Go-555555?style=flat-square&logo=go&logoColor=white)
![](https://img.shields.io/badge/Rust-555555?style=flat-square&logo=rust&logoColor=white)
![](https://img.shields.io/badge/Python-555555?style=flat-square&logo=python&logoColor=white)
![](https://img.shields.io/badge/C++-555555?style=flat-square&logo=cplusplus&logoColor=white)

**Data**

![](https://img.shields.io/badge/PostgreSQL-555555?style=flat-square&logo=postgresql&logoColor=white)
![](https://img.shields.io/badge/SQLite-555555?style=flat-square&logo=sqlite&logoColor=white)
![](https://img.shields.io/badge/Redis-555555?style=flat-square&logo=redis&logoColor=white)

**Infrastructure**

![](https://img.shields.io/badge/Linux-555555?style=flat-square&logo=linux&logoColor=white)
![](https://img.shields.io/badge/Docker-555555?style=flat-square&logo=docker&logoColor=white)
![](https://img.shields.io/badge/Kubernetes-555555?style=flat-square&logo=kubernetes&logoColor=white)
![](https://img.shields.io/badge/Git-555555?style=flat-square&logo=git&logoColor=white)

<!--
  Logo slugs come from simpleicons.org. Every badge is 555555 on purpose —
  don't let one turn blue. If a slug doesn't exist, drop &logo= entirely
  and the badge still renders fine.

  Want no images at all? Replace this whole section with plain text:

    **Languages** — Go, Rust, Python, C++
    **Data** — PostgreSQL, SQLite, Redis
    **Infrastructure** — Linux, Docker, Kubernetes, Git
-->

---

## Activity

<a href="https://github.com/hberahma">
  <img height="150" alt="GitHub statistics"
       src="https://github-readme-stats.vercel.app/api?username=hberahma&show_icons=true&hide_border=true&bg_color=00000000&title_color=555555&text_color=888888&icon_color=555555&hide_rank=true&cache_seconds=86400" />
</a>
<a href="https://github.com/hberahma">
  <img height="150" alt="Most used languages"
       src="https://github-readme-stats.vercel.app/api/top-langs/?username=hberahma&layout=compact&hide_border=true&bg_color=00000000&title_color=555555&text_color=888888&cache_seconds=86400" />
</a>

<!--
  HEADS UP ON THESE TWO CARDS.
  They come from a shared community instance that was manually paused in
  January 2026 and still hits Vercel free-tier rate limits at peak times.
  When it fails you get a broken image on your landing page, which is
  worse than having no card at all.

  Options, in order of effort:
    1. Delete this section. Nothing else depends on it.
    2. Fork anuraghazra/github-readme-stats, deploy to your own Vercel with
       a PAT, swap the hostname above. This is the reliable option.
    3. Keep the shared instance and accept occasional breakage.
       cache_seconds=86400 is already set, which helps a little.

  Note the language card measures bytes committed, not skill or time spent.
  One vendored dependency folder can make it lie loudly.
-->

---

## Elsewhere

- Writing — [hberahma.com/writing](https://hberahma.com/writing)
- Competitive programming — [codeforces.com/profile/hberahma](https://codeforces.com/profile/hberahma)
- Everything else — [hberahma.com](https://hberahma.com)

---

<sub>Best way to reach me is email. I read everything, and I answer anything
that isn't a recruiter template.</sub>

<!--
  ============================================================================
  OPTIONAL BLOCKS — paste any of these in above, or ignore them.
  All monochrome, all emoji-free.
  ============================================================================

  PINNED REPO CARDS (better than the stats card if your repos carry the story)
  ----------------------------------------------------------------------------
  <a href="https://github.com/hberahma/REPO">
    <img src="https://github-readme-stats.vercel.app/api/pin/?username=hberahma&repo=REPO&hide_border=true&bg_color=00000000&title_color=555555&text_color=888888&icon_color=555555" />
  </a>

  CONTRIBUTION GRAPH
  ----------------------------------------------------------------------------
  ![](https://github-readme-activity-graph.vercel.app/graph?username=hberahma&bg_color=00000000&color=888888&line=555555&point=555555&hide_border=true)

  A SMALLER, QUIETER NAME BANNER
  ----------------------------------------------------------------------------
  Swap the block letters at the top for this if they feel too loud:

   _  _   _   __  __ ____  _     ___ ___ ___    _   _  _ __  __   _
  | || | /_\ |  \/  |_  / /_\   | _ ) __| _ \  /_\ | || |  \/  | /_\
  | __ |/ _ \| |\/| |/ / / _ \  | _ \ _||   / / _ \| __ | |\/| |/ _ \
  |_||_/_/ \_\_|  |_/___/_/ \_\ |___/___|_|_\/_/ \_\_||_|_|  |_/_/ \_\

  Keep it in a fenced code block with NO language tag — a tag turns on
  syntax highlighting and sprays colour across your name.

  ============================================================================
  LEFT OUT ON PURPOSE
  ----------------------------------------------------------------------------
  - Trophy and streak widgets. Stacking widgets from three different
    projects is the fastest way to make a profile look noisy.
  - Animated typing SVGs and wave banners. Load time spent on decoration.
  - A visitor counter. It measures nothing anyone else cares about.
  - GPA, awards, coursework. Resume material. Treating the profile README
    as a resume dump is the most common failure mode there is.
  - A list of every technology ever touched. Four languages you can defend
    in an interview beats twenty you can't.
  ============================================================================
-->
