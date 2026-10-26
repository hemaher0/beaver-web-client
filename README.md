# 비버.ai 웹 클라이언트

## 프로젝트 소개

비버.ai는 소매업자가 데이터를 업로드하고 자연어로 질문해 분석 결과를 확인하는 팀 프로젝트입니다. 이 저장소는 웹 클라이언트의 개인 포크입니다. 분석과 답변 생성은 서버에서 처리하고, 클라이언트는 파일 업로드, 채팅, 문서·테이블 조회, 요약과 차트 표시를 담당합니다.

- 개발 기간: 2023.09.26~2024.02.27
- 팀 저장소: [beaver-web-client](https://github.com/inha-carbon-neutral-seven/beaver-web-client)

## 팀원 구성 및 역할 분담

|                                                                 **서강문**                                                                  |                                                                  **백범성**                                                                  |                                                               **최승혁**                                                                |                                                              **강민우**                                                              |                                                                 **최보근**                                                                  |
| :-----------------------------------------------------------------------------------------------------------------------------------------: | :------------------------------------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------------------------------------------: | :-----------------------------------------------------------------------------------------------------------------------------------------: |
| [<img src="https://avatars.githubusercontent.com/u/100016044?v=4" height=150 width=150> <br/> @KangmoonSeo](https://github.com/KangmoonSeo) | [<img src="https://avatars.githubusercontent.com/u/80192345?v=4" height=150 width=150> <br/> @highcloud100](https://github.com/highcloud100) | [<img src="https://avatars.githubusercontent.com/u/117180508?v=4" height=150 width=150> <br/> @ColdTbrew](https://github.com/ColdTbrew) | [<img src="https://avatars.githubusercontent.com/u/69228100?v=4" height=150 width=150> <br/> @hemaher0](https://github.com/hemaher0) | [<img src="https://avatars.githubusercontent.com/u/136104922?v=4" height=150 width=150> <br/> @ChoiBoKeun1](https://github.com/ChoiBoKeun1) |
|                                  팀장<br/> 웹 서버 개발 </br> LLM 결합 로직 개발</br> 모델 서버 관리 </br>                                  |                                       웹 개발 환경 구축</br> 개발 CI/CD 관리 </br> 모델 서버 및 최적화                                       |                                     오픈 소스 모델 평가<br> LLM 로직 개발 지원 </br> 모델 서버 관리                                     |                       클라이언트 개발 </br> 대시보드 기획 </br> 대시보드 인터페이스 제작</br> 형태소 분석 기획                       |                                  클라이언트 개발</br> 클라이언트 프로젝트 관리 </br> 채팅 인터페이스 제작                                   |

### 프론트엔드 기여 구분

- **강민우 (@hemaher0)**: 대시보드 기획과 인터페이스 개발을 담당했습니다. 서버에서 받은 차트 데이터를 Redux 상태와 대시보드 사이드바에 연결했고([f584c5b](https://github.com/hemaher0/beaver-web-client/commit/f584c5b8824d20fd6ce48c17461be6f12fed73d9)), 기존 코드·출력 표시 UI의 레이아웃과 스크롤 처리를 수정했습니다([0b18980](https://github.com/hemaher0/beaver-web-client/commit/0b18980260b1e07185c8d3213e238eb817ab8ee2)).
- **최보근 (@ChoiBoKeun1)**: 채팅 인터페이스와 클라이언트 프로젝트 관리를 담당했습니다. 답변의 코드와 출력을 보여주는 `MessageSource` 컴포넌트를 처음 추가했습니다([2503d06](https://github.com/hemaher0/beaver-web-client/commit/2503d060d1d0f59c678d719969acb5d99c784c4e)).

## 서비스 아키텍처

<img src="https://raw.githubusercontent.com/inha-carbon-neutral-seven/beaver-web-client/38a00bd4a568ac22022d60abc8eee145ee76b663/src/image/Architecture.png"/>

## 프론트엔드 개발 환경

- HTML, [React](https://react.dev/): 화면과 컴포넌트 구성
- Redux: 채팅, 업로드 파일, 분석 결과 및 서버 연결 상태 공유
- [Tailwind CSS](https://tailwindcss.com/): 화면 스타일과 다크 모드
- [FontAwesome](https://fontawesome.com/): 아이콘
- [ApexCharts.js](https://apexcharts.com/): 서버에서 받은 차트 데이터 표시
- [MUI X Data Grid](https://mui.com/x/react-data-grid/): CSV 테이블 표시와 필터링
- [React DocViewer](https://www.npmjs.com/package/@cyntler/react-doc-viewer): 업로드한 문서 표시

## 코드 구현

[코드 설명](https://github.com/inha-carbon-neutral-seven/beaver-web-client/wiki/%EC%BD%94%EB%93%9C-%EA%B5%AC%ED%98%84-%EC%9D%98%EB%8F%84-%EB%B0%8F-%EC%A0%95%EB%A6%AC)

## 클라이언트 실행 방법

1. 레포지토리를 로컬 시스템으로 복제합니다.

```bash
git clone https://github.com/inha-carbon-neutral-seven/beaver-web-client.git
```

2. 프로젝트 디렉토리로 이동합니다.

```bash
cd beaver-web-client
```

3. 필요한 패키지를 설치합니다.

```bash
npm install
```

4. 애플리케이션을 시작합니다.

```bash
npm start
```

실행에는 Node.js와 npm이 필요합니다. `npm start`는 클라이언트 개발 서버를 실행합니다. 파일 분석과 채팅 응답을 사용하려면 별도의 웹·모델 서버에 연결되어야 합니다. API 주소는 `FileUploadToServer.js`, `UserInput.js`, `ServerStateIndicator.js`에 작성되어 있습니다.

## 페이지 및 화면 구성

### 랜딩 페이지

<img src="https://github.com/inha-carbon-neutral-seven/beaver-web-client/blob/master/src/image/repo_images/Beaver%20Landing%20Page.JPG?raw=true" width="60%"/>

### 메인 페이지

<img src="https://github.com/inha-carbon-neutral-seven/beaver-web-client/blob/master/src/image/repo_images/Beaver%20chat.JPG?raw=true" width="40%" style="margin-right: 10px;" /> <img src="https://github.com/inha-carbon-neutral-seven/beaver-web-client/blob/master/src/image/repo_images/Beaver%20Sidebar.JPG?raw=true" width="40%" />

## 주요 기능 소개

### 다크 모드 지원

<img src="https://github.com/inha-carbon-neutral-seven/beaver-web-client/blob/master/src/image/repo_images/Beaver%20DarkMode%20Sidebar.JPG?raw=true" width="80%"/>

### 문서, 테이블 뷰어, 요약 문서, 데이터 시각화

<img src="https://github.com/inha-carbon-neutral-seven/beaver-web-client/blob/master/src/image/repo_images/document.webp?raw=true" width="80%"/>

### 테이블 데이터 분석

<img src="https://github.com/inha-carbon-neutral-seven/beaver-web-client/blob/master/src/image/repo_images/full.webp?raw=true" width="80%"/>
