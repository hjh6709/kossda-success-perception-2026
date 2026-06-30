# 노력하면 성공할 수 있을까?

> 자산 격차 시대, 한국인이 생각하는 성공 공식은 어떻게 바뀌었나

KOSSDA 대학생 데이터 시각화 공모전 2026 제출을 위한 분석 저장소입니다.  
핵심 주장은 다음 한 문장으로 정리됩니다.

**한국인은 노력을 버린 것이 아니라, 성공을 노력 하나만으로 설명하지 않게 되었다.**

## 1. 연구 질문

한국 사회에서 성공하려면 여전히 `열심히 일하는 것`이 중요하다고 인식되는가?  
아니면 가족 배경, 부모 교육, 관계 자본 같은 조건도 성공 공식의 일부로 함께 인식되고 있는가?

이 프로젝트는 “한국인이 노력을 포기했다”는 주장을 검증하지 않습니다. 대신 KGSS 자료를 중심으로, 한국인이 성공의 조건을 어떻게 이해하는지 살펴봅니다.

## 2. 데이터 구성

### 메인 데이터: KGSS 2003-2025 누적자료

- 자료명: 한국종합사회조사, 2003-2025 누적자료
- 영문명: Korean General Social Survey, 2003-2025 Cumulative File
- 자료번호: A1-CUM-0074
- 제공기관: 한국사회과학자료원 KOSSDA
- 연구수행기관: 성균관대학교 서베이리서치센터 SRC
- 활용 목적: 한국인의 성공 요인 인식 분석
- 주요 변수:
  - `SUCDEFRT`: 열심히 일
  - `SUCDWLTH`: 부유한 집안
  - `SUCDPAED`: 부모 교육
  - `SUCDKNOW`: 좋은 사람을 아는 것
  - `KIDSOL06`: 자녀 세대 생활수준 전망
  - `YEAR`, `AGE`, `FINALWT`

### 보조 데이터: 가계금융복지조사

KGSS 인식 분석의 경제적 배경을 설명하기 위해 통계청 가계금융복지조사를 보조 자료로 사용했습니다.

- 2025년 가계금융복지조사 부록 통계표
  - 소득 5분위와 순자산 5분위 격차
  - 연령대별 소득·순자산 비교
- MDIS 가계금융복지조사 2025 가구마스터
  - 같은 가구 안에서 소득 분위와 순자산 분위가 어떻게 겹치는지 확인

단, 가계금융복지조사는 본 프로젝트의 메인 근거가 아니라 경제적 배경을 보완하는 자료입니다.

## 3. 주요 분석 결과

- 2025년 KGSS 기준, 성공 요인으로 `열심히 일`을 중요하다고 답한 비율은 98.6%입니다.
- 같은 해 `좋은 사람을 아는 것`은 98.4%, `부유한 집안`은 91.0%, `부모 교육`은 87.5%입니다.
- 노력의 중요성은 사라지지 않았습니다. 다만 2009년 이후 배경·관계 조건의 중요도 인식이 크게 올라왔습니다.
- 2025년 연령대별 차이는 주로 `부유한 집안` 항목에서 확인됩니다.
- 가계금융복지조사 기준, 소득 격차보다 순자산 격차가 훨씬 크게 나타납니다. 다만 순자산은 연령과 생애주기 효과가 섞여 있으므로 개인 노력 차이로 해석하지 않습니다.

## 4. 해석 원칙

이 저장소의 분석은 다음 표현을 피합니다.

- “한국인은 노력을 믿지 않는다.”
- “부모 배경이 노력보다 중요해졌다.”
- “자산 격차가 성공 인식 변화를 일으켰다.”
- “순자산 격차는 곧 개인 노력의 차이다.”

대신 다음처럼 해석합니다.

- 노력은 여전히 거의 보편적으로 중요한 성공 요인으로 인식된다.
- 동시에 배경·관계 조건도 성공의 일부로 강하게 인식되고 있다.
- 경제 분석은 인식 변화를 설명하는 인과 근거가 아니라, 그 인식이 놓인 사회경제적 배경이다.

## 5. 저장소 구조

```text
.
├── docs/
│   ├── project_plan.md
│   ├── ppt_logic_audit.md
│   ├── ppt_research_design_methods.md
│   └── mdis_household_finance_microdata_guide.md
├── notebooks/
│   ├── 01_kgss_variable_check.ipynb
│   ├── 02_kgss_success_perception_analysis.ipynb
│   ├── 03_household_finance_context.ipynb
│   ├── 04_household_finance_microdata_analysis.ipynb
│   └── 05_statistical_validation_and_research_context.ipynb
├── outputs/
│   ├── figures/
│   ├── tables/
│   └── ppt/
├── data/
│   └── raw/        # 원자료 저장 위치, Git 제외
└── requirements.txt
```

## 6. 노트북 실행 순서

1. `notebooks/01_kgss_variable_check.ipynb`
   - KGSS 변수 존재 여부와 분석 가능 연도 확인
2. `notebooks/02_kgss_success_perception_analysis.ipynb`
   - 성공 요인별 중요 응답 비율, 시계열, 연령대별 비교
3. `notebooks/03_household_finance_context.ipynb`
   - 가계금융복지조사 부록 통계표 기반 경제적 배경 분석
4. `notebooks/04_household_finance_microdata_analysis.ipynb`
   - MDIS 2025 가구마스터 기반 소득·순자산 분위 교차 분석
5. `notebooks/05_statistical_validation_and_research_context.ipynb`
   - 카이제곱 검정, 추세 검정, 선행연구·방법론 정리

## 7. 주요 산출물

- 최종 PPT 초안: `outputs/ppt/kossda_success_perception_draft.pptx`
- 주요 그래프: `outputs/figures/`
- 집계 결과표: `outputs/tables/`
- 프로젝트 기획서: `docs/project_plan.md`
- PPT 논리 점검: `docs/ppt_logic_audit.md`
- 분석 방법 정리: `docs/ppt_research_design_methods.md`

## 8. 실행 환경

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

필요 패키지는 `pandas`, `numpy`, `matplotlib`, `pyreadstat`, `jupyter`, `openpyxl`입니다.

## 9. 원자료 주의

원자료는 공개 저장소에 포함하지 않습니다.  
다음 경로는 `.gitignore`로 제외되어 있습니다.

- `data/raw/`
- `data/processed/`
- `data/external/`
- `*.sav`, `*.xlsx`, `*.xls`, `*.csv`

단, `outputs/tables/*.csv`는 개인·가구 단위 원자료가 아니라 분석 결과 집계표이므로 저장소에 포함합니다.

## 10. 현재 제출물 기준

공모전 제출 요건에 맞춰 PPT는 표지와 참고문헌을 제외한 10장 구성으로 설계했습니다.  
요약문은 PPT의 보조 설명용으로 작성하며, PPT에 없는 새로운 내용은 포함하지 않는 것을 원칙으로 합니다.
