# Oikonomia Deterministic Silicon Benchmark: Bare-Metal FPGA vs. CPU/GPU Containment

Open-source C hardware audit harnesses, raw Xilinx UltraScale+ PCIe Gen3 x16 BAR0 MMIO telemetry (`agfi-037dec8eb7fe5504d`), tail-jitter distributions, memory scaling comparisons, and SHA-256 verification manifest (`AUDIT_MANIFEST.json`).

## Verified Silicon Telemetry (`0000:34:00.0` | `0x1d0f:0xf010`)
- **Steady-State Core Power ($V_{\text{CCINT}}$):** 10 W (Last / Avg / Max)
- **Physical Drop Shunt:** 21 cycles @ 250 MHz (**84.0 ns**)
- **Posted BAR0 MMIO Write:** **84.34 ns** avg (100,000 writes) | **Non-Posted Read P50:** **870.00 ns**
- **FPGA BAR0 Invariant Gate:** **150.00 ns P50** / **160.00 ns P99** / **200.00 ns P99.9** (**50.00 ns** P99.9-P50 jitter)
- **OS-Mediated CPU Pipe Gate:** **1,150.00 ns P50** / **9,230.00 ns P99.9** / **14,740.00 ns Max** (**8,080.00 ns** P99.9-P50 jitter)
- **Adversarial Attack Containment:** **5,000 / 5,000 (100.00%)** blocked across cap, policy, replay, and TOCTOU vectors
- **State Footprint & Reversibility:** **256 bytes (0.25 KB)** constant $O(1)$ manifold; **0 bits LSB drift** across 10,000-step inverse pass $T^{-1}$ (vs. 62,592 KB RSS growth for $O(N)$ log and 937 drifted bits / $5.46 \times 10^{21}$ error in IEEE 754 `double`)
