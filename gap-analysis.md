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
| 실제 Figure 부재 | Figure 1~4가 텍스트 placeholder만 존재, 실제 이미지 없음 (자세한 내용은 [[figure-descriptions]]) | 모든 Figure가 실제 데이터 기반 그림 | 이전 버전에서는 존재하지 않는 "Fig. 1a"를 인용하는 더 심각한 오류가 있었으나 현재는 placeholder로 명시해 완화됨 |

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
2. **(Critical)** 실제 Figure 1~4 제작 ([[figure-descriptions]] 명세 기준)
3. **(High)** Methods에 솔버/격자/경계조건 등 구체 스펙 추가
4. **(High)** n=4 표본 크기의 통계적 한계를 Discussion/Limitations에 명시
5. **(Medium)** Reporting Summary, Supplementary Information 섹션 신설 (실측 이후)
6. **(Low)** 저자 정보 및 행정 섹션 채우기

Critical/High 항목은 실측 데이터가 있어야만 해결 가능하므로, 그 전까지 이 문서는 "완결된 논문"이 아니라 **검증 계획서(pre-registration-style proposal)**로만 취급되어야 한다.

## 관련 문서
- [[paper_draft.md]]
- [[figure-descriptions]] — 이 문서에서 분리된, Figure placeholder들의 상세 명세
- [[FOL_followup_proposal]]
- [[paper_writing_skill]]
