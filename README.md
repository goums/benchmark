# CI runner benchmark — goums fork

This public `goums/benchmark` fork prepares one bounded native Tenki GitHub
Actions runner sample alongside the free GitHub-hosted baseline.

## Provenance

- **Target:** [`goums/benchmark`](https://github.com/goums/benchmark), public
  repository ID `1450714132`; target `main` was
  `8aca953f40e3619a84efecc4578113ac1f1b86b4` when prepared.
- **Harness:** incorporates reviewed upstream
  [`ci-router/benchmark`](https://github.com/ci-router/benchmark) commit
  `71098db26f7ed6b6cc2c3e0275d80491399969c2`, preserving target ancestry.
- **Runs and results:** a fork result must link to a public run in
  `goums/benchmark`. Upstream and other-fork runs are historical measurements
  from those repositories, not this fork's results. The collector and publisher
  validate `GITHUB_REPOSITORY` and use that repository's `results` branch and
  canonical GitHub run URLs.
- **Private sibling:** `goums/benchmark-private` is outside this pilot.

## Status

**Prepared source, not executed.** No Tenki measurement, comparison, score or
ranking exists from this fork. Exactly two routes are enabled:

| Route | Label | Size | Image |
| --- | --- | --- | --- |
| `github-hosted-4vcpu` | `ubuntu-24.04` | 4 vCPU / 16 GB | Ubuntu 24.04 |
| `tenki-hosted-4vcpu` | `tenki-standard-medium-4c-8g` | 4 vCPU / 8 GB | Ubuntu 24.04 |

The Tenki label and advertised shape come from the reviewed upstream route.
Tenki has half the memory of the public GitHub baseline. All Depot, Boat and
Ubicloud routes remain disabled.

The owner confirms Tenki is installed on `goums/benchmark`. Installation and
repository admin access do not prove hosted-runner admission or size eligibility;
a normal native job establishes that. A PAT installations-list 403 does not
prove absence, and a sandbox API key does not prove hosted-runner access.
`transparentCache` and `stickyDisk` stay `null` (unknown); do not change account
settings to fill them in. A job fingerprint is required to interpret actual
CPU, OS and resources. Charges remain unknown. No subscription or plan purchase,
settings change, secret change or ruleset bypass is part of this source pilot.

## Run only with confirmed budget headroom

As of 2026-11-10, the $10 combined daily allocation is $4 external / $6 internal.
The Depot, Boat and Ubicloud attempts retain $1 each with charges unreconciled;
one additional $1 is reserved for this single Tenki native Node attempt. The
old refused internal attempt also retains its $1 hold within the internal share.
Holds are operational reservations, not observed invoices or refunds. Standing
owner authority covers this bounded attempt after source review and merge,
workflow activation, and completion of the current free GitHub baseline run.
No retry, fallback dispatch or subscription purchase is authorized.

After independent review and merge to this fork's `main`, and with confirmed
headroom, the intended single command is:

```sh
gh workflow run benchmark.yml \
  --repo goums/benchmark \
  --ref main \
  -f route=tenki-hosted-4vcpu \
  -f workload=node-typescript \
  -f repeats=1
```

This selects one explicit native paid route, one workload and one repetition.
The workflow uses a 15-minute job timeout, max parallelism one, a repository-wide
singleton concurrency group, no fallback and no automatic retry. A timeout does
not prove native teardown or enforce a hard billing cutoff. Retain uncertain
charges until terminal reconciliation. This source preparation dispatches no job.

The default manual dispatch remains the free GitHub baseline. The existing
six-hour cron is guarded to upstream `ci-router/benchmark` on `main`; fork
scheduled planning is skipped. `schedule.json` enrolls only the free baseline.
Enabling Tenki does not add a paid cron.

## Collection and checks

The existing fingerprint collector records CPU, resources, OS and kernel without
printing the environment. On `main`, collection appends immutable rows under
`results/<suite>/` and raw jobs-API data to this fork's `results` branch. Only the
GitHub baseline opts into raw log archiving; Tenki logs are not archived.
Unknown settings, price and absent samples remain unknown. External native
samples do not qualify an internal CI Router route or feed placement scores.

Suite `0.2.0` is unchanged: Node `22.23.4`, TypeScript commit
`1e4744d68260a7cb91b62b12edc3f6a2187faaf1`, Rust `1.98.0` and rust-analyzer
commit `b98172d80f0da12bbde3d6733c274e17cb6417aa`. All actions use full commit
SHA pins. Node 22 is required; there are no packages.

```sh
node --test bench/*.test.mjs
actionlint
```

The workflow has only manual and scheduled triggers, with no pull-request
trigger. Benchmark jobs have `permissions: {}` and no secrets. The GitHub-hosted
collector can write only on `main` and publishes only to `results`. See
[METHODOLOGY.md](METHODOLOGY.md) for sampling, scoring and publication limits.

## Licence

- Code, workflows, workload definitions and tests: [Apache License 2.0](LICENSE).
- Results and raw data on `results`: [CC-BY-4.0](LICENSE-RESULTS), attributed to
  "ci-router benchmark".
