# FPGA Learning Journal

> My structured notes, designs, and testbenches from learning FPGA design — from combinational logic to sequential circuits — using **VHDL / Verilog**, **Quartus Prime Lite**, and **ModelSim**, targeting the **Intel MAX 10 (10M50DAF484C7G) on the Terasic DE10-Lite**.

![Quartus](https://img.shields.io/badge/Quartus_Prime-Lite-blue)
![Simulator](https://img.shields.io/badge/Simulator-ModelSim%2FQuesta-orange)
![Language](https://img.shields.io/badge/HDL-VHDL%20%7C%20Verilog-green)
![Board](https://img.shields.io/badge/Target-DE10--Lite-lightgrey)

## About

I'm a B.Sc. (Hons.) Physics student at Sri Sathya Sai Institute of Higher Learning with a growing focus on digital design and VLSI. This repo is both a **personal reference** (so I never have to re-learn a workflow from scratch) and a **portfolio** of the designs I've built and verified.

**Status legend used throughout this repo**

| Badge | Meaning |
|---|---|
| ✅ Simulated | Verified with a self-checking testbench in ModelSim |
| ✅ Synthesized | Compiled in Quartus; reports reviewed (resources, timing) |
| 🔲 On hardware | Programmed and tested on a DE10-Lite *(planned — board not yet available)* |

## Repository Structure

```
fpga-learning-journal/
├── README.md
├── LICENSE
├── .gitignore
├── docs/
│   ├── theory/                 # Notes: number systems, Boolean algebra, combinational, sequential, timing
│   ├── tools/                  # Quartus & ModelSim workflows, "delta cards" per new topic
│   └── images/                 # Waveforms, RTL viewer screenshots, block diagrams
├── 01-combinational/
│   ├── gates/
│   ├── mux_demux/
│   ├── adders/
│   └── comparators/
├── 02-sequential/
│   ├── latches/
│   ├── dff_variants/           # plain, enable, async reset, sync reset
│   ├── registers/
│   ├── shift_register/
│   └── accumulator/
├── 03-fsm-and-counters/        # (upcoming)
├── 04-advanced/                # memories, PLLs, ADC, clock domain crossing (upcoming)
├── projects/
│   └── de10-lite-final-year/   # Final-year project (in progress)
└── templates/
    ├── project_README_template.md
    ├── testbench_template.vhd
    └── quartus_sdc_template.sdc
```

Each design folder follows the same layout:

```
design_name/
├── README.md        # Aim, theory, block diagram, results
├── src/             # HDL source
├── tb/              # Testbench
├── sim/             # ModelSim .do script (not the generated work/ library)
├── constraints/     # .sdc, .qsf pin assignments
└── docs/            # Waveform + RTL viewer screenshots
```

## Roadmap

### Theory & Designs
- [x] Combinational logic — gates, multiplexers, adders, comparators
- [x] Sequential basics — latches, D flip-flops, registers, enable, resets
- [ ] 4-bit accumulator with enable and reset
- [ ] 4-bit shift register with parity/comparison output
- [ ] Counters
- [ ] Finite State Machines (Moore / Mealy)
- [ ] Memories (ROM / RAM)
- [ ] PLLs and clocking
- [ ] ADC interfacing (MAX 10)
- [ ] Clock domain crossing

### Tooling
- [x] Quartus Prime flow: project setup → compile → RTL / Technology Map viewers → Chip Planner
- [x] Timing Analyzer (all corners) and basic SDC constraints
- [x] ModelSim simulation with VHDL testbenches
- [ ] Pin assignment and programming the DE10-Lite *(pending board)*
- [ ] SignalTap logic analyzer

### Capstone
- [ ] Final-year project on the DE10-Lite — see [`projects/de10-lite-final-year`](projects/de10-lite-final-year)

## Designs Index

| # | Design | Language | Simulated | Synthesized | On hardware | Link |
|---|---|---|---|---|---|---|
| 1 | 4-bit register | VHDL | ✅ | ✅ | 🔲 | [`02-sequential/registers`](02-sequential/registers) |
| 2 | *add as you go…* | | | | | |

## Documentation Highlights

- **Theory notes** — [`docs/theory`](docs/theory)
- **Quartus workflow (learn once)** — [`docs/tools/quartus-workflow.md`](docs/tools/quartus-workflow.md)
- **ModelSim workflow** — [`docs/tools/modelsim-workflow.md`](docs/tools/modelsim-workflow.md)
- **Delta cards** (only what's *new* per topic: HDL constructs, viewers, SDC, timing reports) — [`docs/tools/delta-cards`](docs/tools/delta-cards)

## Getting Started

**Requirements**
- Intel Quartus Prime Lite (version used: *25.1* — verify against your install)
- ModelSim / Questa Intel FPGA Edition (bundled with Quartus)
- Target device: Intel MAX 10 `10M50DAF484C7G` (DE10-Lite)

**Run a simulation**
```bash
git clone https://github.com/Russhi1/fpga-learning-journal.git
cd fpga-learning-journal/02-sequential/registers/sim
# In ModelSim's transcript window:
do run_sim.do
```

**Build in Quartus**
1. Open the `.qpf` project file inside the design folder (or create a new project and add `src/`).
2. Set device to `10M50DAF484C7G`.
3. Processing → Start Compilation.
4. Review the Compilation Report, RTL Viewer, and Timing Analyzer.

## Conventions

- **Naming:** `snake_case` for files and signals; `_tb` suffix for testbenches; `_n` suffix for active-low signals
- **Every design includes:** a self-checking testbench, a waveform screenshot, and a short README with aim, theory, and results
- **Commits:** small and descriptive (`add: 4-bit accumulator with sync reset + testbench`)
- **Generated files are not committed** (see `.gitignore`)

## Resources

- Terasic DE10-Lite user manual
- Intel MAX 10 device handbook
- Quartus Prime and ModelSim user guides
- Course: *Digital Design for FPGAs*

## License

Code is released under the [MIT License](LICENSE). Notes and documentation are shared for learning purposes.

## Contact

**Rushil** — GitHub: [@Russhi1](https://github.com/Russhi1)
