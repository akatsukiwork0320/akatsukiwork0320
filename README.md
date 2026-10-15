# Satoshi Kawasaki

**Independent researcher and research software engineer.** I build reproducible evaluations, proposed fixes, and verification tools for Ethereum and ZK infrastructure, AI and funding benchmarks, and scientific computing.

Open to research grants, collaborations, and scoped engineering contracts. Corporate contracting is available through [MIKOTO Co., Ltd.](https://mikoto-style.co.jp/en/).

[Discuss a project](https://mikoto-style.co.jp/en/contact.php) · [Research and evidence](https://mikoto-style.co.jp/en/research/) · [Company GitHub](https://github.com/mikoto0320) · [ORCID](https://orcid.org/0009-0000-9146-6399)

## Selected authored pull requests

### Ethereum infrastructure

**[Optimism (`op-reth`) #23334](https://github.com/ethereum-optimism/optimism/pull/23334)** (fixes [#22501](https://github.com/ethereum-optimism/optimism/issues/22501)) — Proposed a fix and regression tests for historical proofs returning current-state data after unwinds and subsequent appends. A maintainer independently reproduced the bug, stated that the fix looks correct in a [commented review](https://github.com/ethereum-optimism/optimism/pull/23334#pullrequestreview-5488507484), and opened [#23341](https://github.com/ethereum-optimism/optimism/pull/23341) for a separate store-repair subcommand; formal approval is still pending. Local validation passed 822 tests across 17 packages; repairing previously corrupted history is separate work.

### Evaluation and funding benchmarks

**[Manifund `funding-bench` #1](https://github.com/manifund/funding-bench/pull/1)** — Built an offline diagnostic and unit tests comparing how proposal attribution and scoring windows affect a synthetic Timaeus prediction. Production scoring and data are unchanged; this demonstrates sensitivity to the assumptions, not an improvement in actual funding decisions or model rankings.

### Scientific computing

**[Tellurium #611](https://github.com/sys-bio/tellurium/pull/611) · [#612](https://github.com/sys-bio/tellurium/pull/612)** (fixes [#604](https://github.com/sys-bio/tellurium/issues/604), [#603](https://github.com/sys-bio/tellurium/issues/603)) — Proposed fixes for order-dependent SED-ML model initialization and repeated tasks overwriting standalone simulation outputs. Regressions cover XML ordering, the reported simulation, nested tasks, and both fixes applied together.

**[Diffrax #787](https://github.com/patrick-kidger/diffrax/pull/787)** (fixes [#707](https://github.com/patrick-kidger/diffrax/issues/707)) — Added construction-time checks for Brownian-path shapes to reject unsuitable static metadata before JIT tracing. Selected tests cover accepted NumPy integer dimensions and rejected array/tracer inputs; these are regression checks, not a complete statistical validation of the solvers.

<details>
<summary>Additional authored PRs: AI inference (open feature PRs, awaiting review)</summary>

- **[SGLang #43603](https://github.com/sgl-project/sglang/pull/43603)** — Public extension points for model-weight placement before cache allocation and CUDA Graph capture, with CPU tests and single-L4 comparisons.
- **[SGLang #43597](https://github.com/sgl-project/sglang/pull/43597)** — A public way to refuse unsupported online weight updates before mutation, with CPU tests and a live-server refusal check.

</details>

All seven PRs linked in this section are **open and not merged**, checked 2026-10-16. The linked PRs document implementation details and validation limits.

## Selected reports and independent validation

These are reports and tests contributed to other authors' work, not PRs authored by me (checked 2026-10-16).

- **[HiGHS: incorrect optimality result](https://github.com/ERGO-Code/HiGHS/issues/3387)** — Reported a small MIP with an exact optimum of 1 where the tested solver reported 0. A maintainer confirmed the bug on `latest` and opened [PR #3408](https://github.com/ERGO-Code/HiGHS/pull/3408) (open); my [source-build comparison](https://github.com/ERGO-Code/HiGHS/pull/3408#issuecomment-6152858701) verified the proposed fix on the original and redundant-row examples. Exact feasibility checks of returned solutions covered the original reproducer cases.
- **[ControlArena: input-validator pilot](https://github.com/UKGovernmentBEIS/control-arena/pull/899#issuecomment-6142961607)** — Audited 24 stored backdoor inputs across 10 sampled problems. One conflicted with a stated constraint also violated by two recorded test inputs: an unresolved specification/data conflict, not a confirmed scoring error. The audit was offline and did not test live attacks or scorer integration.
- **[SGLang: speculative sampling kernel reduction](https://github.com/sgl-project/sglang/pull/42850#issuecomment-6068696152)** — Synthetic-kernel measurements on one RTX 3070 identified ~23 µs of extra reduction work at batch size 1 on common paths; the **PR author incorporated the proposed branch guard** ([response](https://github.com/sgl-project/sglang/pull/42850#issuecomment-6082827978), upstream PR open). Not an end-to-end serving benchmark.
- **[SP1: GPU worker failure propagation](https://github.com/succinctlabs/sp1/issues/2950#issuecomment-6114284554)** — On one L40S, reproduced allocation panics and a client waiting until a configured 15-minute limit. Tested an existing development-branch error-handling approach on a pinned `main` build; clients then received terminal errors. OOM prevention and foreign-exception aborts were not resolved.
- **[Tycho: delayed revert replay](https://github.com/propeller-heads/tycho/pull/1486#issuecomment-6090912403)** — Supplied three-stream staggered-lag tests, a remaining edge-case reproducer, and a candidate cache fix (**upstream PR merged**; that merge does not establish adoption of my candidate cache change).

<details>
<summary>Additional public reports and reviews</summary>

| Project | My contribution |
|---|---|
| [LLVM](https://github.com/llvm/llvm-project/pull/214016#issuecomment-6118429105) | Differential tests and an exact-enumeration witness for near-tie layout selection; no generated-code runtime measurement. |
| [Kokkos](https://github.com/kokkos/kokkos/pull/9122#issuecomment-6139445264) | ThreadSanitizer race reproduction and CI build-failure diagnosis. |
| [revm](https://github.com/bluealloy/revm/pull/3833#issuecomment-6090083437) | Nine-case library-level `SELFDESTRUCT` trace comparison. |
| [vLLM](https://github.com/vllm-project/vllm/issues/52620#issuecomment-6072169935) | Concurrent structured-output comparisons across model-runner configurations. |
| [cosign](https://github.com/sigstore/cosign/pull/5074#discussion_r4243484217) | A regression test for a caller-supplied signature verifier being bypassed. |
| [SPIRE](https://github.com/spiffe/spire/pull/7310#discussion_r4235626035) | A cached-SVID regression test after sequential registration updates. |

</details>

## Reusable research artifacts

**[C1: synthetic Uniswap v3 replay-checking demo](https://github.com/akatsukiwork0320/c1-synthetic-review-demo)** — Four fixed, offline fixtures demonstrate exact state checks and separate outcomes for unconfirmed coverage and malformed inputs. This is a synthetic demonstration, not validation of a deployed pool or live-chain data.

[HiGHS exact checker](https://github.com/akatsukiwork0320/highs-analytic-center-repro) · [revm reproduction bundle](https://github.com/akatsukiwork0320/revm-selfdestruct-trace-repro) · [SGLang kernel measurements](https://github.com/akatsukiwork0320/sglang-speculative-sampling-repro)

AI tools assisted implementation, experiments, analysis, and writing. Linked reports record the tested inputs, environment, results, and limitations; upstream responses are distinguished from local checks.
