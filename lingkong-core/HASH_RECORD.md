# LingKong Core — SHA256 Prior Art Hash Record
## 凌控核 IP时间戳哈希存档

**Author:** Mao Guanghui (毛广辉)  
**Timestamp:** 2026-05-02  
**Purpose:** Public prior art establishment via cryptographic hash

---

## File Hashes (SHA256)

| File | SHA256 | Description |
|------|--------|-------------|
| PRIOR_ART_LINGKONG.md | `03f4912098a5ce450c38313e75ad89652110f9ec8764630f85cf5ac80f42436e` | Architecture claims & novel features |
| VERIFICATION_REPORT.md | `7088c2ae022ec65d97373152f5b3a516be05c87f2c9a88e83d6530dd0d44626b` | Full 32/32 verification report |
| EXECUTIVE_SUMMARY.md | `cc8476274de55017390219401bfd95f30289c4d29645df967609b2412c7bf3b1` | IP licensing business summary |

---

## Combined Hash (all three files concatenated)

```
a8a894a1df11fd02a503fd860ae0d49756377a0387584cabe0eef0a486b48634
```

---

## Verification Method

Anyone can verify these hashes by:
1. Downloading the files from this repository
2. Running: `sha256sum FILENAME.md`
3. Comparing output with the hashes above

Any modification to the files will produce a completely different hash,  
proving that the content existed in its current form as of the commit timestamp.

---

## Architecture Claims Summary (for hash record)

The following novel architectural claims are covered by this prior art record:

1. Zero-Heat Power Domain with photon bypass trigger (EFF=98%, ΔT=0.001K)
2. RISC-V RV32I single-cycle CPU Core with 10-instruction ISA subset
3. INT8 4×4 MAC Array AI Inference Engine with ReLU and batch clear
4. Tri-domain integration: CPU + Zero-Heat + AI on 1mm² target die
5. Power sampler with 4-cycle sliding average and peak tracking
6. Photon bypass controller with threshold-triggered activation counter
7. Thermal feedback controller with real-time EFF calculation
8. vec_mac parallel row computation with independent ReLU per output
9. Zero-Heat domain as standalone IP licensable independent of CPU core
10. Full pipeline verified: 32/32 scenarios, Icarus Verilog 12.0

---

*This hash record is intentionally public to establish prior art.*  
*MGOVL v2.0 — Viewing and citation permitted. Commercial use requires written authorization.*  
*© 2026 Mao Guanghui. All architectural rights reserved.*
