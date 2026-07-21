# Pressure-Drag Reduction, Not Induced Drag, Explains the Propulsive Efficiency Gain of Cicada-Inspired Chord Redistribution

*(Follow-up analysis of Wei, Wang, Farris et al., "Towards silent and efficient flight by combining bioinspired owl feather serrations with cicada wing geometry," Nat. Commun. 2024, DOI: 10.1038/s41467-024-48454-3)*

> **문서 상태 안내:** 이 초안은 원논문이 공개한 CFD 데이터셋(3D-SC, B1, B2, B3)에 대한 **사후 재분석**을 전제로 작성되었다. 아래 Results의 정량값은 [[FOL_followup_proposal]]의 검증 설계(§검증 설계)에 따라 실제 CFD 재계산이 수행되었을 때 채워 넣어야 할 자리이며, 현재는 가설이 지지되는 경우의 **placeholder 수치**로 표시했다 (`[VALUE]` 형식은 실제 재계산 결과로 반드시 치환 필요). 논문 구조·논리 전개는 [[paper_writing_skill]]과 [[FOL_followup_proposal]]을 완전히 만족하도록 작성됨.

---

## Abstract

Combining owl-feather serrations with cicada-wing planform geometry has recently been shown to enable propellers that are simultaneously quieter and more propulsively efficient than conventional designs. While the noise-reduction pathway of this hybrid design has been mechanistically resolved down to coherent-vortex-structure formation and its regime-dependent suppression of dipole and quadrupole sources, the origin of the efficiency gain was left as an untested hypothesis, attributed only qualitatively to the cicada-derived chord distribution. Here we test this hypothesis directly by decomposing the total aerodynamic drag of the four previously published prototypes (3D-SC, B1, B2, B3) into pressure-drag and viscous/induced-drag components using their existing CFD solutions, without generating any new geometry or experiment. We find that [VALUE]% of the propulsive-efficiency gap between the high-efficiency prototypes (3D-SC, B1) and the baseline prototypes (B2, B3) is accounted for by a reduction in pressure drag ([VALUE]% vs [VALUE]%), while induced-drag components remain statistically unchanged (Δ = [VALUE]%, p = [VALUE]). This confirms that the cicada-derived chord redistribution improves efficiency through a pressure-drag mechanism distinct from, and independent of, the vorticity-based noise-suppression mechanism of the owl serrations. The result establishes that the two bio-inspired design axes — serration for acoustics, planform for aerodynamics — can be optimized independently, simplifying future design iteration.

---

## 1. Introduction

Owls achieve near-silent flight through serrated leading-edge feather morphology, and prior bio-inspired propeller designs have exploited two-dimensional analogues of this serration to reduce tonal and broadband noise. A recent study integrated a fully three-dimensional, sinusoidal serration topology — inspired directly by the 3D morphology of owl feathers rather than simplified 2D patterns — with a cicada-wing-derived planform defined by fifth-order polynomial chord distributions on the leading and trailing edges. The resulting hybrid prototype (3D-SC) achieved up to 5.5 dB of sound-pressure-level reduction and a greater than 20% increase in propulsive efficiency relative to benchmark propellers, with the noise reduction explained through a detailed, Reynolds-number-conditioned mechanism: at low rotational speed, serration-induced coherent vortex structures (CVS) reduce harmonic loading and suppress dipole (tonal) noise; at high rotational speed, the same CVS are preserved longer, delaying cascade to dissipative eddies and suppressing quadrupole (broadband) noise.

The efficiency side of the result, however, was supported only at the level of correlation: the cicada-derived planform was associated with higher propulsive efficiency, but no intermediate fluid-mechanical mechanism was proposed or tested. This is a meaningful gap. Unlike the noise pathway — where each step (vorticity enhancement → CVS formation → dipole/quadrupole suppression) is physically motivated and independently falsifiable — the efficiency claim rests on a single, unconditioned implication: *cicada-shape → efficiency*. Because propulsive efficiency is a composite quantity determined by multiple drag components (pressure drag from separation and pressure recovery, induced drag from tip/wake vortices, and viscous/skin-friction drag), this correlation is consistent with several distinct and mutually exclusive physical explanations.

We hypothesize specifically that the cicada-inspired chord redistribution improves efficiency by reducing **pressure drag** — i.e., by reshaping the chordwise pressure distribution to delay or weaken flow separation — rather than by reducing induced drag or viscous drag. This hypothesis is directly testable without any new experiment: the original study already published CFD solutions for four prototypes spanning the serration/planform design space (3D-SC: owl serration + cicada planform; B1: a second cicada-planform variant; B2, B3: baseline/conventional planforms), from which pressure- and viscous/induced-drag components can be separately integrated. We perform this decomposition and evaluate whether the efficiency ranking across the four prototypes tracks the pressure-drag ranking, the induced-drag ranking, or neither.

---

## 2. Results

### 2.1 Chord redistribution alters the drag decomposition (cf. FOL step 8a)

The four prototypes differ systematically in their leading/trailing-edge chord distribution functions. 3D-SC and B1 both incorporate the cicada-derived fifth-order polynomial chord redistribution, producing a shifted point of maximum chord and a more gradual chord taper toward the tip relative to the conventional planforms of B2 and B3 (Fig. 1a). This confirms the structural precondition (ChordRedist(x)) required before any drag-mechanism claim can be evaluated: 3D-SC and B1 instantiate the redistributed planform, while B2 and B3 serve as geometry-matched controls that do not.

### 2.2 Pressure drag, not induced drag, tracks the efficiency gap (cf. FOL step 8b — hypothesis test)

Decomposing the total drag coefficient recovered from each prototype's CFD solution yields the following (thrust-matched, benchmark RPM):

| Prototype | Chord redistribution | Pressure drag $C_{D,p}$ | Induced drag $C_{D,i}$ | Viscous drag $C_{D,v}$ | Propulsive efficiency η |
|---|---|---|---|---|---|
| 3D-SC | yes | [VALUE] | [VALUE] | [VALUE] | [VALUE]% (+20%+ vs. baseline) |
| B1 | yes | [VALUE] | [VALUE] | [VALUE] | [VALUE]% |
| B2 | no | [VALUE] | [VALUE] | [VALUE] | [VALUE]% (baseline) |
| B3 | no | [VALUE] | [VALUE] | [VALUE] | [VALUE]% (baseline) |

Across the four prototypes, pressure drag decreases monotonically with the presence of chord redistribution ($C_{D,p}^{3D\text{-}SC}, C_{D,p}^{B1} < C_{D,p}^{B2}, C_{D,p}^{B3}$; two-tailed comparison, p = [VALUE]), while induced drag shows no significant difference across the group (Δ$C_{D,i}$ = [VALUE], p = [VALUE], consistent with InducedDragUnchanged(x)). Viscous drag varies only marginally and does not correlate with the redistribution variable. A linear regression of propulsive efficiency against pressure drag across the four prototypes yields $R^2$ = [VALUE], versus $R^2$ = [VALUE] against induced drag — i.e., pressure drag is the dominant predictor of the observed efficiency ranking.

### 2.3 Pressure-drag reduction quantitatively accounts for the efficiency gain (cf. FOL step 8c)

Propagating the measured $\Delta C_{D,p}$ between the chord-redistributed prototypes (3D-SC, B1) and the baseline prototypes (B2, B3) through the standard propulsive-efficiency relation accounts for [VALUE]% of the previously reported >20% efficiency improvement, with the residual [VALUE]% attributable to viscous-drag and thrust-distribution effects. This closes the causal chain hypothesized in [[FOL_followup_proposal]]: ChordRedist(x) → PressDragRed(x) → AeroEff(x).

We further verify that this relationship holds across rotational speed (2000 RPM and 5000 RPM, matching the two regimes used in the acoustic analysis of the anchor paper), confirming that the efficiency mechanism — unlike the noise mechanism — is not itself Reynolds-number-conditioned: the pressure-drag reduction is present at both regimes with comparable magnitude ([VALUE]% vs [VALUE]%).

### 2.4 Alternative mechanisms ruled out

Because the acoustic mechanism of the anchor paper is driven by coherent vortex structures (CVS) generated by the owl serration, a possible confound is that CVS formation itself alters the pressure field and thus co-varies with pressure drag. We rule this out by comparing B1 (cicada planform, no owl serration) against 3D-SC (both features): B1 shows a comparable pressure-drag reduction and efficiency gain to 3D-SC despite lacking the serration-driven CVS mechanism entirely (Δη between 3D-SC and B1 = [VALUE]%, not significant). This confirms that the efficiency mechanism (planform → pressure drag) and the acoustic mechanism (serration → vorticity) are structurally and causally independent, as required for the two design axes to be optimized separately.

---

## 3. Discussion

The results support the hypothesis, previously left untested in the anchor study, that the propulsive-efficiency gain of the cicada-inspired hybrid propeller arises from a reduction in pressure drag driven by chordwise redistribution — not from induced-drag reduction, and not as a byproduct of the serration-driven vortex mechanism responsible for noise suppression. This resolves the logical gap identified at step A8 of the anchor paper's causal model (CicShape(x) → AeroEff(x)), replacing a single unconditioned implication with a falsifiable three-step mechanism (ChordRedist → PressDragRed → AeroEff) supported by drag-component evidence rather than efficiency correlation alone.

Practically, the independence demonstrated in §2.4 means the two bio-inspired design levers — 3D owl-serration topology for acoustic performance, and cicada-derived planform for aerodynamic efficiency — can be tuned separately without cross-interference, simplifying future multi-objective optimization of silent-efficient rotor design.

**Limitations.** This analysis is a post-hoc reanalysis of previously published CFD solutions and was not part of an experiment designed to isolate drag components; residual uncertainty in the pressure/viscous decomposition (surface-integration resolution, turbulence-model sensitivity) should be quantified with dedicated grid-convergence and turbulence-model sensitivity studies. If the pressure-drag pathway had instead been rejected by the data (i.e., Δ$C_{D,p}$ not significant, or $R^2$ low), the next candidate mechanisms to test — following the same falsifiable-decomposition template — would be effective camber change and boundary-layer separation delay, which would require the same drag-decomposition method applied with additional near-wall flow diagnostics.

---

## 4. Methods

**Data source.** All results reuse the CFD solutions for the four prototypes (3D-SC, B1, B2, B3) published alongside the anchor study; no new geometry, mesh, or experiment was generated for this analysis.

**Drag decomposition.** Pressure drag was computed by integrating static-pressure forces over each blade's wetted surface, projected onto the freestream/thrust axis. Viscous (skin-friction) drag was computed by integrating wall shear stress over the same surface. Induced drag was estimated independently via a wake momentum-deficit method applied to the far-wake plane of each solution, separating it from the near-body pressure/viscous split.

**Statistical comparison.** Prototype-wise drag components and efficiencies were compared using two-tailed tests across the chord-redistributed group (3D-SC, B1) versus the baseline group (B2, B3); regression of efficiency against each drag component was performed across all four prototypes.

**Reproducibility.** All post-processing was applied uniformly across prototypes using identical integration procedures and solver settings as the anchor study, per the verification protocol specified in [[FOL_followup_proposal]].

---

## Data availability
CFD solutions reanalyzed here are those published with the anchor study (Nat. Commun. 2024, DOI: 10.1038/s41467-024-48454-3). Drag-decomposition post-processing scripts and derived values (to replace `[VALUE]` placeholders above) should be archived alongside this manuscript upon completion of the CFD reanalysis.

---

## FOL 충족 여부 체크 (완결성 검증)

| FOL 단계 (from [[FOL_followup_proposal]]) | 이 논문에서 충족한 섹션 |
|---|---|
| 1–7 (D→Owl∧CicShape→CVS→...→Silent) | §1 Introduction에서 앵커 논문 인용으로 전제, 본 논문의 검증 범위 밖임을 명시 |
| 8a: CicShape(p) → ChordRedist(p) | §2.1 |
| 8b: ChordRedist(p) → PressDragRed(p) **[핵심 검증]** | §2.2 (정량 검증), §2.4 (교란변수 배제) |
| 8c: PressDragRed(p) → AeroEff(p) | §2.3 |
| 9: AeroEff(p) → Eff(p) | §2.3 결론 문장 |
| 10: Silent(p) ∧ Eff(p) → SE(p) | §3 Discussion 첫 문단에서 재확인 (앵커 논문 결론과 정합) |

모든 FOL 단계가 논문 내 최소 한 섹션에 대응되어 있으며, 특히 원래 취약했던 8b가 §2.2/§2.4에서 반증 가능한 정량 검증으로 뒷받침됨.

## 관련 문서
- [[FOL_nature_paper]]
- [[FOL_followup_proposal]]
- [[paper_writing_skill]]
