# Pressure-Drag Reduction, Not Induced Drag, Explains the Propulsive Efficiency Gain of Cicada-Inspired Chord Redistribution

**Author(s):** *[저자명 기입 필요]*
**Affiliation:** *[소속 기입 필요]*

*(Follow-up analysis of Wei, Z., Wang, S., Farris, S. et al. "Towards silent and efficient flight by combining bioinspired owl feather serrations with cicada wing geometry." Nat. Commun. 15, 4337 (2024). [1])*

> **문서 상태 안내 (반드시 읽을 것):** 이 초안은 원논문[1]이 공개한 CFD 데이터셋(3D-SC, B1, B2, B3)에 대한 **사후 재분석 계획**이며, 실제 CFD 재계산은 아직 수행되지 않았다. 본문의 모든 `[VALUE]`는 재계산이 완료된 뒤 실측값으로 반드시 치환해야 하며, 그 전까지 이 문서를 "결과가 확인된 논문"으로 인용하거나 배포해서는 안 된다. 또한 이 문서에는 실제로 생성된 그림(Figure)이 없다 — 본문에서 그림을 언급하지 않은 것은 이 때문이며, 이는 이전 버전의 오류(존재하지 않는 "Fig. 1a" 인용)를 수정한 것이다. 논문 구조·논리 전개는 [[paper_writing_skill]]과 [[FOL_followup_proposal]]을 만족하도록 작성됨.

---

## Abstract

Combining owl-feather serrations with cicada-wing planform geometry has recently been shown to enable propellers that are simultaneously quieter and more propulsively efficient than conventional designs. While the noise-reduction pathway of this hybrid design has been mechanistically resolved down to coherent-vortex-structure (CVS) formation and its regime-dependent suppression of dipole and quadrupole sources, the origin of the efficiency gain was left as an untested hypothesis in that study, attributed only qualitatively to the cicada-derived chord distribution. Here we propose to test this hypothesis directly by decomposing the total aerodynamic drag of the four previously published prototypes (3D-SC, B1, B2, B3) into pressure-drag and viscous/induced-drag components, following standard drag-decomposition practice, using their existing CFD solutions and without generating any new geometry or experiment. If confirmed, we predict that the majority of the propulsive-efficiency gap between the high-efficiency prototypes (3D-SC, B1) and the baseline prototypes (B2, B3) would be accounted for by a reduction in pressure drag, while induced-drag components would remain statistically unchanged. Such a result would confirm that the cicada-derived chord redistribution improves efficiency through a mechanism distinct from, and independent of, the vorticity-based noise-suppression mechanism of the owl serrations, establishing that the two bio-inspired design axes — serration for acoustics, planform for aerodynamics — can be optimized independently.

*(참고: Nature Communications 등 주요 저널 관행상 Abstract에는 참고문헌 번호를 넣지 않는다 — 초록만 단독으로 읽힐 수 있어 문헌번호가 본문 없이는 의미가 없기 때문. 이전 버전에서 Abstract에 [1][2]를 넣은 것은 이 관행을 어긴 실수였다.)*

---

## 1. Introduction

A recent study demonstrated that combining owl-feather serrations with cicada-wing planform geometry enables propellers that are simultaneously quieter and more propulsively efficient than conventional designs [1]. This builds on a long tradition of drawing engineering inspiration from biological structures shaped by selective pressure, and in particular on a substantial body of work exploiting the serrated leading-edge feather morphology that allows owls to achieve near-silent flight [2,3]. Prior bio-inspired propeller designs exploited two-dimensional analogues of this serration to reduce tonal and broadband noise, but such simplified two-dimensional patterns limit the achievable noise reduction and often trade off against aerodynamic performance [1].

Wei et al. [1] recently integrated a fully three-dimensional, sinusoidal serration topology — inspired directly by the 3D morphology of owl feathers rather than simplified 2D patterns — with a cicada-wing-derived planform defined by fifth-order polynomial chord distributions on the leading and trailing edges. The resulting hybrid prototype (3D-SC) achieved up to 5.5 dB of sound-pressure-level reduction and a greater than 20% increase in propulsive efficiency relative to benchmark propellers [1]. In that work, the noise reduction was explained through a detailed, Reynolds-number-conditioned mechanism: at low rotational speed, serration-induced coherent vortex structures (CVS) reduce harmonic loading and suppress dipole (tonal) noise; at high rotational speed, the same CVS are preserved longer, delaying cascade to dissipative eddies and suppressing quadrupole (broadband) noise [1].

The efficiency side of that result, however, was supported only at the level of correlation: the cicada-derived planform was associated with higher propulsive efficiency, but no intermediate fluid-mechanical mechanism was proposed or tested [1]. This is a meaningful gap. Unlike the noise pathway — where each step (vorticity enhancement → CVS formation → dipole/quadrupole suppression) is physically motivated and independently falsifiable — the efficiency claim in [1] rests on a single, unconditioned implication: cicada-shape → efficiency. Because propulsive efficiency is a composite quantity determined by multiple drag components — pressure drag from separation and pressure recovery, induced drag from tip/wake vortices, and viscous/skin-friction drag [4] — this correlation is consistent with several distinct and mutually exclusive physical explanations.

We hypothesize specifically that the cicada-inspired chord redistribution improves efficiency by reducing pressure drag — i.e., by reshaping the chordwise pressure distribution to delay or weaken flow separation — rather than by reducing induced drag or viscous drag. This hypothesis is directly testable without any new experiment: Wei et al. [1] already published CFD solutions for four prototypes spanning the serration/planform design space (3D-SC: owl serration + cicada planform; B1: a second cicada-planform variant; B2, B3: baseline/conventional planforms), from which pressure- and viscous/induced-drag components can, in principle, be separately integrated [4]. We propose to perform this decomposition and evaluate whether the efficiency ranking across the four prototypes tracks the pressure-drag ranking, the induced-drag ranking, or neither.

---

## 2. Proposed Results *(pending CFD reanalysis — see status note above)*

The subsections below describe the analysis to be performed and the falsifiable predictions each step makes, mapped to the FOL steps in [[FOL_followup_proposal]]. **No values in this section are measured yet.**

### 2.1 Chord redistribution alters the drag decomposition (cf. FOL step 8a)

The four prototypes reported in [1] differ systematically in their leading/trailing-edge chord distribution functions: 3D-SC and B1 incorporate the cicada-derived fifth-order polynomial chord redistribution, while B2 and B3 use conventional planforms [1]. This is the structural precondition (ChordRedist(x)) required before any drag-mechanism claim can be evaluated, and requires no new analysis to confirm — it is already established in [1].

### 2.2 Pressure drag, not induced drag, is predicted to track the efficiency gap (cf. FOL step 8b — hypothesis test)

**Planned analysis:** decompose the total drag coefficient recovered from each prototype's CFD solution in [1] into pressure drag $C_{D,p}$, induced drag $C_{D,i}$, and viscous drag $C_{D,v}$, using the surface-pressure and wake-momentum methods described in §4 (Methods).

**Prediction table (to be filled with measured values):**

| Prototype | Chord redistribution | $C_{D,p}$ | $C_{D,i}$ | $C_{D,v}$ | Propulsive efficiency η |
|---|---|---|---|---|---|
| 3D-SC | yes | `[VALUE]` | `[VALUE]` | `[VALUE]` | `[VALUE]`% (reported: +20%+ vs. baseline [1]) |
| B1 | yes | `[VALUE]` | `[VALUE]` | `[VALUE]` | `[VALUE]`% |
| B2 | no | `[VALUE]` | `[VALUE]` | `[VALUE]` | `[VALUE]`% (baseline) |
| B3 | no | `[VALUE]` | `[VALUE]` | `[VALUE]` | `[VALUE]`% (baseline) |

**Falsifiable prediction:** if the hypothesis holds, $C_{D,p}^{3D\text{-}SC}, C_{D,p}^{B1} < C_{D,p}^{B2}, C_{D,p}^{B3}$ with statistical significance, while $\Delta C_{D,i}$ across the group is not significant. A regression of η against $C_{D,p}$ should yield higher $R^2$ than η against $C_{D,i}$.

### 2.3 Pressure-drag reduction is predicted to quantitatively account for the efficiency gain (cf. FOL step 8c)

**Planned analysis:** propagate the measured $\Delta C_{D,p}$ between the chord-redistributed prototypes (3D-SC, B1) and the baseline prototypes (B2, B3) through the standard propulsive-efficiency relation [4], and compare the resulting predicted efficiency gain against the >20% efficiency improvement reported in [1]. We will also test whether this relationship holds across both rotational-speed regimes used in the acoustic analysis of [1] (2000 RPM and 5000 RPM), to check whether the efficiency mechanism is Reynolds-number-conditioned as the noise mechanism is [1].

### 2.4 Alternative mechanisms to be ruled out

Because the acoustic mechanism in [1] is driven by coherent vortex structures generated by the owl serration, a possible confound is that CVS formation itself alters the pressure field and thus co-varies with pressure drag. **Planned control:** compare B1 (cicada planform, no owl serration) against 3D-SC (both features) [1]; if B1 shows a comparable pressure-drag reduction and efficiency gain to 3D-SC despite lacking the serration-driven CVS mechanism, this would confirm that the efficiency mechanism (planform → pressure drag) and the acoustic mechanism (serration → vorticity) are structurally independent.

---

## 3. Discussion

If the predictions in §2.2–2.4 are confirmed, this analysis would resolve the logical gap identified at step A8 of the causal model implicit in [1] (CicShape(x) → AeroEff(x)), replacing a single unconditioned implication with a falsifiable three-step mechanism (ChordRedist → PressDragRed → AeroEff) supported by drag-component evidence rather than efficiency correlation alone. Practically, confirming the independence proposed in §2.4 would mean the two bio-inspired design levers reported in [1] — 3D owl-serration topology for acoustic performance, and cicada-derived planform for aerodynamic efficiency — could be tuned separately without cross-interference, simplifying future multi-objective optimization of silent-efficient rotor design.

**Limitations.** This is a post-hoc reanalysis proposal applied to CFD solutions from [1] that were not generated to isolate drag components; residual uncertainty in the pressure/viscous decomposition (surface-integration resolution, turbulence-model sensitivity) will need to be quantified with dedicated grid-convergence and turbulence-model sensitivity studies [4]. If the pressure-drag pathway (§2.2) were instead rejected by the data, the next candidate mechanisms to test — following the same falsifiable-decomposition template — would be effective camber change and boundary-layer separation delay, requiring the same drag-decomposition method applied with additional near-wall flow diagnostics.

---

## 4. Methods (planned)

**Data source.** All planned analysis reuses the CFD solutions for the four prototypes (3D-SC, B1, B2, B3) published alongside [1]; no new geometry, mesh, or experiment will be generated.

**Drag decomposition.** Pressure drag will be computed by integrating static-pressure forces over each blade's wetted surface, projected onto the freestream/thrust axis. Viscous (skin-friction) drag will be computed by integrating wall shear stress over the same surface. Induced drag will be estimated independently via a wake momentum-deficit method applied to the far-wake plane of each solution, following standard aerodynamic decomposition practice [4].

**Statistical comparison.** Prototype-wise drag components and efficiencies will be compared using two-tailed tests across the chord-redistributed group (3D-SC, B1) versus the baseline group (B2, B3); regression of efficiency against each drag component will be performed across all four prototypes.

**Reproducibility.** Post-processing will be applied uniformly across prototypes using identical integration procedures and solver settings as [1], per the verification protocol specified in [[FOL_followup_proposal]].

---

## Data availability
The CFD solutions to be reanalyzed are those published with [1] (Zenodo DOI: 10.5281/zenodo.11088631, as cited in [1]; access and licensing terms should be verified directly with that repository before reuse). No new data are generated by this proposal document.

## Code availability
No analysis code has been written yet. Drag-decomposition post-processing scripts, once written, should be archived in a public repository and linked here before this document is considered a completed manuscript.

## Acknowledgements
*[본 저자가 실제 저술 시 펀딩/기관 정보 기입 필요]*

## Author contributions
*[본 저자가 실제 저술 시 역할 기입 필요]*

## Competing interests
*[해당 사항 기입 필요 — 현재 명시된 이해상충 없음]*

---

## References

[1] Wei, Z., Wang, S., Farris, S. et al. Towards silent and efficient flight by combining bioinspired owl feather serrations with cicada wing geometry. *Nat. Commun.* **15**, 4337 (2024). https://doi.org/10.1038/s41467-024-48454-3

[2] Wang, Y., Zhao, K., Lu, X.-Y., Song, Y.-B. & Bennett, G. J. Bio-inspired aerodynamic noise control: a bibliographic review. *Appl. Sci.* **9**, 2224 (2019). https://doi.org/10.3390/app9112224

[3] Glegg, S. & Devenport, W. *Aeroacoustics of Low Mach Number Flows: Fundamentals, Analysis, and Measurement*, 464–494 (Academic Press, 2017).

[4] Anderson, J. D., Jr. *Fundamentals of Aerodynamics*, 6th edn (McGraw-Hill Education, New York, 2017). Chs. 1, 5 (drag decomposition: pressure vs. skin-friction drag) and Ch. 5 (induced drag, finite-wing theory) — standard reference for the drag-decomposition and propulsive-efficiency relations used in §1, §2.3, §3, and §4.

---

## FOL 충족 여부 체크 (완결성 검증)

| FOL 단계 (from [[FOL_followup_proposal]]) | 이 문서에서 다룬 위치 |
|---|---|
| 1–7 (D→Owl∧CicShape→CVS→...→Silent) | §1 Introduction에서 [1] 인용으로 전제, 본 문서의 검증 범위 밖임을 명시 |
| 8a: CicShape(p) → ChordRedist(p) | §2.1 (이미 [1]에서 확립됨, 추가 분석 불필요) |
| 8b: ChordRedist(p) → PressDragRed(p) **[핵심 검증 대상]** | §2.2 (예정된 정량 검증), §2.4 (예정된 교란변수 배제) |
| 8c: PressDragRed(p) → AeroEff(p) | §2.3 (예정) |
| 9: AeroEff(p) → Eff(p) | §2.3 결론 문장 (예정) |
| 10: Silent(p) ∧ Eff(p) → SE(p) | §3 Discussion 첫 문단 (예정, [1]의 결론과 정합 확인) |

**중요:** 위 표는 "이 문서가 논리적으로 어디를 다루는가"를 보여줄 뿐, **8b~10은 아직 실측으로 검증되지 않은 예정된 분석**이다. 이 점을 이전 버전보다 명확히 구분했다.

## 관련 문서
- [[FOL_nature_paper]]
- [[FOL_followup_proposal]]
- [[paper_writing_skill]]
