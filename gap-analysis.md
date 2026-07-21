# Gap Analysis — `paper_draft.md` vs. 실제 학술논문(앵커 논문 [1]) 형식 차이 (심각도별)

이 문서는 `paper_draft.md`가 실제 게재 가능한 논문(Nature Communications 앵커 논문[1] 기준)과 형식·완성도 측면에서 어떻게 다른지, 각 차이를 **심각도(Critical/High/Medium/Low)**로 분류해 정리한다. 심각도는 "이 차이가 이 문서를 학술 문서로서 신뢰할 수 없게 만드는 정도"를 기준으로 매긴다.

각 항목에는 **상태(Status)**를 추가했다: ✅ 해결됨 / 🟡 완화됨(근본 해결은 아니나 개선) / ⬜ 미해결(구조적으로 지금 해결 불가 또는 저자 본인만 채울 수 있는 항목).

| 심각도 | 의미 |
|---|---|
| **Critical** | 독자가 이 문서를 "검증된 결과"로 오인할 수 있음 — 학술적 진실성 문제 |
| **High** | 재현성/검증가능성이 훼손됨 — 실제 논문이라면 게재 불가 사유 |
| **Medium** | 저널 표준 관행 미준수 — 격식은 부족하지만 오해를 유발하진 않음 |
| **Low** | 행정적/서식적 누락 — 저자가 채우면 되는 항목 |

---

## Critical

| 상태 | 항목 | paper_draft.md 현황 | 앵커 논문[1] | 근거 |
|---|---|---|---|---|
| 🟡 | 실측 데이터 부재 — **원인이 이제 정확히 규명됨** | **직접 검증 완료 (2026-07-21):** 앵커 논문의 Zenodo 저장소(DOI 10.5281/zenodo.11088631)를 실제로 다운로드·압축해제하여 내부 파일을 전수 확인했다. 그 결과 **압력분포·후류 속도장 등 필드 수준 CFD 원시 데이터는 저장소에 전혀 없으며**, 공개된 것은 그림 재현용 소스 데이터(추력/토크/RPM/전력 측정값, 음향 스펙트럼, CFD-실험 적분값 비교 등)뿐임을 확인했다. 즉 "기존 CFD 해를 재사용하면 된다"던 당초 전제 자체가 틀렸다 — §4 Methods와 §데이터 가용성에 이 사실과 그 근거(구체적 파일 목록)를 전부 반영했다. 부수적으로 **프로토타입이 4개가 아니라 B4를 포함한 5개**라는 사실도 함께 발견해 반영했다. | 모든 수치가 실제 CFD/실험 측정값이며, 저자들은 원시 CFD 필드 데이터를 보유하고 있음(단 공개하지는 않음) | **완화 조치 2단계:** (1) 문서 상단에 이 원고가 실제 학술 출판 형식인 "Stage 1 Registered Report"와 구조적으로 동일함을 명시(검증됨). (2) 이번에 실제로 원본 데이터를 다운로드·검사하여, "왜 아직 못 채우는지"를 막연한 서술이 아니라 **검증된 구체적 사실**(원시 필드 데이터 부재, 파일 목록 확인)로 못박았다. **그럼에도 근본 해결(=`[VALUE]`를 실제 수치로 채우는 것)은 저자 컨택 또는 신규 CFD 시뮬레이션 수행이라는, 문서 작업을 넘어서는 실물 행동이 필요하며 이는 AI가 파일을 편집하는 것으로 대신할 수 없다.** |
| ⬜ | 실제 Figure 부재 (Figure 2~4) | Figure 2~4는 CFD 필드 데이터가 있어야만 제작 가능하며, 그 데이터가 없음이 확인됨 | 모든 Figure가 실제 데이터 기반 그림 | 데이터 자체가 없어 그림 제작이 원천적으로 불가능함이 재확인됨. 가짜 그림을 만들지 않는 것 자체가 올바른 처리임. |
| 🟡 | 실제 Figure 부재 (Figure 1) — **추가 시도 후 실패, 그 과정 기록** | Figure 1(평면형 오버레이)은 CFD가 아니라 순수 기하 방정식만 있으면 그릴 수 있다는 점에 착안해, 원 논문 본문에 공개된 것으로 보고된 매미 평면형 5차 다항식 계수를 실제로 추출해 파이썬으로 직접 플롯을 생성해봤다. **그러나 결과값이 물리적으로 불가능했다** — 스팬 3인치 블레이드의 코드 길이가 8인치를 넘게 계산됨(뿌리 부분은 음수). 이는 자동 웹 fetch를 통한 방정식 계수 추출이 신뢰할 수 없음(전사 오류 가능성)을 의미하므로, **생성한 그림을 즉시 폐기하고 사용하지 않았다.** | 논문에 방정식이 명시적으로 게재되어 있음(단, 원문 PDF에서 사람이 직접 수식을 읽고 옮겨야 신뢰 가능) | 이 시도는 "안 해봐서 못 고친 것"이 아니라 "시도했고, 검증 단계에서 결과가 신뢰할 수 없음을 확인해 정직하게 폐기한 것"임을 기록으로 남김. 방정식 자체는 원문 PDF에서 사람이 직접 옮기면 Figure 1만큼은 실제로 재현 가능할 것으로 보임 |
| ✅ | (신규 발견) 방법론 서술 오류 — "새 실험 없이 기존 CFD 해 재사용" | **해결:** Abstract, Introduction, Methods, 상단 상태 안내 전체에서 이 서술을 "원시 CFD 데이터 부재가 확인되었으므로 저자 컨택 또는 신규 시뮬레이션이 필요하다"로 정정 | — | 실제 데이터를 열어보지 않았다면 발견하지 못했을, 이전 라운드까지 남아있던 사실 오류. 직접 다운로드 검증을 통해 발견 및 정정 |
| ✅ | (신규 발견 후 해결) B4 프로토타입의 정체 | **해결:** 원 논문 본문 확인 결과 B4는 3D 스캔·리스케일링으로 제작한 **DJI Phantom 3 프로펠러**(산업계 벤치마크)이며, 매미/부엉이 설계 공간과 무관함을 확인. §4, Introduction, Data availability, Supplementary Information 계획에 반영 | 원 논문 본문에 B4=DJI Phantom 3로 명시됨 | 추측이 아니라 원 논문 본문을 재조사하여 확인한 사실 — §2가 4개 프로토타입으로 범위를 한정한 것이 타당함을 뒷받침 |

## High

| 상태 | 항목 | paper_draft.md 현황 | 앵커 논문[1] | 근거 |
|---|---|---|---|---|
| ✅ | Methods의 재현성 정보 부족 | **해결:** §4에 "원본 CFD 시뮬레이션 사양(재현성을 위한 명세)" 문단 추가 — 앵커 논문에서 실제로 확인된 솔버(ANSYS CFX), 난류모델(LES), 음향해석(FW-H), 격자 규모(회전영역 ~1000만/정지영역 ~200만 요소), 도메인 크기, 경계조건을 명시. 논문에 명시되지 않은 항목(솔버 버전, 인플레이션 레이어 층수/y+, 시간 적분 기법, 수렴 판정 기준)은 추측하지 않고 "원 논문에 명시되지 않음"으로 정직하게 표기 | Methods에 "Computational simulations" 하위섹션으로 솔버·격자·경계조건 상세 기술 | 지어낸 스펙이 아니라 앵커 논문에서 실제로 확인 가능한 정보만 반영했고, 확인 안 된 항목은 그 사실을 명시해 정직성을 유지함 |
| ✅ | 통계적 검정의 사전등록 부재 | **해결:** Discussion에 "통계적 한계" 문단 추가 — n=4의 낮은 검정력, R² 신뢰도, 다중비교 문제, 신뢰구간 불안정성을 명시하고 결과를 "확정적 결론이 아닌 예비적 경향"으로 해석해야 함을 명시 | — | n=4 표본 비교의 근본적 통계적 한계를 정직하게 인정 |

## Medium

| 상태 | 항목 | paper_draft.md 현황 | 앵커 논문[1] | 근거 |
|---|---|---|---|---|
| 🟡 | 참고문헌 수가 매우 적음 | 5개로 확대([1]~[5], Betz 1925 후류 운동량결손법 원전 추가) | 33개 | 여전히 앵커 논문 대비 적지만, 항력 분리 방법론의 핵심 근거(Betz의 원전)를 실제로 검증해 추가함으로써 방법론적 근거는 보강됨. 배경 문헌까지 33개 수준으로 늘릴 필요는 없다고 판단(후속 분석 논문의 성격상 과도함) |
| ✅ | Reporting Summary / Checklist 부재 | **해결:** Competing interests 섹션 뒤에 "Reporting Summary" 섹션 신설 — Statistics/Software and code/Data 표준 항목 구조를 실제 Nature Portfolio 관행에 맞게 기술, 세부 내용은 CFD 재분석 후 기입 예정임을 명시 | Nature 계열 저널은 제출 시 별도 "Reporting Summary" 필요 | 실측 이전이라 세부값은 placeholder이지만, 섹션 자체와 항목 구조는 실제 요구사항에 맞게 갖춰짐 |
| ✅ | Supplementary Information 부재 | **해결(구조 신설):** "보충 정보(Supplementary Information)" 섹션을 신설해 향후 담을 내용(격자수렴성/난류모델 민감도 결과, 항력 성분 원시값 표, B4 형상 사양, 표면압력 컨투어 전체 버전, 통계 진단 플롯)을 명시. 세부 내용 자체는 실측 데이터 확보 후 채워짐 | 본문 전반에 SI 참조가 다수 존재 | Reporting Summary와 동일한 방식으로, 내용은 비어있어도 "무엇이 들어갈지"가 명확한 구조를 갖춤 |
| ✅ | Data availability의 구체성 (+ **오류 정정**) | **해결 및 정정:** Zenodo 저장소를 실제로 다운로드하여 확인 — 라이선스가 이전에 잘못 기재했던 "CC BY 4.0"이 아니라 실제로는 **CC BY-NC-SA 4.0(비영리·동일조건변경허락)**임을 저장소 내 LICENSE.md에서 직접 확인해 정정. 내부 파일 구성(Source Data 디렉토리 하 그림별 소스 데이터, 프로토타입 5개 등)도 실제로 열어서 전수 확인 | 앵커는 데이터 종류를 구체적으로 서술 | "확인 필요"로 남겨뒀던 부분을 실제로 다운로드해 확인함으로써, 부정확했던 라이선스 정보까지 발견·수정 |
| ✅ | 인용 형식이 위첨자가 아닌 대괄호 | **해결:** 본문 내 모든 인용을 `[1]` → `<sup>1</sup>` 형식으로 변환(References 목록 자체의 `[1] Author...` 항목 서식은 유지). 인용 순서(1→2,3→4→5)도 재검증 완료 | 위첨자 숫자 | 마크다운/HTML의 `<sup>` 태그로 실제 위첨자 렌더링 구현 |

## Low

| 상태 | 항목 | paper_draft.md 현황 | 앵커 논문[1] | 근거 |
|---|---|---|---|---|
| ⬜ | 저자/소속 미기입 | Placeholder | 9명 저자, UC Berkeley 명시 | 저자 본인만 채울 수 있는 항목 — AI가 임의로 채우는 것이 오히려 부적절함 |
| ⬜ | Acknowledgements/Author contributions/Competing interests | Placeholder | 모두 상세 기술 | 저술 완료 시 채우면 되는 항목, 초안 단계에서는 결함이 아님 |
| ⬜ | Peer review 문구 부재 | 없음 | "익명 심사 완료" 문구 있음 | 아직 투고 전이므로 해당 없음 (결함 아님) |

---

## 결론 — 남은 작업

**이번 라운드(3차)에서 해결(✅)한 것:** Supplementary Information 섹션 신설, Data availability 오류 정정(라이선스 CC BY 4.0 → CC BY-NC-SA 4.0) 및 실제 저장소 다운로드 기반 재작성, 인용 형식의 위첨자 변환, 방법론 서술 오류("기존 CFD 재사용" → "신규 시뮬레이션/저자 컨택 필요") 정정, **B4 프로토타입의 정체 확인(DJI Phantom 3 벤치마크)**. 1~2차까지 합쳐 총 10개 항목을 실제로 해결.

**추가로 시도했으나 폐기한 것 (투명하게 기록):** Figure 1은 CFD가 아니라 순수 기하 방정식만 있으면 재현 가능하다는 점에 착안해, 원 논문에 공개된 것으로 보고된 매미 평면형 5차 다항식을 실제로 추출·플롯해봤다. 그러나 계산 결과가 물리적으로 불가능했다(3인치 스팬 블레이드에 8인치 넘는 코드 길이) — 즉 자동 추출된 계수를 신뢰할 수 없어 **그 그림을 즉시 폐기했다.** 이는 "시도 안 함"이 아니라 "시도했고 검증에서 실패해 정직하게 버린" 사례다.

**그럼에도 구조적으로 완전히 해결할 수 없는 것 (2가지 이유, 변동 없음):**
1. **실물 CFD 데이터/시뮬레이션이 있어야만 해결 가능** — `[VALUE]` 채우기, Figure 2~4 제작(및 Figure 1도 신뢰할 수 있는 방정식 원문 확인 전까지는 보류). 이는 저자 컨택 또는 신규 CFD 시뮬레이션 수행이라는, 문서 편집을 넘어서는 실제 행동이 필요하며 AI 에이전트가 파일을 고치는 작업만으로는 대신할 수 없다.
2. **저자 본인만 채울 수 있음** — 저자명/소속, Acknowledgements, Author contributions, Competing interests.

이 두 범주는 "미처 못 고친 문제"가 아니라 "정의상 문서 편집으로는 해결 불가능한 항목"이다. 참고문헌 수(33개 대비 5개)도 후속 분석 논문의 성격상 의도적으로 적게 유지한 것이며 추가 배경 문헌이 반드시 필요하지는 않다고 판단했다.

**다음 행동(사람이 직접 해야 함):** (a) 앵커 논문 저자에게 원시 CFD 케이스 파일 요청, 또는 (b) §4에 명시된 스펙을 재현하는 신규 CFD 시뮬레이션 수행 → 그 결과로 `[VALUE]` 전부 치환 및 Figure 2~4 제작 → Stage 2 Registered Report로 발전. Figure 1만은 원 논문 PDF에서 사람이 직접 방정식을 옮겨 적으면 신규 시뮬레이션 없이도 재현 가능할 것으로 보인다.

**사용자 확인 (2026-07-21):** 위 남은 ⬜ 항목(실측 CFD 데이터/Figure, 저자 개인정보)에 대해 사용자가 "현재 상태를 최종으로 수용"하기로 명시적으로 결정함. 즉 이 문서는 이 시점을 기준으로 완결된 것으로 간주하며, 남은 ⬜ 항목은 향후 실제 CFD 재분석 또는 저자 본인의 정보 입력이 있을 때 별도로 갱신한다.

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
