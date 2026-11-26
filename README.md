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

## Zero-Integration 72-Hour Deterministic Containment Sprint
Enterprise infrastructure, safety-critical AI, and regulated systems teams do not need to provision AWS F2 instances, configure PCIe BAR0 drivers, or share a 12-digit AWS Account ID. Oikonomia runs custom invariant-gating, tail-jitter, and bit-exact $T^{-1}$ causal unwinding audits inside our air-gapped enclave:

1. **Submit Anonymized Policy & Event Vectors:** Email a JSON/CSV batch of up to 100,000 sequential action/state payloads (interleaved with threshold/cap breaches, policy violations, monotonic epoch replays, and TOCTOU payload mutations) to `contact@oikonomia-platform.com`.
2. **Private Vault Execution:** Direct userspace C PCIe BAR0 MMIO validation (`exp1_silicon_audit.c`) executes inside Oikonomia's single-tenant, zero-egress AWS F2 enclave (`10 W` steady-state $V_{CCINT}$).
3. **Cryptographically Signed Benchmark Dossier:** Receive the complete `SHA-256` signed hardware audit log, nanosecond `P50 / P99 / P99.9` latency distribution (`150.00 ns P50` / `84.0 ns` physical cutoff), `0.25 KB` constant memory proof, and 0-bit drift $10,000$-step $T^{-1}$ causal unwinding attestation within 72 hours (`$7,500–$12,000` flat sprint via AWS Marketplace Private Offer or invoice).
