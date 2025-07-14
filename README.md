# 🧳 여행자비스(여행자+Javis)

사용자가 입력한 텍스트와 사진을 기반으로, 해당 장소에 대한 정보를 자연어로 응답하는 모바일 웹 기반 AI 챗봇 서비스

---

## 📌 프로젝트 요약

- **프로젝트명**: 여행자비스
- **목표**:
  - 사진과 텍스트 기반으로 랜드마크를 인식하여 RAG(벡터 검색 + LLM 응답) 기반으로 정보를 제공 
  - 추가 질문에 대응하고 장소 또는 경로 링크를 안내
- **기술 스택**:
  - Product Design: `Figma`
  - Frontend: `React`
  - Backend: `Python - FastAPI`
  - DB: `Cloud DB for MySQL`, `Object Storage`, `Cloud DB for PostgreSQL - Pinecone`, 
  - API 연동: `Clova Studio`, `Naver Map URL`
  - Authorization: `Naver SSO`
  - DevOps: `NCP API Gateway`
  - Co-work: `Github Issues`, `Slack`, `Notion`
- **팀원 구성**:  
  - 이예승: 팀장 / BE(챗봇 API) / BE(멀티 모달 API) / DevOps / NCP Resources Monitoring
  - 김현욱: PM / 서비스기획 / FE / DB 설계
  - 박성국: BE(로그인 API) / BE(마이페이지 API) / BE (대화 리스트 API) / BE (대화 검색 API) / BE (대화 제목 생성 API)
  - 장은빈: AI(RAG 파이프라인 구축) / AI(벡터 DB 스키마 설계) / AI (LangChain 구성) / Security Engineer

---

## 🧠 기획 의도

- 여행 중 낯선 장소에서 현재 위치, 주변 볼거리, 이동 경로를 빠르게 알고 싶은 요구 사항 반영

- 여러 앱을 오가는 번거로움을 해결하고자, 사진 한 장과 간단한 질문만으로도 직관적인 안내를 제공하여 사용자 경험 개선

---

## 🛠 주요 기능 (Features)

| 기능 | 설명 |
|------|------|
| ✅ 멀티 모달 데이터 입력 | 이미지, 음성 등 비정형 데이터 전처리 및 후처리 |
| ✅ 장소 인식 및 설명 제공 | 사진과 질문 입력 시 장소 식별 → 벡터 DB 검색 → 설명 생성 |
| ✅ 추가 질의 응답 | 대화 맥락 유지 → 주변 장소, 카페 등 정보 추가 제공 |
| ✅ 경로 안내 임베드 | 채팅창 내 지도 렌더링 |
| ✅ 대화 제목 생성 | 대화 내용을 기반으로 자동 제목 생성 |
| ✅ 로그인 플로우 | 로그인 시작 → 네이버 SSO 로그인 → 콜백 → JWT 토큰 발행 및 사용자 정보 처리 → 액세스 토큰 만료 시 갱신|
| ✅ 로그아웃 | 세션 삭제 → 대화 내역 저장 →  토큰 폐기 |
| ✅ 마이페이지 | 사용자 정보 확인 및 수정 |
| ✅ 대화 목록 관리 | 사용자의 대화 목록을 리스트로 제공, 대화 제목 변경 및 삭제 기능 |
| ✅ 대화 검색 | 대화 제목이나 내용을 자연어 입력하여 쿼리 |

---

## 🏗️ Architecture

<img src="https://lh3.googleusercontent.com/d/1uPMXau3eDCw5JdEavclFnDd4-qZ4G83P?v=2" Width="840" alt="architecture" />

---
## 📷 결과 화면 예시
### ▶️ [Prototype-Figma](https://www.figma.com/proto/FgbknG9bV0edFVdfAFcR5C/%EC%97%AC%ED%96%89Javis?node-id=3202-3821&t=q6V6a2eRWWNmtjUV-1)

<table>
  <tr>
    <td align="center" valign="top">
      <b>🔐 Naver 소셜로그인</b><br/>
      <img src="https://lh3.googleusercontent.com/d/1HC3OShwdyFreZeqLXQbtmx_wo5zeiS47" Width="420" />
    </td>
    <td align="center" valign="top">
      <b>💬 초기 화면</b><br/>
      <img src="https://lh3.googleusercontent.com/d/1YkulZnvAcJqYUBhePDhAqfMkEv_ZPUiJ" width="420"/>
    </td>
  </tr>
  <tr>
    <td align="center" valign="top">
      <b>⌨️  여행 정보 질문 Typing 입력</b><br/>
      <img src="https://lh3.googleusercontent.com/d/1nEUXHaUnCgyQEmZA-cOt-_m53HIW1hgv" width="420"/>
    </td>
    <td align="center" valign="top">
      <b>🗺️ 여행 정보 응답 Text & Embedding</b><br/>
      <img src="https://lh3.googleusercontent.com/d/19JA_9IFnfrjoF-qErilry8nJ6cvJNFzt" width="420"/>
    </td>
  </tr>
  <tr>
    <td align="center" valign="top">
      <b>📸 멀티모달 - 이미지</b><br/>
      <img src="https://lh3.googleusercontent.com/d/14rLaoPRS6Uz4HbdYoxLuLNi--YnrV1WD" width="420"/>
    </td>
     <td align="center" valign="top">
      <b>🎙️ 멀티모달 - STT</b><br/>  
      <img src="https://lh3.googleusercontent.com/d/1zKz9nPX5Te4QbHx2K7jhy5e8vGnllWT3" width="420"/>
    </td>
  </tr>
  <tr>
    <td align="center" valign="top">
      <b>📚 대화 목록 관리</b><br/>
      <img src="https://lh3.googleusercontent.com/d/1_Ng97II31xuz0wYZskNOfvXDLCYEdjLy" width="420"/>
    </td>
     <td align="center" valign="top">
      <b>👤 마이페이지</b><br/>  
      <img src="https://lh3.googleusercontent.com/d/1zM8Xw7QU4xNJpFH8yHJLfRLMtIGY9wzJ" width="420"/>
    </td>
  </tr>
</table>

---

## ⚙️ 비기능 요건 (Non-Functional)

- 성능 최적화하여 1~2초 내에 응답
- AR, Graph RAG 등 고도화 대응 구조 고려
- 예외 대응 메시지 제공하여 안정성 확보 
- 모바일 웹 기반 직관적 UX 구현, 스마트폰에서도 별도 설치 없이 사용 가능 

---

## 🚀 추후 확장 계획

### Phase 2 (기능고도화)
| 항목 | 내용 | 기대 효과 |
|------|------|------|
| 🖇️ Graph RAG 도입 | 장소 간 관계성 학습 → 연관 응답 추천 | 유사 장소/컨텍스트 기반 질의 확대 |
| 🔠 텍스트 기반 인식 고도화 | CLOVA OCR 적용 | 이미지 내 텍스트 인식률 강화 |
| 💰 날씨 정보 연동 | 기상청 API 또는 OpenWeather API 연동 | 단기간 여행 일정/복장 판단 조언 |
| 📍 영업시간/혼잡도 안내 | 장소 기반 실시간 운영 정보 수집 (네이버, 카카오 API 등) | 실시간 현지 정보 파악 가능 |
<br />

### Phsae 3 (글로벌 개인화 여행 가이드 확장)
| 항목 | 내용 | 기대 효과 |
|------|------|------|
| 🌐 다국어 지원 | Clova Translation API 또는 Prompt 기반 언어 전환 | 외국인 관광객 대상 확장성 확보 |
| 🛫 해외 관광지 정보 연동 | Google Maps / Places API 활용 | 국내외 통합 여행 챗봇 가능 |
| 👀 AR 기반 위치 탐지 | 기상청 API 또는 OpenWeather API 연동 | 실시간 무인 안내 시스템 대체 |
| 🧭 일정 추천 & 경로 최적화 | 사용자 조건 기반 맞춤 루트 제안 | 개인화된 여행 플래너 기능 |

---
