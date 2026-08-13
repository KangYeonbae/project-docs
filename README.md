# 강연배 — 프로젝트 엔지니어링 문서

AI·백엔드·제품 영역에서 만든 **19개 프로젝트의 설계 기록**입니다. 각 프로젝트가 어떤 문제에서 출발했고, 어떤 구조로 풀었으며, 무엇을 고르지 않았는지를 문서로 남겼습니다.

**이 저장소에는 코드가 없습니다.** 실무 프로젝트의 코드는 회사와 클라이언트 자산이고, 개인 제품의 코드는 별도 저장소에 있습니다. 여기에 있는 것은 그 위에서 내린 판단의 기록입니다.

- 직접 만든 서비스: [byeoljari.com](https://byeoljari.com) · [bid-master.co.kr](https://bid-master.co.kr) · [snap-p.com](https://snap-p.com/)
- 웹 포트폴리오: [kangyeonbae.dev](https://kangyeonbae.dev)
- 연락처: dusqo7951@gmail.com · [GitHub](https://github.com/KangYeonbae) · [LinkedIn](https://linkedin.com/in/yeonbae-kang-973436334)

---

## 어디부터 읽으면 되나요

| 목적 | 추천 문서 |
|---|---|
| **10분 안에 파악하고 싶다** | [Amazon Ads Reporting Agent](projects/amazon-ads-agent/) → [Bid Master](projects/bid-master/) → [Byeoljari](projects/byeoljari/) 의 각 README |
| **설계 판단의 깊이를 보고 싶다** | 위 세 프로젝트의 `decisions.md` |
| **장애 대응·협업 방식을 보고 싶다** | 위 세 프로젝트의 `operations.md` |
| **기술 폭을 보고 싶다** | 아래 전체 목록 |
| **일하는 방식이 궁금하다** | [엔지니어링 원칙](docs/engineering-principles.md) |

문서 표기 규칙과 비공개 처리 기준은 [문서를 읽는 법](docs/how-to-read.md)에 정리했습니다.

---

## 대표 프로젝트

가장 오래 붙잡았고, 운영까지 책임진 세 가지입니다. 네 개 문서(개요·구조·판단·운영)를 모두 갖췄습니다.

### [Amazon Ads Reporting Agent](projects/amazon-ads-agent/)
`2025.10 — 2026.05` · 실무 · 운영 중 · 단독 개발

광고·매출 데이터를 매일 수집해 근거 기반 리포트를 자동 생성합니다. **리포트를 쓰는 LLM과 그 숫자를 검증하는 Python을 분리한 것**이 핵심입니다. 누적 1억 3,500만 행을 적재하는 멀티테넌트 시스템으로 운영 중입니다. 구축 사례가 [동아일보 경제면](https://www.donga.com/news/Economy/article/all/20260622/134158095/1)에 보도됐습니다.

`Google ADK` `Gemini` `BigQuery` `Cloud Tasks` `Amazon SP-API`

### [Bid Master](projects/bid-master/)
`2025.11 — 2025.12` · 실무 · 운영 중 · 단독 개발

학교급식 입찰 공고를 수집해 품목·수익성을 판별하고 알려줍니다. **여러 사이트를 긁는 대신 폐쇄형 조달 시스템 한 곳을 API 레벨까지 역설계했습니다.** 엑셀로 3~4시간 걸리던 공고 검토가 30분 내외로 줄었습니다.

`FastAPI` `SQLAlchemy` `PostgreSQL` `Next.js` `Cloud Run Job` `Gemini`

### [Byeoljari.com](projects/byeoljari/)
`2026.03 — 운영 중` · 개인 제품 · 실결제 운영 · 단독 개발

사주·점성술 계산과 AI 해석, 결제를 하나의 여정으로 묶은 유료 B2C 서비스입니다. **성공 기준을 '결제 완료'가 아니라 '결제한 사람이 결과를 받는 것'으로 정의**하고 그에 맞춰 아키텍처를 짰습니다. 사업자 등록과 PG 계약까지 직접 진행했습니다.

`Next.js 16` `React 19` `FastAPI` `Supabase` `PortOne V2` `Gemini`

---

## 실무 프로젝트

재직 중 또는 클라이언트 요청으로 만든 것들입니다. 코드는 공개할 수 없어 설계 판단과 기여 범위만 기록했습니다.

| 프로젝트 | 기간 | 한 줄 요약 | 주요 스택 |
|---|---|---|---|
| [BigQuery AI Analyst](projects/text-to-sql/) | 2025.11 — 2026.01 | 자연어 질문을 SQL로 만들고 안전 검사·실행·복구·해석까지 연결 | ADK · LangGraph · BigQuery · RAG |
| [VOC Counseling Analyzer](projects/voc-analyzer/) | 2025.08 · 2026.05 확장 | 상담 데이터를 요약·분류해 리포트로 연결한 운영 자동화 | OpenAI · Streamlit · PyInstaller |
| [Review Sentiment Classifier](projects/review-classifier/) | 2025.09 | 반복 분류를 LLM에서 경량 자체 모델로 교체 | scikit-learn · Linear SVM · Flask |
| [Local Browser Agent](projects/local-browser-agent/) | 2025.10 | 고객 화면을 외부 API로 보내지 않는 로컬 자율 브라우저 에이전트 | Ollama · Qwen2.5 · LLaVA · Playwright |
| [Snap-p](projects/snap-p/) | 2026.03 — 2026.04 | 상품 정보 하나로 리스팅 이미지 9장·카피·정책 검수까지 | Gemini · Next.js 16 · Prisma |
| [Multilingual Blog CMS](projects/multilingual-cms/) | 2026.06 — 2026.07 | 언어별 초안·검수·발행 상태를 독립 관리하는 콘텐츠 도구 | Next.js · Tiptap · Prisma |
| [GA4 Event Validator](projects/ga4-validator/) | 2025.09 | 사용자 플로우를 자동 탐색하며 계측 이벤트를 검증 | Playwright · AsyncIO · GA4 |
| [Instagram Purchase-intent Analyzer](projects/instagram-insight/) | 2025.07 — 2025.08 | 댓글에서 단순 반응과 구매 의도를 구분 | Selenium · KcBERT · FastAPI |
| [Digital Signage DID CMS](projects/did-cms/) | 2025.05 — 2025.07 | 폐쇄망에서 콘텐츠·스케줄·단말 상태를 관리 | FastAPI · MinIO · MQTT |

## 개인 제품

기획부터 배포·운영까지 직접 한 제품입니다.

| 프로젝트 | 기간 | 한 줄 요약 | 주요 스택 |
|---|---|---|---|
| [MeetSub](projects/meetsub/) | 2026.08 — 현재 | 실시간 번역 자막부터 회의 기록·요약 PDF까지 한 세션으로 | Deepgram · Gemini · WebSocket · Cloud Run |
| [Exam Forge](projects/exam-forge/) | 2026.08 — 현재 | 수치를 바꾸면 선택지·정답·도형이 함께 바뀌는 수학 문항 생성기 | Next.js · TikZ · KaTeX · PWA |
| [Dubby](projects/dubby/) | 2026.07 — 현재 | 채팅·스토리·투표·서버 권위형 게임을 한 앱에 | Flutter · Firebase · Cloud Functions |

## 기술 실험 (Lab)

가설을 확인하려고 만든 것들입니다. 제품화보다 구조 검증이 목적이었습니다.

| 프로젝트 | 기간 | 확인하려던 것 | 주요 스택 |
|---|---|---|---|
| [SNS EasyUp](projects/sns-easyup/) | 2026.07 — 현재 | 아이디어에서 채널별 발행까지 한 흐름으로 묶을 수 있는가 | Meta API · Next.js · Cron |
| [Cloud Run Monitor](projects/cloudrun-monitor/) | 2026.04 — 현재 | 서비스 계정 키 없이 사용자 권한만으로 관측이 되는가 | GCP · OAuth · Cloud Logging |

## 학습기 팀 프로젝트

교육 과정에서 팀으로 만든 것들입니다. 기여 범위를 그대로 적었습니다.

| 프로젝트 | 기간 | 한 줄 요약 | 기여 |
|---|---|---|---|
| [Echo Recycle Hub](projects/echo-recycle-hub/) | 2023 — 2024 | 폐기물 이미지 분류를 배출 안내·챗봇·음성 상담까지 연결 | Architecture · Backend · ML / 50% |
| [SpacePlace.store](projects/spaceplace/) | 2023 — 2024 | 공간 검색·예약을 마이크로서비스로 분리한 대여 플랫폼 | Frontend · API / 35% |

---

## 경력

| 기간 | 소속 | 역할 |
|---|---|---|
| 2025.07 — 현재 | Hurdlers | AI Engineer — 광고·커머스·VOC를 위한 AI 제품과 운영 자동화 |
| 2025.03 — 2025.07 | Mooker | Backend Lead — 폐쇄망 DID CMS 백엔드와 미디어 아키텍처 |
| 2023 — 2024 | Codelab · SeSac | 클라우드·AICC·백엔드 집중 과정, 최우수 프로젝트 |
| 2012 — 2016 | 용인송담대학교 | 실내건축·에너지 |
