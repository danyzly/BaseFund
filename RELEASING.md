# Releasing & Tagging Guide

Align each on-chain release (**v0–v10**) with Git history using **annotated Git tags**, and optionally publish **GitHub Releases** with links to deployments and build configs.

---

## Goals
- One **Git tag per version** (`v0…v10`).
- **Traceability**: repository state ↔ deployed contract.
- Optional **GitHub Releases** with deployment links.

## Prerequisites
- Write access to the repository.
- Local clone; `main` up-to-date.

---

## Tagging Strategy

> ✅ **Recommended**: tag the **historical commit** that introduced each version (more accurate than tagging `HEAD`).

```markdown

1. **Find the commit that added a version** (example for `v6`):
   
   git log --pretty=oneline -- deployments/v6

   # Copy the SHA of the commit that added v6 (repeat per version)

2. Create annotated tags (replace <sha_vX>):

git tag -a v0  <sha_v0>  -m "v0: Basic escrow"
git tag -a v1  <sha_v1>  -m "v1: Events & errors"
git tag -a v2  <sha_v2>  -m "v2: Roles & access"
git tag -a v3  <sha_v3>  -m "v3: Pause + reentrancy"
git tag -a v4  <sha_v4>  -m "v4: Gas optimizations"
git tag -a v5  <sha_v5>  -m "v5: ERC-20 contributions"
git tag -a v6  <sha_v6>  -m "v6: Fees & treasury"
git tag -a v7  <sha_v7>  -m "v7: Factory/Proxy"
git tag -a v8  <sha_v8>  -m "v8: Meta-transactions"
git tag -a v9  <sha_v9>  -m "v9: Security hardening"
git tag -a v10 <sha_v10> -m "v10: UX & security"

3. Push all tags:

git push origin --tags

```

---

## Release notes template

```markdown

### BaseFund vX — Release Notes
**Key change:** <short summary>

**Deployments**
- Sepolia: `deployments/vX/base-sepolia.json`
  (interactions: `deployments/vX/base-sepolia-interactions.json`)
- Mainnet: `deployments/vX/base-mainnet.json`
  (interactions: `deployments/vX/base-mainnet-interactions.json`)

**Build Configs**
- Sepolia: `build-config/vX.standard-json.sepolia.json`
- Mainnet: `build-config/vX.standard-json.mainnet.json`

```
