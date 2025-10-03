# Releasing & Tagging Guide

This guide explains how to align on-chain releases (v0–v10) with Git history using annotated tags, and how to publish GitHub Releases.

## Goals

- One Git tag per on-chain version (v0–v10).
- Traceability from repository state → deployed contract.
- Optional GitHub Releases with links to deployments and build configs.

## Prerequisites

- Write access to the repository.
- Local clone with the main branch up-to-date.

## Tagging Strategy

```bash

1. Find the commit that introduced each version (example for v6):
   
git log --pretty=oneline -- deployments/v6
# Copy the SHA of the commit that added v6
   
2. Create an annotated tag per version:

git tag -a v0  <sha_v0>  -m "v0: Basic escrow"
git tag -a v1  <sha_v1>  -m "v1: Events & errors"
git tag -a v2  <sha_v2>  -m "v2: Roles & access"
git tag -a v3  <sha_v3>  -m "v3: Pause + reentrancy"
git tag -a v4  <sha_v4>  -m "v4: Gas optimizations"
git tag -a v5  <sha_v5>  -m "v5: ERC20 contributions"
git tag -a v6  <sha_v6>  -m "v6: Fees & treasury"
git tag -a v7  <sha_v7>  -m "v7: Factory/Proxy"
git tag -a v8  <sha_v8>  -m "v8: Meta-transactions"
git tag -a v9  <sha_v9>  -m "v9: Security hardening"
git tag -a v10 <sha_v10> -m "v10: UX & security"

3. Push all tags:

git push origin --tags

```
