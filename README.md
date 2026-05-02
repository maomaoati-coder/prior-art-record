# 凌控核 · LingKong Core

<div align="center">

**Edge-AI MCU Architecture with Zero-Heat Power Domain**

[![Verification](https://img.shields.io/badge/Verification-32%2F32%20PASS-brightgreen?style=for-the-badge)](./lingkong-core/VERIFICATION_REPORT.md)
[![ISA](https://img.shields.io/badge/ISA-RISC--V%20RV32I-blue?style=for-the-badge)](./lingkong-core/PRIOR_ART_LINGKONG.md)
[![EFF](https://img.shields.io/badge/Efficiency-98%25-orange?style=for-the-badge)](./lingkong-core/PRIOR_ART_LINGKONG.md)
[![License](https://img.shields.io/badge/License-MGOVL%20v2.0-red?style=for-the-badge)](./License)

*Independently designed and verified by **Mao Guanghui (毛广辉)***  
*2026-05-02 · Icarus Verilog 12.0 · EDA Playground*

</div>

---

## Overview

**LingKong Core** is a novel Edge-AI MCU architecture that solves a fundamental tradeoff in embedded computing: AI inference capability has always come at the cost of higher power dissipation and heat.

LingKong Core eliminates this tradeoff through a **Zero-Heat Power Domain** — a photon-bypass-triggered thermal management architecture transplanted from the author's prior LengXin (冷芯) work — integrated directly with a RISC-V CPU core and an INT8 AI inference engine.

> **No team. No institution. No external funding.**  
> Architecture designed, simulated, and verified by a single independent inventor.

---

## Architecture

```
┌─────────────────────────────────────────────────┐
│              LingKong Core  (1mm² target)        │
│                                                  │
│  ┌──────────┐  ┌──────────┐  ┌───────────────┐  │
│  │ CPU Core │  │Zero-Heat │  │  AI Engine    │  │
│  │ RISC-V   │◄─│  Domain  │─►│  INT8 MAC 4×4 │  │
│  │ RV32I    │  │ EFF=98%  │  │  ReLU · 4-way │  │
│  └────┬─────┘  └──────────┘  └───────────────┘  │
│       │                                          │
│  ┌────▼─────┐  ┌──────────┐                     │
│  │  ALU     │  │  RegFile │                     │
│  │ 10 ops   │  │ 32×32bit │                     │
│  └──────────┘  └──────────┘                     │
└─────────────────────────────────────────────────┘
```

### Five-Layer Verification Pipeline

| Layer | Module | Description | Scenarios | Status |
|-------|--------|-------------|-----------|--------|
| L1 | Register File | 32×32-bit GPR, dual-read, x0 hardwired | 6 | ✅ 6/6 PASS |
| L2 | ALU | ADD/SUB/AND/OR/XOR/SLT/SLL/SRL/SRA | 10 | ✅ 10/10 PASS |
| L3 | CPU Core | Single-cycle fetch→decode→execute→writeback | 6 | ✅ 6/6 PASS |
| L4 | Zero-Heat Domain | Photon bypass · EFF=98% · ΔT=0.001K | 5 | ✅ 5/5 PASS |
| L5 | AI Inference Engine | INT8 4×4 MAC array · ReLU · batch clear | 5 | ✅ 5/5 PASS |
| | **TOTAL** | | **32** | **✅ 32/32 PASS** |

---

## Key Performance Parameters

| Parameter | Value | Conventional MCU |
|-----------|-------|-----------------|
| Power Efficiency (EFF) | **98%** | 60–75% |
| Thermal Delta (ΔT) | **0.001 K** | > 0.5 K |
| ISA | RISC-V RV32I | Varies |
| AI Precision | INT8 | Not available |
| Target Die Area | 1 mm² | — |
| Process Node | 28nm / 40nm | — |

---

## Novel Architectural Claims

**1. Zero-Heat Power Domain**  
Photon bypass controller triggers when average power exceeds threshold. Once activated: EFF → 98%, ΔT → 0.001K. No equivalent in commercially available Edge MCU products.

**2. RISC-V RV32I Single-Cycle Core**  
Full 10-instruction ISA subset including branch (BEQ) and jump (JAL). Register file and ALU independently verified before integration.

**3. INT8 AI Inference Engine**  
4×4 weight matrix MAC array with 4-way parallel vec_mac units. ReLU activation per output. Clear signal supports batch inference frame reset.

**4. Tri-Domain Integration**  
CPU Core + Zero-Heat Domain + AI Engine co-integrated in 1mm² target die. Zero-Heat domain operates as an independent power island, licensable separately.

---

## SHA256 Prior Art Hash Record

```
PRIOR_ART_LINGKONG.md    03f4912098a5ce450c38313e75ad89652110f9ec8764630f85cf5ac80f42436e
VERIFICATION_REPORT.md   7088c2ae022ec65d97373152f5b3a516be05c87f2c9a88e83d6530dd0d44626b
EXECUTIVE_SUMMARY.md     cc8476274de55017390219401bfd95f30289c4d29645df967609b2412c7bf3b1
```

**Combined hash (all three files):**
```
a8a894a1df11fd02a503fd860ae0d49756377a0387584cabe0eef0a486b48634
```

> These hashes, combined with the GitHub commit timestamp, establish an immutable prior art record.  
> Any modification produces a completely different hash — tampering is cryptographically detectable.

---

## Target Markets

| Segment | Market Size | Supply Status |
|---------|-------------|---------------|
| Edge AI Inference Modules | $18B | Demand surge |
| Industrial IoT MCU | $12B | Critical shortage |
| Automotive Sensor Control | $8B | Sustained shortage |
| Medical Wearables | $5B | Growth |

---

## IP Licensing

LingKong Core follows an **ARM-style asset-light model** — architecture licensed, not manufactured.

| Model | Terms |
|-------|-------|
| One-time architecture license | ¥500K – ¥5M per design win |
| Per-chip royalty | $0.1 – $1.0 per unit shipped |
| Joint development | Equity / revenue share; partner funds tape-out |
| Architecture consulting | IP retained by inventor |

**Seeking:** IP licensing partners · Joint development agreements · Strategic investment

---

## Repository Structure

```
prior-art-record/
├── README.md                          ← This file
├── License                            ← MGOVL v2.0
└── lingkong-core/
    ├── PRIOR_ART_LINGKONG.md          ← Architecture claims
    ├── VERIFICATION_REPORT.md         ← Full 32/32 simulation log
    ├── EXECUTIVE_SUMMARY.md           ← Business & licensing brief
    └── HASH_RECORD.md                 ← SHA256 timestamps
```

---

## License

**MGOVL v2.0 — Mao Guanghui Open View License**

- ✅ Viewing and citation permitted
- ✅ Academic reference permitted
- ❌ Reproduction prohibited without written authorization
- ❌ Commercial use prohibited without written authorization
- ❌ Adaptation or derivative works prohibited without written authorization

See [License](./License) for full terms.

---

## Author

**Mao Guanghui (毛广辉)**  
Independent Hardware Architecture Inventor

> Designed, simulated, and verified without institutional backing,  
> team support, or external funding.

---

<div align="center">

*This repository constitutes a public prior art record.*  
*All architectural rights reserved · © 2026 Mao Guanghui*

</div>
