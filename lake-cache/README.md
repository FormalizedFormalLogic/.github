# `lake-cache`

Composite actions for the Lake build cache shared across FormalizedFormalLogic repositories, so a
CI run and a fresh clone do not have to elaborate a whole library. Mathlib is a separate cache:
`lake exe cache get`, as always.

Not reusable workflows — these steps have to interleave with the build in the same job.

Lake puts `<owner>/<repo>` in the object key, so repositories share one bucket without colliding.
Adding one needs no Cloudflare work.

## Using it from another repository

**1. `lake-cache.toml` at the repository root.** Copy verbatim; it names no repository. No
`cache.defaultService` on purpose — that would also redirect dependency downloads, which must
keep going to Reservoir.

```toml
# Anonymous reads, via the bucket's custom domain.
[[cache.service]]
name = "ffl"
kind = "s3"
artifactEndpoint = "https://ffl.sno2wman.net/artifacts"
revisionEndpoint = "https://ffl.sno2wman.net/revisions"

# Authenticated writes, via the S3 API. CI only; the credential is the LAKE_CACHE_KEY secret.
[[cache.service]]
name = "ffl-upload"
kind = "s3"
artifactEndpoint = "https://411f2fda06461f8aa09a9055685d6fd9.r2.cloudflarestorage.com/ffl-lake-cache/artifacts"
revisionEndpoint = "https://411f2fda06461f8aa09a9055685d6fd9.r2.cloudflarestorage.com/ffl-lake-cache/revisions"
```

**2. `platformIndependent = true` in `lakefile.toml`,** if it is a pure Lean package. Without it
the scope carries `x86_64-unknown-linux-gnu` and non-Linux contributors always miss.

**3. The two steps.** `secrets` are not readable inside a composite action, so the key is passed as
an input. `fetch-depth` is required: the restore walks back from HEAD to a published revision, and
a merge commit is never one.

```yaml
- uses: actions/checkout@v5
  with:
    fetch-depth: 100

- uses: FormalizedFormalLogic/.github/lake-cache/restore@main

- run: lake build MyLib

- uses: FormalizedFormalLogic/.github/lake-cache/publish@main
  if: github.event_name == 'push' && github.ref == 'refs/heads/main'
  with:
    cache-key: ${{ secrets.LAKE_CACHE_KEY }}
    targets: MyLib
```

`restore` also takes `skip-download` (pass `true` when another cache already restored the build),
`repo`, `config`, `max-revs` and `assert-fresh`. Leave `assert-fresh` empty unless the library
imports all of Mathlib; otherwise it fails on modules the library never uses.

**A dependency's outputs** — what a repository built on Foundation wants, so that a pin bump costs
a download rather than an hour of elaboration — need `package` as well as `repo`: `repo` alone
looks the root package up under someone else's name. The revision read is the one the manifest
pins, not this repository's HEAD, so `fetch-depth` does not apply to it. Restore each package with
its own step; the second one does not undo the first.

```yaml
- uses: FormalizedFormalLogic/.github/lake-cache/restore@main
  with:
    repo: FormalizedFormalLogic/Foundation
    package: Foundation
    assert-fresh: ''
```

**4. The secret.**

| Name | Kind | Value |
|---|---|---|
| `LAKE_CACHE_KEY` | secret | `<ACCESS_KEY_ID>:<SECRET_ACCESS_KEY>` of an R2 API token. Publishing is skipped without it; reads are anonymous and need nothing |

There is no off switch: writing the steps is what asks for the cache, so dropping them is how a
repository stops using it.

The token must be an **Account API token** with **Object Read & Write** scoped to
`ffl-lake-cache` alone — the `Admin` tiers cannot be bucket-scoped and would reach unrelated
buckets in that Cloudflare account. Issue one per repository so revocation is independent.

## Locally

```shell
lake exe cache get
LAKE_CONFIG=lake-cache.toml lake cache get --service ffl --repo <owner>/<repo> --max-revs=100
LAKE_CONFIG=lake-cache.toml lake cache get --service ffl --repo FormalizedFormalLogic/Foundation \
  --package Foundation --max-revs=100
```

A miss is not an error; the build compiles from source.
