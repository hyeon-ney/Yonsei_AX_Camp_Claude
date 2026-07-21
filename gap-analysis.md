# Gap Analysis — `paper_draft.md` vs. 실제 학술논문(앵커 논문 [1]) 형식 차이 (심각도별)

이 문서는 `paper_draft.md`가 실제 게재 가능한 논문(Nature Communications 앵커 논문[1] 기준)과 형식·완성도 측면에서 어떻게 다른지, 각 차이를 **심각도(Critical/High/Medium/Low)**로 분류해 정리한다. 심각도는 "이 차이가 이 문서를 학술 문서로서 신뢰할 수 없게 만드는 정도"를 기준으로 매긴다.

| 심각도 | 의미 |
|---|---|
| **Critical** | 독자가 이 문서를 "검증된 결과"로 오인할 수 있음 — 학술적 진실성 문제 |
| **High** | 재현성/검증가능성이 훼손됨 — 실제 논문이라면 게재 불가 사유 |
| **Medium** | 저널 표준 관행 미준수 — 격식은 부족하지만 오해를 유발하진 않음 |
| **Low** | 행정적/서식적 누락 — 저자가 채우면 되는 항목 |

---

## Critical

| 항목 | paper_draft.md 현황 | 앵커 논문[1] | 근거 |
|---|---|---|---|
| 실측 데이터 부재 | Results(§2.2~2.4)의 모든 수치가 `[VALUE]` placeholder — CFD 재분석이 실제로 수행되지 않음 | 모든 수치가 실제 CFD/실험 측정값 | 문서 상단 상태 안내에서 명시하고 있지만, 표 형태로 제시되어 있어 대충 훑으면 "실측된 표"처럼 보일 위험이 있음 |
| 실제 Figure 부재 | Figure 1~4가 텍스트 placeholder만 존재, 실제 이미지 없음 (자세한 내용은 아래 "Figure 상세 설명" 섹션 참조) | 모든 Figure가 실제 데이터 기반 그림 | 이전 버전에서는 존재하지 않는 "Fig. 1a"를 인용하는 더 심각한 오류가 있었으나 현재는 placeholder로 명시해 완화됨 |

## High

| 항목 | paper_draft.md 현황 | 앵커 논문[1] | 근거 |
|---|---|---|---|
| Methods의 재현성 정보 부족 | 솔버 이름/버전, 격자(mesh) 크기, 경계조건, 난류모델 등 구체적 시뮬레이션 스펙 없음 — "표준 절차를 따른다"는 서술만 있음 | Methods에 "Computational simulations" 하위섹션으로 솔버·격자·경계조건 상세 기술 | 앵커 논문 재현에는 이 정보가 필수이며, 없으면 제3자가 동일 CFD 재분석을 반복할 수 없음 |
| 통계적 검정의 사전등록 부재 | §2.2에서 "two-tailed test", "regression" 등을 언급하지만 유의수준(α), 표본 수(n=4, 매우 작음)에 대한 통계적 한계 논의가 없음 | — (앵커도 완벽하진 않으나 실측 데이터 기반이라 이 문제가 덜 심각) | n=4 프로토타입 비교는 통계적 검정력이 극히 낮아, 이 한계를 Limitations에 명시하지 않은 것은 방법론적 결함 |

## Medium

| 항목 | paper_draft.md 현황 | 앵커 논문[1] | 근거 |
|---|---|---|---|
| 참고문헌 수가 매우 적음 | 4개 ([1]~[4]) | 33개 | 후속 분석 논문이라 전체 배경 문헌을 다 재인용할 필요는 없지만, 항력 분리 방법론·통계 방법 관련 선행 연구가 Anderson 교과서 하나로만 뒷받침되는 것은 다소 얇음 |
| Reporting Summary / Checklist 부재 | 없음 | Nature 계열 저널은 제출 시 별도 "Reporting Summary" 필요 (본문엔 노출 안 되지만 저널 요구사항) | 실제 투고를 염두에 둔다면 언급이라도 필요 |
| Supplementary Information 부재 | 없음 (그림 자체가 없으므로) | 본문 전반에 SI 참조가 다수 존재 | 실측 이후에는 통계 세부표, 격자수렴성 결과 등을 SI로 분리해야 함 |
| Data availability의 구체성 | Zenodo DOI만 명시, 어떤 파일/포맷을 정확히 재사용하는지 명시 안 됨 | 앵커는 데이터 종류를 구체적으로 서술 | "어떤 파일을 어떻게 썼는지"가 없으면 재현성이 떨어짐 |
| 인용 형식이 위첨자가 아닌 대괄호 | `[1]` 형식 (마크다운 한계) | 위첨자 숫자 | 사소한 서식 차이, 마크다운→실제 투고 포맷 변환 시 자동 해결 가능 |

## Low

| 항목 | paper_draft.md 현황 | 앵커 논문[1] | 근거 |
|---|---|---|---|
| 저자/소속 미기입 | Placeholder | 9명 저자, UC Berkeley 명시 | 저자 본인이 채우면 되는 항목 |
| Acknowledgements/Author contributions/Competing interests | Placeholder | 모두 상세 기술 | 저술 완료 시 채우면 되는 항목, 초안 단계에서는 결함이 아님 |
| Peer review 문구 부재 | 없음 | "익명 심사 완료" 문구 있음 | 아직 투고 전이므로 해당 없음 (결함 아님) |

---

## 결론 — 우선순위

이 문서를 "완성된 논문"에 가깝게 만들기 위해 해결해야 할 순서:

1. **(Critical)** CFD 재분석 실제 수행 → `[VALUE]` 전부 치환
2. **(Critical)** 실제 Figure 1~4 제작 (아래 "Figure 상세 설명" 명세 기준)
3. **(High)** Methods에 솔버/격자/경계조건 등 구체 스펙 추가
4. **(High)** n=4 표본 크기의 통계적 한계를 Discussion/Limitations에 명시
5. **(Medium)** Reporting Summary, Supplementary Information 섹션 신설 (실측 이후)
6. **(Low)** 저자 정보 및 행정 섹션 채우기

Critical/High 항목은 실측 데이터가 있어야만 해결 가능하므로, 그 전까지 이 문서는 "완결된 논문"이 아니라 **검증 계획서(pre-registration-style proposal)**로만 취급되어야 한다.

---

# Figure 상세 설명 — `paper_draft.md`의 그림 자리 표시(placeholder)

`paper_draft.md`에는 실제 그림 대신 자리만 표시되어 있다 (위 "Critical — 실제 Figure 부재" 항목 참조). 아래는 CFD 재분석이 완료된 뒤 각 자리에 실제로 어떤 그림이 들어가야 하는지에 대한 상세 명세다. 그림 구성 원칙은 [[paper_writing_skill]] §6("Figure 구성: (a) 형상/개념도 (b) 유동장/CFD 시각화 (c) 정량 막대/산점도")을 따른다.

## Figure 1 — 대응 위치: §2.1 (Chord redistribution alters the drag decomposition)

**패널 구성 (3단):**

- **(a) Planform 오버레이:** 4개 프로토타입(3D-SC, B1, B2, B3)의 blade planform을 반경 방향(r/R) 대비 chord 길이(c/R)로 정규화하여 하나의 좌표축에 겹쳐 그린 선도(line overlay). 3D-SC/B1(cicada 재배치 곡선, 5차 다항식)은 실선, B2/B3(기존 planform)는 점선으로 구분. x축: 무차원 반경 위치(r/R, 0~1), y축: 무차원 chord 길이(c/R). 최대 chord 위치가 3D-SC/B1에서 더 바깥쪽(팁 방향)으로 이동해 있음을 화살표로 표시.
- **(b) Chord 분포 함수 계수 비교:** 각 프로토타입의 5차 다항식 계수를 막대그래프(bar chart)로 비교 — leading edge 계수 세트와 trailing edge 계수 세트를 각각 별도 서브패널로.
- **(c) 3D 렌더링:** 4개 blade의 3D CAD 렌더링을 나란히 배치(isometric view), chord 재배치가 시각적으로 어떻게 다른 형상을 만드는지 한눈에 비교 가능하게.

**캡션 초안:** "Fig. 1 | Planform geometry of the four prototypes. (a) Normalized chord distribution c/R vs. radial position r/R for 3D-SC, B1 (cicada-derived, solid) and B2, B3 (conventional, dashed). (b) Fifth-order polynomial coefficients defining leading/trailing edge curves. (c) Isometric CAD renderings of all four blades."

**데이터 출처:** 원논문[1] 공개 CAD/기하 데이터 — 신규 생성 불필요, 기존 파일에서 추출.

---

## Figure 2 — 대응 위치: §2.2 (Pressure drag, not induced drag, tracks the efficiency gap)

**패널 구성:**

- **(a) 표면 압력 분포 CFD 시각화:** 4개 프로토타입 각각의 blade 표면 압력 계수($C_p$) 컨투어맵(contour map), 동일 스케일/컬러바 사용. 저압 영역(박리 발생 가능 지점)이 3D-SC/B1에서 더 작거나 덜 두드러짐을 시각적으로 대비. Reviewer가 "압력항력이 왜 줄었는지"를 그림만 보고 이해할 수 있도록, 압력 회복(pressure recovery) 구간을 화살표/음영으로 강조.
- **(b) Wake 단면 유동 시각화:** 각 프로토타입의 wake 단면에서의 vorticity 또는 velocity-deficit 컨투어 — 유도항력 추정에 사용된 운동량 결손(momentum-deficit) 영역을 시각적으로 보여줌. 이 패널은 "유도항력이 그룹 간 차이가 없다"는 §2.2 주장의 시각적 근거.
- **(c) 항력 성분 막대그래프:** x축 = 4개 프로토타입, y축 = 항력계수($C_D$), 압력항력/유도항력/점성항력을 누적 막대(stacked bar)로 표시. 오차막대(error bar) 포함.
- **(d) 산점도 + 회귀선:** x축 = 압력항력 $C_{D,p}$ (또는 유도항력, 별도 서브패널), y축 = 추진효율 η. 4개 데이터점 + 선형회귀선 + $R^2$ 값 표기. 압력항력 대비 회귀와 유도항력 대비 회귀를 나란히 배치해 어느 쪽이 효율을 더 잘 설명하는지 시각적으로 대비.

**캡션 초안:** "Fig. 2 | Drag decomposition reveals a pressure-drag pathway to efficiency. (a) Surface pressure coefficient contours for all four prototypes. (b) Wake velocity-deficit contours used for induced-drag estimation. (c) Stacked drag-component bar chart per prototype. (d) Propulsive efficiency vs. pressure drag (left) and induced drag (right), with linear fits and R²."

**이 그림이 핵심인 이유:** [[FOL_followup_proposal]]의 8b(핵심 검증 가설)를 직접 뒷받침하는 유일한 그림. 이 그림 없이는 §2.2의 정량 주장이 텍스트로만 존재하게 되므로, 실제 논문 완성 시 최우선으로 제작해야 함.

---

## Figure 3 — 대응 위치: §2.3 (Pressure-drag reduction accounts for the efficiency gain) + Reynolds수 비교

**패널 구성:**

- **(a) 기여도 분해 막대그래프(waterfall chart):** 전체 효율 향상분(>20%)을 100%로 놓고, 압력항력 감소 기여분 vs 잔여(점성/추력분포 등) 기여분을 waterfall 또는 누적 막대로 시각화.
- **(b) RPM별 비교:** x축 = RPM(2000, 5000), y축 = 압력항력 감소율(%), 3D-SC와 B1 각각의 막대를 두 RPM 조건에 대해 나란히 배치 — "효율 메커니즘은 Re수에 무관하게 일정하다"는 주장(§2.3 마지막 문단)을 뒷받침. 이는 원논문[1]의 Fig.(Re수 조건별 소음 메커니즘 비교 그림)와 나란히 놓고 비교하도록 동일한 스타일로 제작 권장.

**캡션 초안:** "Fig. 3 | Pressure-drag reduction accounts for the propulsive-efficiency gain across Reynolds-number regimes. (a) Decomposition of the >20% efficiency gain into pressure-drag-attributable and residual contributions. (b) Pressure-drag reduction magnitude at 2000 RPM vs. 5000 RPM for 3D-SC and B1."

---

## Figure 4 — 대응 위치: §2.4 (Alternative mechanisms ruled out)

**패널 구성:**

- **(a) 2×2 비교 매트릭스:** 세로축 = {owl serration 있음/없음}, 가로축 = {cicada planform 있음/없음} — 즉 (3D-SC, B1, B2, B3 중 해당하는 조합)를 배치한 2×2 grid. 각 셀에 효율(η)과 압력항력($C_{D,p}$) 값을 함께 표기하는 heatmap 또는 라벨링된 산점도.
- **(b) B1 vs 3D-SC 직접 비교:** 두 프로토타입만 떼어놓고 압력항력·효율을 나란히 비교하는 막대그래프 + 유의성 검정 결과(p-value) 표기 — "CVS 메커니즘 없이도 B1이 비슷한 효율 향상을 보인다"는 핵심 대조 실험 결과를 한눈에.

**캡션 초안:** "Fig. 4 | The efficiency mechanism is independent of serration-driven vorticity. (a) 2×2 design matrix (serration × planform) showing pressure drag and efficiency for each combination. (b) Direct comparison of 3D-SC and B1: comparable pressure-drag reduction and efficiency gain despite B1 lacking owl-serration-driven CVS."

---

## 요약 표 — Figure ↔ 본문 대응

| Figure | 대응 섹션 | FOL 단계 | 핵심 메시지 |
|---|---|---|---|
| Fig. 1 | §2.1 | 8a | chord 재배치가 실제로 존재하는 구조적 차이임을 시각 확인 |
| Fig. 2 | §2.2 | 8b (핵심) | 압력항력만 감소, 유도항력은 불변 — 가설의 직접 증거 |
| Fig. 3 | §2.3 | 8c | 압력항력 감소가 효율 향상을 정량적으로 설명 |
| Fig. 4 | §2.4 | 8b 보강(교란변수 배제) | 세레이션 유무와 무관하게 효율 메커니즘 작동 |

## 관련 문서
- [[paper_draft.md]]
- [[FOL_followup_proposal]]
- [[paper_writing_skill]]
