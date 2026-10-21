# SPMD IR

**SPMD IR** is an MLIR dialect and toolchain that captures the semantics of
SPMD (single-program, multiple-data) parallel programs in one intermediate
representation, independent of the programming model they are written in.
It starts from the application's own C/C++ source code: programs using MPI,
OpenSHMEM, NVSHMEM, NCCL, CUDA or OpenMP are raised into the SPMD IR
dialect, where analyses and transformations run on them independently of the
original programming model:

- **Raising & Lowering** — raising C/C++ applications to MLIR and from there
  into SPMD IR, and lowering them back to an executable, optionally targeting
  a different programming model than the one they were written in
  (experimental).
- **Correctness checking** — static detection of data races,
  collective-communication mismatches and thread-safety violations.
- **Performance optimization** — e.g. removing dead or redundant
  communication and coalescing communication operations.
  
  
SPMD IR is the PhD project of Semih Burak at RWTH Aachen University, with
contributions from students and student workers.

## Repositories

| Repository | What it is |
|---|---|
| [`spmd`](https://github.com/spmd-ir/spmd) | The dialect, its passes and analyses, and the `spmd-verify` driver. Start here. |
| `data-race-detection-benchmark-suite` | Benchmark corpus for the data-race and thread-safety checks. *Not public yet.* |
| `collective-verification-benchmark-suite` | Benchmark corpus for the collective-communication checks. *Not public yet.* |

The repositories here are read-only mirrors of the development repositories
at RWTH Aachen University. Issues and pull requests are welcome; pull
requests are merged upstream and arrive here with the next mirror update.

## Related projects

- [USIS](https://github.com/RWTH-HPC/USIS) — the Unified Semantic Interface
  Specification, which generates the machine-readable API descriptions SPMD IR
  uses to recognise each programming model's calls.
- Built on [MLIR](https://mlir.llvm.org/), with
  [Enzyme-JAX](https://github.com/EnzymeAD/Enzyme-JAX) and
  [Reactant](https://github.com/EnzymeAD/Reactant) for raising C/C++ sources to
  MLIR and [Enzyme](https://github.com/EnzymeAD/Enzyme)'s alias analysis.

## Status

[`v0.1.0`](https://github.com/spmd-ir/spmd/releases/tag/v0.1.0) is the first
public release: a research prototype under active development. Interfaces,
pass names and supported subsets of each programming model may still change.
