# Satoshi Kawasaki

**Independent researcher and research software engineer focused on AI safety evaluation.** I build reproducible evaluations, proposed fixes, and verification tools that support decisions on research and critical software:

- **AI safety & evaluation benchmarks** — [UK AISI ControlArena `#899`](https://github.com/UKGovernmentBEIS/control-arena/pull/899#issuecomment-6142961607) · [`#907`](https://github.com/UKGovernmentBEIS/control-arena/issues/907#issuecomment-6207150903), [FACE-Eval `#1`](https://github.com/aryopg/FACE-Eval/issues/1), [Debate control schemes sensitivity note](https://manifund.org/projects/testing-failure-modes-of-debate-style-ai-control-schemes-tewkbpvy1s?tab=comments#5834dca6-2ea1-427d-aaba-9cc942d2b193), [Manifund `funding-bench` `#1`](https://github.com/manifund/funding-bench/pull/1)
- **Ethereum & ZK infrastructure** — [Optimism `#23334`](https://github.com/ethereum-optimism/optimism/pull/23334), [SP1 `#2950`](https://github.com/succinctlabs/sp1/issues/2950#issuecomment-6114284554), [Tycho `#1486`](https://github.com/propeller-heads/tycho/pull/1486#issuecomment-6090912403), [revm `#3833`](https://github.com/bluealloy/revm/pull/3833#issuecomment-6090083437)
- **Systems biology & scientific computing** — [Tellurium `#611`](https://github.com/sys-bio/tellurium/pull/611) · [`#612`](https://github.com/sys-bio/tellurium/pull/612), [Diffrax `#787`](https://github.com/patrick-kidger/diffrax/pull/787), [HiGHS `#3387`](https://github.com/ERGO-Code/HiGHS/issues/3387)
- **C++ / Rust / GPU systems** — [SGLang `#42850`](https://github.com/sgl-project/sglang/pull/42850#issuecomment-6068696152), [Kokkos `#9122`](https://github.com/kokkos/kokkos/pull/9122#issuecomment-6139445264), [LLVM `#214016`](https://github.com/llvm/llvm-project/pull/214016#issuecomment-6118429105)

Open to research grants, collaborations, and scoped engineering contracts. Corporate contracting is available through [MIKOTO Co., Ltd.](https://mikoto-style.co.jp/en/).

[Discuss a project](https://mikoto-style.co.jp/en/contact.php) · [Research and evidence](https://mikoto-style.co.jp/en/research/) · [Company GitHub](https://github.com/mikoto0320) · [ORCID](https://orcid.org/0009-0000-9146-6399)

## AI safety: selected reports and independent validation

These are reports and tests contributed to other authors' work, not PRs authored by me (status checked 2026-10-17).

- **[ControlArena: AI-control input-validator pilot](https://github.com/UKGovernmentBEIS/control-arena/pull/899#issuecomment-6142961607)** ([reproducibility package](https://github.com/akatsukiwork0320/control-arena-validator-pilot-repro)) — Offline audit of 24 stored backdoor inputs across 10 sampled problems in an AI-control evaluation benchmark. One conflicted with a stated constraint also violated by two recorded test inputs: an unresolved specification/data conflict, not a confirmed scoring error. The audit was offline and did not implement sandbox isolation or test live attacks or scorer integration. [The PR author responded with scope guidance; validator coverage and format policy remain maintainer decisions.](https://github.com/UKGovernmentBEIS/control-arena/pull/899#issuecomment-6214873863)
- **[ControlArena: `swe_django` side-test behavioral probe](https://github.com/UKGovernmentBEIS/control-arena/issues/907#issuecomment-6207150903)** ([reproducibility package](https://github.com/akatsukiwork0320/control-arena-907-swebench-probe)) — Local `pytest` probe of reconstructed `base`/`gold`/mutated Django functions for two reported inverted side-task tests (`15103` and `16661`), identifying an `or`-joined JSON/Python `\u0026` decoding tautology in `15103` that accepts both escaped and unescaped output, and documenting baseline vs. mutation behavior on `16661`. Did not run SWE-bench Docker containers, the full main-task suite, or ControlArena's evaluation pipeline. No upstream response as of 2026-10-17.
- **[FACE-Eval: Inspect scorer missing-reasoning report](https://github.com/aryopg/FACE-Eval/issues/1)** ([offline reproducer `.zip`](https://github.com/user-attachments/files/33580962/face_eval_inspect_repro.zip)) — Source-level probe exercising `eval/inspect/judge.py` (`5f764cbf`) in a standard-library AST-extracted harness with stubbed judge responses. With a valid cue-aligned answer, observed `vcr=0.0` and `uar=1.0` when reasoning is absent or its judge output fails JSON parsing. The no-trace VCR result conflicts with the README's documented `NaN` behavior; UAR and parse-failure eligibility remain questions for upstream. Did not run Inspect's full task orchestration, metric aggregation or live model calls, and has not demonstrated an effect on published paper results. No upstream response as of 2026-10-17.
- **[Debate control schemes: Phase 2 side-standardization sensitivity note](https://manifund.org/projects/testing-failure-modes-of-debate-style-ai-control-schemes-tewkbpvy1s?tab=comments#5834dca6-2ea1-427d-aaba-9cc942d2b193)** — Methods note on `jackmaiorino/selvarath-debate` (`34898fb`) separating the Phase 2 erratum's `+4.56 pp` world-standardized question-side weighting from the `+3.94 pp` `strict` unit-weighted realized schedule (which retains all scheduled slots and counts `INVALID` judgments as wrong), with fixed-sample outer bounds for a hypothetical mirrored target under a homogeneous polarity-interaction assumption (`[+2.06, +5.94] pp`, not a confidence interval or exact feasible range), plus a coarse envelope for bounded heterogeneous interactions (`|κ_u| ≤ K`). Conditional calculations on archived Phase 2 outputs, not newly collected experimental results or a claim that `+4.56 pp` is an arithmetic error. No upstream response as of 2026-10-17.

## Selected authored pull requests

### Ethereum infrastructure

**[Optimism (`op-reth`) #23334](https://github.com/ethereum-optimism/optimism/pull/23334)** (fixes [#22501](https://github.com/ethereum-optimism/optimism/issues/22501)) — Proposed a fix and regression tests for historical proofs returning current-state data after unwinds and subsequent appends. A maintainer independently reproduced the bug, stated that the fix looks correct in a [commented review](https://github.com/ethereum-optimism/optimism/pull/23334#pullrequestreview-5488507484), and opened [#23341](https://github.com/ethereum-optimism/optimism/pull/23341) for a separate store-repair subcommand; formal approval is still pending. Local validation passed 822 tests across 17 packages; repairing previously corrupted history is separate work.

### AI evaluation and funding benchmarks

**[Manifund `funding-bench` #1](https://github.com/manifund/funding-bench/pull/1)** — Built an offline diagnostic and unit tests comparing how proposal attribution and scoring windows affect a synthetic Timaeus prediction. Production scoring and data are unchanged; this demonstrates sensitivity to the assumptions, not an improvement in actual funding decisions or model rankings.

### Systems biology and scientific computing

**[Tellurium #611](https://github.com/sys-bio/tellurium/pull/611) · [#612](https://github.com/sys-bio/tellurium/pull/612)** (fixes [#604](https://github.com/sys-bio/tellurium/issues/604), [#603](https://github.com/sys-bio/tellurium/issues/603)) — Proposed Python fixes for SBML/SED-ML biochemical network simulation workflows: preventing order-dependent model initialization from resetting parameter changes and preventing repeated tasks from overwriting standalone simulation outputs. Regressions cover XML ordering, the reported pathway simulation, nested tasks, and both fixes applied together.

**[Diffrax #787](https://github.com/patrick-kidger/diffrax/pull/787)** (fixes [#707](https://github.com/patrick-kidger/diffrax/issues/707)) — Added construction-time checks for Brownian-path shapes to reject unsuitable static metadata before JIT tracing. Selected tests cover accepted NumPy integer dimensions and rejected array/tracer inputs; these are regression checks, not a complete statistical validation of the solvers.

<details>
<summary>Additional authored PRs: AI inference (open feature PRs, awaiting review)</summary>

- **[SGLang #43603](https://github.com/sgl-project/sglang/pull/43603)** — Public extension points for model-weight placement before cache allocation and CUDA Graph capture, with CPU tests and single-L4 comparisons.
- **[SGLang #43597](https://github.com/sgl-project/sglang/pull/43597)** — A public way to refuse unsupported online weight updates before mutation, with CPU tests and a live-server refusal check.

</details>

All seven PRs linked in this section are **open and not merged**, checked 2026-10-17. The linked PRs document implementation details and validation limits.

## Other selected reports and independent validation

These are reports and tests contributed to other authors' work, not PRs authored by me. Links point to the recorded contributions; HiGHS and SGLang status checked 2026-10-17.

- **[HiGHS: incorrect optimality result](https://github.com/ERGO-Code/HiGHS/issues/3387)** — Reported a small MIP with an exact optimum of 1 where the tested solver reported 0. A maintainer [confirmed the bug](https://github.com/ERGO-Code/HiGHS/issues/3387#issuecomment-6120063138), and the fix, [PR #3408](https://github.com/ERGO-Code/HiGHS/pull/3408), was merged into `latest` as [`c2ddc850`](https://github.com/ERGO-Code/HiGHS/commit/c2ddc850fc0594ea1afbae1eca3cb0b642f00537) on 2026-10-16. Following my [candidate-build comparison](https://github.com/ERGO-Code/HiGHS/pull/3408#issuecomment-6152858701), an agent-run comparison of the merged build and a reverted control reproduced the correction on the original and redundant-row examples. Exact checks confirmed optimal returned points for the presolve-off API and MPS baselines; this is validation of the reported examples, not general solver correctness.
- **[SGLang: speculative sampling kernel reduction](https://github.com/sgl-project/sglang/pull/42850#issuecomment-6068696152)** — Synthetic-kernel measurements on one RTX 3070 identified ~23 µs of extra reduction work at batch size 1 on common paths; the **PR author incorporated the proposed branch guard** ([response](https://github.com/sgl-project/sglang/pull/42850#issuecomment-6082827978), upstream PR open). Not an end-to-end serving benchmark.
- **[Kokkos: host-side C++ Event race reproduction](https://github.com/kokkos/kokkos/pull/9122#issuecomment-6139445264)** — Reproduced a host-side C++ `Serial` ThreadSanitizer data race on the portable `Experimental::Event` fallback across Clang and GCC, and diagnosed three Jenkins CI/NVCC build failures.
- **[LLVM: `ExtTSP` code-layout differential testing](https://github.com/llvm/llvm-project/pull/214016#issuecomment-6118429105)** — Differential tests across 2,001 synthetic CFGs and an 8-node exact-enumeration witness showing near-tie layout changes in `mergeChainPairs`; no generated-code runtime measurement.
- **[SP1: GPU worker failure propagation](https://github.com/succinctlabs/sp1/issues/2950#issuecomment-6114284554)** — On one L40S, reproduced allocation panics and a client waiting until a configured 15-minute limit. Tested an existing development-branch error-handling approach on a pinned `main` build; clients then received terminal errors. OOM prevention and foreign-exception aborts were not resolved.
- **[Tycho: delayed revert replay](https://github.com/propeller-heads/tycho/pull/1486#issuecomment-6090912403)** — Supplied three-stream staggered-lag tests, a remaining edge-case reproducer, and a candidate cache fix (**upstream PR merged**; that merge does not establish adoption of my candidate cache change).

<details>
<summary>Additional public reports and reviews</summary>

| Project | My contribution |
|---|---|
| [revm](https://github.com/bluealloy/revm/pull/3833#issuecomment-6090083437) | Nine-case library-level `SELFDESTRUCT` trace comparison. |
| [vLLM](https://github.com/vllm-project/vllm/issues/52620#issuecomment-6072169935) | Concurrent structured-output comparisons across model-runner configurations. |
| [cosign](https://github.com/sigstore/cosign/pull/5074#discussion_r4243484217) | A regression test for a caller-supplied signature verifier being bypassed. |
| [SPIRE](https://github.com/spiffe/spire/pull/7310#discussion_r4235626035) | A cached-SVID regression test after sequential registration updates. |

</details>

## Reusable research artifacts

[ControlArena validator pilot (`#755` / `#899`)](https://github.com/akatsukiwork0320/control-arena-validator-pilot-repro) · [ControlArena `#907` side-test probe](https://github.com/akatsukiwork0320/control-arena-907-swebench-probe) · [FACE-Eval `#1` Inspect scorer probe (`.zip` attached to the issue)](https://github.com/aryopg/FACE-Eval/issues/1) · [revm reproduction bundle](https://github.com/akatsukiwork0320/revm-selfdestruct-trace-repro) · [HiGHS exact checker](https://github.com/akatsukiwork0320/highs-analytic-center-repro) · [SGLang kernel measurements](https://github.com/akatsukiwork0320/sglang-speculative-sampling-repro) · [Uniswap v3 replay checker (synthetic demo)](https://github.com/akatsukiwork0320/c1-synthetic-review-demo)

AI tools assisted implementation, experiments, analysis, and writing. Linked reports record the tested inputs, environment, results, and limitations; upstream responses are distinguished from local checks.
