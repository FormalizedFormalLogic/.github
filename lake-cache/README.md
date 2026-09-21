# `lake-cache`

Composite actions for the shared FormalizedFormalLogic Lake build cache. Not a reusable workflow:
these steps have to interleave with the build in the same job.

The repository using them needs a `lake-cache.toml` at its root defining the `ffl` and
`ffl-upload` services, the `LAKE_CACHE_ENABLED` variable and the `LAKE_CACHE_KEY` secret. See
[Foundation's `contribute/cache.md`](https://github.com/FormalizedFormalLogic/Foundation/blob/master/contribute/cache.md).

```yaml
- uses: FormalizedFormalLogic/.github/lake-cache/restore@main
  with:
    enabled: ${{ vars.LAKE_CACHE_ENABLED }}
    skip-download: ${{ steps.cache-restore.outputs.cache-matched-key != '' }}

- run: lake build Foundation

- uses: FormalizedFormalLogic/.github/lake-cache/publish@main
  if: github.event_name == 'push' && github.ref == 'refs/heads/master'
  with:
    cache-key: ${{ secrets.LAKE_CACHE_KEY }}
    targets: Foundation
```

`vars` and `secrets` are not readable inside a composite action, so both are passed as inputs.
