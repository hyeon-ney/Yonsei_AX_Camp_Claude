# Paper Writing Skill — 앵커 논문(Nature Comm.) 구조 복제 가이드

**앵커 논문:** Towards silent and efficient flight by combining bioinspired owl feather serrations with cicada wing geometry (Nature Communications, 2024, DOI: 10.1038/s41467-024-48454-3)

**목적:** 앵커 논문과 동일한 섹션 구조·서술 패턴을 따르되, [[FOL_nature_paper]]에서 지적된 8단계(A8) 취약점을 [[FOL_followup_proposal]]의 압력항력(pressure drag) 가설로 채우는 후속 논문을 작성한다.

---

## 0. 사전 체크 — 이 스킬을 쓰기 전에 확정할 것

- [ ] 검증할 핵심 가설 1문장으로 확정 (예: "3D-SC/B1의 효율 향상은 chord 재배치에 의한 압력항력 감소가 원인이다")
- [ ] 사용할 데이터: 원논문 공개 CFD 결과(3D-SC, B1, B2, B3) 재분석 — 신규 실험 없음
- [ ] FOL에서 어느 단계(A8b)를 검증 대상으로 삼는지 명시

---

## 1. 전체 섹션 구조 (앵커 논문과 1:1 대응)

| # | 섹션 | 앵커 논문에서의 역할 | 이 논문에서 채울 내용 |
|---|------|---------------------|----------------------|
| 1 | Title | 메커니즘 + 결과를 압축 (동사형: "~ suppress/enable ~") | "Pressure-drag reduction, not induced-drag, explains the propulsive efficiency gain of cicada-inspired chord redistribution" 형태 |
| 2 | Abstract | 배경→gap→방법→정량결과→결론 5문장 구조 | 아래 §2 템플릿 사용 |
| 3 | Introduction | (a) 생체모방 배경 (b) 기존 한계 (c) 이 논문이 메우는 gap | 앵커 논문의 A8을 gap으로 명시 인용 |
| 4 | Results | 메커니즘별 하위 섹션 (구조→물리량→정량 결과) | §3 참고 |
| 5 | Discussion | 함의 + 한계 + 후속 방향 | 8b 기각 시 대안 메커니즘 언급 |
| 6 | Methods | CFD 셋업, 항력 분리 방법론 | §4 참고 |
| 7 | Data availability | 원논문 CFD 데이터 재사용 명시 | 원논문 인용 + 재분석 코드 |

---

## 2. Abstract 템플릿 (앵커 논문 패턴 모사)

앵커 논문 Abstract 패턴: **[생물학적 배경] → [기존 접근의 한계] → [이 연구의 통합/방법] → [정량 결과] → [함의]**

```
[owl serration + cicada geometry를 결합한 하이브리드 프로펠러가 정숙성과
추진 효율을 동시에 달성한다는 것이 최근 보고되었다.] (배경, 앵커 논문 인용)

[그러나 효율 향상의 유체역학적 기원(압력항력 감소 vs 유도항력 감소 vs 기타)은
가설로만 제시되었고 직접 검증되지 않았다.] (gap = A8 취약점)

[본 연구는 원논문이 공개한 4개 프로토타입(3D-SC, B1, B2, B3)의 CFD 결과에서
항력을 압력항력과 점성/유도항력 성분으로 분리 재계산하여 이 가설을 정량적으로
검증한다.] (방법)

[그 결과 3D-SC/B1의 효율 향상 중 X%가 압력항력 감소로 설명되며, 이는 매미
평면형의 chord 재배치가 유발하는 [구체적 유동 현상]에 기인함을 보인다.] (결과)

[이는 세레이션(소음)과 평면형(효율)이 독립적으로 작동하는 메커니즘임을
확인하며, 향후 두 설계 변수의 독립적 최적화를 가능케 한다.] (함의)
```

---

## 3. Results 섹션 구조 (FOL 8a→8b→8c를 하위 섹션으로 1:1 매핑)

앵커 논문은 "구조 소개 → 메커니즘 시각화(CFD/유동장) → 정량 지표(dB, %) → 조건별(Re수) 비교" 순서로 서술한다. 동일 패턴 사용:

### 3.1 "Chord redistribution alters the drag decomposition" (↔ FOL 8a)
- 4개 프로토타입의 chord 분포 함수(5차 다항식 계수) 비교
- 그림: planform 형상 오버레이

### 3.2 "Pressure drag, not induced drag, drives the efficiency gap" (↔ FOL 8b, 핵심 검증)
- CFD 항력 분리 방법론 결과: 프로토타입별 압력항력 vs 유도항력 비율
- 정량 표: (프로토타입) × (전체 항력, 압력항력, 유도항력, 효율 %)
- 통계적 유의성 (프로토타입 간 압력항력 차이가 효율 차이를 설명하는 회귀/상관)

### 3.3 "Pressure drag reduction accounts for the propulsive efficiency gain" (↔ FOL 8c)
- 압력항력 감소분 → 전체 효율 향상분(20%+)에 대한 기여율 계산
- 앵커 논문의 Re수별 비교 패턴처럼, 회전수(RPM)별로도 이 관계가 유지되는지 확인

### 3.4 (선택) "Alternative mechanisms ruled out"
- InducedDragUnchanged(x) 대조 확인 — 앵커 논문처럼 "이것 때문이 아니다"를 명시하는 섹션 포함하면 반증가능성이 강화됨

---

## 4. Methods 템플릿

- **데이터 출처:** 원논문(Nature Comm. 2024) 공개 CFD 데이터셋, 4개 프로토타입(3D-SC, B1, B2, B3)
- **항력 분리 절차:** 표면 압력 적분 vs 벽면 전단응력 적분으로 압력항력/점성항력 분리; 유도항력은 wake 운동량 결손법으로 별도 계산
- **재현성:** 원논문 CFD 솔버/격자/경계조건 동일 사용 (신규 시뮬레이션 아님, 사후 재계산)
- **검증 기준:** [[FOL_followup_proposal]] §검증 설계에 명시된 예측/반증 조건 그대로 사용

---

## 5. Discussion 체크리스트 (앵커 논문 톤 유지)

- [ ] 가설이 지지됐는지/기각됐는지 명확히 서술 (애매하게 얼버무리지 않기)
- [ ] 지지된 경우: 소음 메커니즘(세레이션)과 효율 메커니즘(평면형)이 **독립적**임을 강조 → 두 설계 변수를 따로 최적화 가능하다는 실용적 함의
- [ ] 기각된 경우: A8b 대신 검토해야 할 대안 메커니즘 제시 (유효 캠버, 경계층 박리 지연 등) — 즉 다음 FOL 반복으로 연결
- [ ] 한계: 사후 재분석이라 원 실험이 이 가설을 검증하도록 설계되지 않았다는 점 명시

---

## 6. 문체·구성 체크리스트 (앵커 논문과 "구조가 비슷하다"고 느끼게 하는 요소)

- [ ] 각 Results 소제목이 **주장문(claim sentence)** 형태 ("X causes Y", 앵커 논문도 이 패턴)
- [ ] 정량 결과는 항상 "숫자 + 비교 대상(benchmark/타 프로토타입)" 쌍으로 제시
- [ ] 메커니즘 설명 시 항상 "구조적 원인 → 유동학적 중간변수 → 성능 지표" 3단 서술 순서 유지 (FOL의 8a→8b→8c와 동일 리듬)
- [ ] Figure 구성: (a) 형상/개념도 (b) 유동장/CFD 시각화 (c) 정량 막대/산점도 — 앵커 논문의 그림 패턴과 동일하게

---

## 관련 문서
- [[FOL_nature_paper]] — 앵커 논문의 10단계 FOL, 8단계 취약점 진단
- [[FOL_followup_proposal]] — 이 논문이 검증하려는 8a/8b/8c 가설 및 검증 설계
