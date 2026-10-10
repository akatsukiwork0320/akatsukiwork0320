# Satoshi Kawasaki

I work on reproducible correctness and performance studies for AI inference, numerical software, and stateful systems. My work focuses on explicit assumptions, controlled comparisons, and evidence that others can rerun.

## Authored pull requests

### SGLang — public weight-update refusal

[PR #43597](https://github.com/sgl-project/sglang/pull/43597) · **Open; awaiting review; not merged** (status checked 2026-10-11).

Adds a public way for models and plugins to refuse unsupported online weight updates, with checks across selected runners before mutation. Validation includes 31 CPU component tests and a live-server check with Qwen3-0.6B on one NVIDIA L4. Generation continued after each tested refusal; the PR documents untested configurations and AI assistance.

## Selected upstream reports and reviews

*Status checked on 2026-10-11. These entries describe my reports and review contributions, not PRs authored by me.*

### SGLang — speculative sampling

[Review and proposed patch](https://github.com/sgl-project/sglang/pull/42850#issuecomment-6068696152) · [Author's response](https://github.com/sgl-project/sglang/pull/42850#issuecomment-6082827978) · [Author's status update](https://github.com/sgl-project/sglang/pull/42850#issuecomment-6091422228)

Synthetic kernel measurements on one RTX 3070 identified about 23 µs of extra work at batch size 1 on the tested nonempty-residual and bonus paths. The PR author incorporated the proposed conditional reduction; the upstream PR remains unmerged. These measurements are not end-to-end serving benchmarks.

[Reproduction code, raw results, and comparison limits](https://github.com/akatsukiwork0320/sglang-speculative-sampling-repro)

### HiGHS — exact verification of a reported optimum

[Issue #3387](https://github.com/ERGO-Code/HiGHS/issues/3387)

An 11-variable reproducer and exact rational checks show a feasible objective of 1 and a matching upper bound, while the recorded HiGHS 1.15.1 run with presolve disabled reports Optimal 0. The report includes a runtime trace of the bound fixing. Upstream assessment is pending.

[Reproducer and exact checker](https://github.com/akatsukiwork0320/highs-analytic-center-repro)

### revm — SELFDESTRUCT trace validation

[Validation report on PR #3833](https://github.com/bluealloy/revm/pull/3833#issuecomment-6090083437)

A library-level comparison checks trace payloads, address-filter matches, and recorded state fields across nine cases. The probe supports the proposed trace fix on the tested cases; it does not run the Reth binary or replay a chain. The report awaits an upstream response.

[Probe, reference outputs, and checker](https://github.com/akatsukiwork0320/revm-selfdestruct-trace-repro)

## Research and reproducibility

[C1 synthetic review demo](https://github.com/akatsukiwork0320/c1-synthetic-review-demo) · [ORCID](https://orcid.org/0009-0000-9146-6399)

The linked studies use AI-assisted implementation and analysis, including agent-run experiments. Their reports record the methods, measurements, and limits of each check.
