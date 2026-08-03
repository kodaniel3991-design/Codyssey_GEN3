# 노코드 자동화 기초: 워크플로우 설계

코디세이 AI Native Basic · AI 도구 학습 (40시간) 과제 산출물

동일한 워크플로우를 두 개의 도구로 구현해 비교하고, 그 결론을 근거로 도구를 선정해 실무 자동화 파이프라인을 설계·구현했다.

---

## 산출물

| | 내용 | 열기 |
|---|---|---|
| **프로젝트 1** | 자동화 도구 비교 구현 (Make vs Zapier) | [발표 자료](https://kodaniel3991-design.github.io/Codyssey_GEN3/p1.html) · [비교 보고서](P1_report.md) |
| **프로젝트 2** | 블로그 초안 준비 자동화 (Make 단독) | [발표 자료](https://kodaniel3991-design.github.io/Codyssey_GEN3/p2.html) |

발표 자료는 좌우 방향키로 슬라이드를 넘길 수 있다.

---

## 프로젝트 1 — 자동화 도구 비교 구현

문의 접수 처리 워크플로우를 Make와 Zapier에 **동일한 구조**로 구현하고, 구현 과정에서 실제로 겪은 차이를 근거로 비교했다.

```
Trigger  Google Forms 응답 접수
   │
Router   문의 유형 분기 (솔루션 도입 상담 / 단순 문의)
   ├─ Google Sheets 기록 + Gmail 알림
   └─ Google Sheets 기록 + Gmail 알림 (문구 상이)
```

- Make 시나리오 `P1_문의접수_Make` — Router + 필터
- Zapier Zap `P1_문의접수_Zapier` — Paths

## 프로젝트 2 — 블로그 초안 준비 자동화

주제 한 줄을 시트에 적으면 초안 생성부터 검증·문서화·알림까지 자동으로 이어진다.

```
Trigger  Google Sheets · Watch New Rows       주제큐 탭
   │
Action   OpenAI gpt-4o-mini                   초안 생성       ← 보너스 1
   │
Router   초안 글자수 검증 (800자 기준)
   ├─ 정상  Google Docs 생성 → Gmail 검토 요청
   └─ 미달  재작업 탭 적재 → Gmail 경고        ← 보너스 2
```

분기 기준을 **AI 출력의 길이 검증**으로 잡아, 생성 결과를 그대로 믿지 않고 확인한 뒤 다음 단계로 넘기는 구조를 만들었다.

---

## 요건 대조

| 요건 | 구현 | |
|---|---|:-:|
| 도구 2개 이상 직접 사용 | Make · Zapier | ✅ |
| 동일 워크플로우 구조로 구현 | Trigger → 분기 → Sheets + Gmail | ✅ |
| 비교 항목 5개 이상 | `P1_report.md` | ✅ |
| Trigger 1 / Action 2+ / 조건 분기 1+ | 두 프로젝트 모두 충족 | ✅ |
| 각 분기 경로 1회 이상 실행 | 실행 로그 캡처로 증빙 | ✅ |
| 프로젝트 2 자동 실행 | Schedule 발화 로그 | ✅ |
| 보너스 1 — AI 연동 Action | OpenAI gpt-4o-mini | ✅ |
| 보너스 2 — 대체 경로 | 재작업 시트 + 경고 알림 | ✅ |
| 민감정보 비노출 | API 키 화면 미촬영 | ✅ |

---

## 파일 구성

```
p1.html             프로젝트 1 발표 자료
presentation.html   프로젝트 1 발표 자료 (연결 문서)
P1_report.md        프로젝트 1 비교 분석 보고서
p2.html             프로젝트 2 발표 자료
img/                프로젝트 1 캡처 이미지
```

프로젝트 2 발표 자료는 이미지를 파일 내부에 포함한 단일 HTML이라 별도 리소스가 없다.

---

이대흥 · 2026.08.03
