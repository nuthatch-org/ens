# ens

A [nuthatch](https://github.com/nuthatch-org/nuthatch) nest: **ENS Registry on Ethereum**.

The ownership graph: owners, resolvers and TTLs.

One binary, one config file, no graph-node, no gateway, no query fees.

## What it indexes

**Chain:** `mainnet`. **1 contract**, **5 tables**.

| alias | address |
|---|---|
| `c0` | `0x00000000000c2e074ec69a0dfb2997ba6c7d2e1e` |

## Verified

Indexed blocks **25,791,620 to 25,811,556** and sealed **4,635 events**. Every table below is generated from the vendored ABIs, and the run above is what this nest actually decoded, not an estimate.

## Read this before trusting it

- Registry only. Resolvers and text records are a separate surface and are **not** covered.

## Run it

```sh
nuthatch init --from https://github.com/nuthatch-org/ens
cd ens
nuthatch dev --dir . --backfill 50000 --seal-direct
nuthatch sql --dir . "SELECT count(*) FROM \"c0__approval_for_all\""
```

The endpoint in `nuthatch.toml` is keyless and public, so this file is publishable: a `nuthatch.toml` is pinned into the nest's content address and must never carry a credential. It is enough to follow the tip. A **backfill** wants archive depth it may not have: pass your own with `--rpc`, and check it first with `nuthatch doctor --rpc <url>`.

## Tables

```
c0__approval_for_all
c0__new_owner
c0__new_resolver
c0__new_t_t_l
c0__transfer
```
