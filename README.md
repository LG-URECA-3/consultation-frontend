<div align="center">

# 🎧 LG U+ 프리톡  (Free-Talk with Pre-Talk) - 프론트엔드
**통신사 고객 상담사를 위한 실시간 상담 업무 지원 웹 애플리케이션**

![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-B73BFE?style=for-the-badge&logo=vite&logoColor=FFD62E)
![Zustand](https://img.shields.io/badge/Zustand-432211?style=for-the-badge&logo=zustand&logoColor=white)
![React Router](https://img.shields.io/badge/React_Router_v7-CA4245?style=for-the-badge&logo=react-router&logoColor=white)

<br/>

> *백엔드 서비스(`consultation-service`, `consultation-ai`)와 연동하여 실시간 대기열 관리, AI 기반 상담 지원, 통합 이력 검색 등 상담사에게 최적의 UI/UX를 제공합니다.*

</div>

<br/>

## 📖 프로젝트 개요 (Introduction)

**U+ 프리톡 프론트엔드**는 통신사 상담사가 고객 상담 업무 전 과정을 빠르고 직관적으로 처리할 수 있도록 지원하는 SPA(Single Page Application)입니다. 복잡한 상담 화면을 간결하게 구성하고, AI가 분석한 데이터를 적재적소에 배치하여 상담사의 인지 부하를 최소화하는 데 집중했습니다.

### 💡 핵심 가치
* ⏱️ **실시간 대기 현황 파악:** 대기 고객 목록 실시간 조회 및 다음 상담 즉시 배정
* 🤖 **AI 기반 상담 지원:** 고객 문의에 맞는 AI 추천 답변 및 사전 FAQ 즉시 제공
* 📊 **고객 성향 시각화:** 가격민감도, 결정스타일, 불안수준, 감정 기반 성향을 직관적인 UI로 표시
* 🔍 **통합 이력 검색:** Elasticsearch 연동 시맨틱 검색으로 유사 상담 사례 빠른 탐색
* ⚡ **업무 자동화 체감:** 상담 종료 시 AI가 자동 요약·키워드를 추출하여 기록 업무 제로화

---

## 🛠 기술 스택 (Tech Stack)

| 분류 | 기술 | 비고 |
| :--- | :--- | :--- |
| **Framework** | React 18+ | UI 컴포넌트 렌더링 |
| **Language** | TypeScript | 정적 타입 시스템으로 런타임 에러 방지 |
| **Build Tool** | Vite | 빠른 HMR 및 최적화된 빌드 환경 제공 |
| **Routing** | React Router v7 | 페이지 라우팅 및 네비게이션 |
| **State Mgt.** | Zustand | 가볍고 직관적인 전역 상태 관리 |
| **HTTP Client** | Axios | JWT 자동 갱신(Refresh) 인터셉터 구현 |
| **Auth** | @react-oauth/google | Google OAuth2 ID 토큰 기반 로그인 |
| **Icons** | Lucide React | 일관성 있는 벡터 아이콘 시스템 |

---

## ✨ 주요 기능 및 화면 (Features & Views)

### 🧑‍💻 상담사(Agent) 업무 공간
* **로그인 (`/`)**: Google OAuth2 소셜 로그인 지원 (시연용 모드를 통해 백엔드 없이 UI 테스트 가능)
* **대시보드 (`/dashboard`)**: 
  * 업무 상태 관리 (시작/잠시 멈춤/정지)
  * 실시간 대기열 및 오늘 성과(통계) 조회
  * 실시간 급상승 키워드(예: 5G 요금제, 결합할인) 및 팀 공지 확인
  * 🚨 실시간 장애 대응 가이드 제공
* **실시간 상담 (`/consultation/:customerId`)**: 
  * 마스킹된 고객 정보 및 최근 상담 내역 패널
  * 고객 성향 분석(신중형/즉흥형 등) 레이더 차트/지표 시각화
  * 실시간 채팅 및 AI 추천/종합 답변 제공
  * 클릭 한 번으로 상담 결과 분류 및 메모 후 종료
* **통합 이력 검색 (`/search`)**: 탭 기반 필터링(전체/나의상담/이관), 기간/키워드/시맨틱 검색 및 리포트 다운로드
* **상세 내역 (`/history/:historyId`)**: 특정 상담의 채팅 전문, AI 요약, 키워드 조회

### 📱 고객(Customer) 경험 채널
* **상담 신청 (`/customer/apply`)**: 고객 센터 진입 및 상담 접수
* **사전 FAQ (`/customer/qa`)**: 대기 중 자가 해결을 유도하는 챗봇/FAQ 화면
* **고객 채팅 (`/customer/chat`)**: 상담사와 연결되는 실시간 채팅 인터페이스
* **요약 확인 (`/customer/summary`)**: 상담 종료 후 제공되는 핵심 요약본

---

## 🏗 프로젝트 구조 (Directory Structure)

```text
consultation-frontend/
├── src/
│   ├── main.tsx               # 앱 진입점
│   ├── App.tsx                # 라우터 및 글로벌 레이아웃 설정
│   ├── pages/                 # 페이지 레벨 컴포넌트 (Dashboard, Consultation 등)
│   │   └── customer/          # 고객용 화면 컴포넌트 분리
│   ├── components/            # 도메인 독립적인 재사용 UI 컴포넌트
│   ├── store/                 # Zustand 전역 상태 보관소
│   ├── api/                   # Axios 인스턴스, 인터셉터 및 API 호출 함수
│   └── types/                 # TypeScript 인터페이스/타입 정의
├── dist/                      # 빌드 결과물 (Production)
├── .env.local                 # 로컬 환경 변수
└── vite.config.ts             # Vite 빌드 설정
```

---

## 🚀 실행 및 환경 설정 (Getting Started)

### 1. 사전 요구사항
* **Node.js**: v18 이상 권장
* **백엔드 실행**: 본 프론트엔드를 정상 구동하기 위해서는 `consultation-service` 및 `consultation-ai` 백엔드 서버가 띄워져 있어야 합니다.

### 2. 환경 변수 설정
프로젝트 루트 디렉토리에 `.env.local` 파일을 생성하고 아래와 같이 백엔드 연동 정보를 입력합니다. *(Vite 환경변수는 반드시 `VITE_` 접두사를 사용해야 합니다.)*

```env
# 백엔드 API 엔드포인트
VITE_API_BASE_URL=http://localhost:8081        # api-module (상담 핵심 로직)
VITE_ADMIN_BASE_URL=http://localhost:8082      # admin-module (백오피스 검색)
VITE_FASTAPI_BASE_URL=[http://127.0.0.1:8000](http://127.0.0.1:8000)    # consultation-ai (AI 시맨틱 검색)

# 인증 정보
VITE_BASIC_AUTH_USERNAME=your_basic_auth_username
VITE_BASIC_AUTH_PASSWORD=your_basic_auth_password
VITE_GOOGLE_CLIENT_ID=your_google_client_id.apps.googleusercontent.com
```

### 3. 설치 및 실행
```bash
# 1. 패키지 의존성 설치
$ npm install

# 2. 로컬 개발 서버 실행 (기본 포트: 5173)
$ npm run dev

# 3. 프로덕션 빌드 및 미리보기
$ npm run build
$ npm run preview
```

---

## 🔗 연동 백엔드 서비스 요약

본 프론트엔드는 다음 세 가지 주요 백엔드 모듈과 통신합니다.

| 서비스 모듈 | Port | 주요 연동 API 및 기능 |
| :--- | :--- | :--- |
| **`api-module`** | `8081` | Google OAuth 로그인(`/auth/google`), 토큰 갱신<br>상담 대기열 조회 및 매칭(`/consultations/waiting`)<br>채팅 메시지 전송 및 컨텍스트 로드 |
| **`admin-module`** | `8082` | 상담 이력 통합 검색 및 필터링(`/admin/v1/consultations`) |
| **`consultation-ai`** | `8000` | Elasticsearch 기반 상담 및 FAQ 시맨틱 검색(`/fastapi/v1/search/*`)<br>개별 상담 상세 이력 조회 |
