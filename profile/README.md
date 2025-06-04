# HGU Glocal Website

> 한동대학교 공식 글로컬 홈페이지

**공식 홈페이지**: [https://glocal.handong.edu](https://glocal.handong.edu)

## 📝 개요

**HGU Glocal Website** 는 한동대학교의 **2024년 글로컬대학 30 최종 선정**에 따라 제작된 공식 홈페이지입니다.  
본 웹사이트는 **학교의 글로컬 프로젝트를 소개**하고, **학생 및 관계자 간의 원활한 소통을 지원하기 위해 개발**되었습니다.

주요 기능:
- 📌 **게시판 시스템** (공지사항, 커뮤니티 등)
- 🔐 **사용자 인증** (로그인 / 회원가입)
- 🌍 **다국어 지원** (한국어 & 영어)
- 📱 **다양한 기기 지원** (반응형 UI)

<br />

## 🛠 기술 스택

### Frontend

![Next.js](https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=next.js&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![CSS Modules](https://img.shields.io/badge/CSS_Modules-1572B6?style=for-the-badge&logo=css3&logoColor=white)

- **Framework:** `Next.js` (React 기반 SSR/SSG 지원)
- **Styling:** `CSS Modules` (컴포넌트별 스타일 관리)
- **State Management:** `Context API` (전역 상태 관리)
- **Internationalization:** `i18n` (다국어 지원)
- **API Request:** `Fetch API` (REST API 연동)

### Backend

![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=for-the-badge&logo=spring-boot&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)

- **Framework:** `Spring Boot` (백엔드 API 구축)
- **Database:** `PostgreSQL` (RDBMS)
- **Authentication:** JWT 기반 인증

### Infra and DevOps
![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonWebServices&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)

- **Version Control:** `Git & GitHub` (소스 코드 관리)
- **CI/CD:** AWS 환경에서 배포 예정
- **Infrastructure:** `AWS EC2` + `RDS (PostgreSQL)`

<br />

## 📘 상세 설명

### Frontend

**주요 역할**

* `React` 및 `Next.js` 기반의 프론트엔드 UI 개발
* 사용자 인증 및 게시판 기능 제공
* 다국어(i18n) 지원 및 반응형 웹 구현
* Spring Boot 백엔드와의 API 통신 및 통합


#### 개발 컨벤션

> 코드의 일관성과 유지보수성을 높이고 원활한 협업을 위해 아래와 같은 규칙을 따릅니다.

##### 파일 및 디렉토리 네이밍 규칙

| 파일/디렉토리 유형 | 네이밍 규칙 | 예시 |
|-|-|-|
| **컴포넌트** | `PascalCase` | `Nav.tsx`, `UserProfile.tsx` |
| **훅 (Hooks)** | `camelCase` (`use` 접두어)| `useFetch.ts`, `useAuth.ts`|
| **API 서비스** | `camelCase` (`service.ts` 접미어) | `userService.ts`, `postService.ts` |
| **DTO 파일** | `requests.ts`, `responses.ts` | `requests.ts`, `responses.ts` |
| **상태 관리 (Context)** | `PascalCaseContext.tsx` | `AuthContext.tsx`, `ToastContext.tsx`|
| **스타일 파일** | `PascalCase.module.css` | `Button.module.css`, `NavBar.module.css` |
| **페이지 라우트** | 폴더명 소문자, 파일명 `page.tsx` | `/home/page.tsx`, `/privacyPolicy/page.tsx` |
| **아이콘 및 이미지 파일** | `kebab-case`| `logo.svg`, `user-profile.png` |

##### 코드 스타일

* 인덴트: `2 spaces`
* 세미콜론: 사용함 `;`
* 따옴표: 더블 쿼트 `"`
* 함수형 컴포넌트 사용 권장 (`const` + 화살표 함수)
* 불필요한 `console.log` 지양

---

#### Git 워크플로우

##### 📌 브랜치 전략

| 브랜치명 | 설명 |
| -------------- | ---------------------- |
| `main` | 운영 및 릴리즈 브랜치 (배포 시 PR) |
| `dev` | 개발 기본 브랜치 |
| `feat#XXX` | 기능 개발 브랜치 (이슈 번호 기반) |
| `fix#XXX` | 버그 수정 브랜치 |
| `docs#XXX` | 문서 수정 관련 브랜치 |
| `refactor#XXX` | 리팩토링 브랜치 |

**이미지**

<img src="https://github.com/user-attachments/assets/388b7338-69ca-482d-9573-e8ee772fcd63" alt="branch-workflow">

##### 작업 플로우

1. 이슈 생성
2. 브랜치 생성

```bash
git switch dev
git pull origin dev
git checkout -b feat#16
```

3. 커밋 & 푸시

```bash
git add .
git commit -m "feat: 로그인 기능 추가 (#16)"
git push origin feat#16
```

4. PR 생성 → 대상 브랜치: `dev`

   * PR 제목: `Feat/#16 로그인 기능 추가`
   * PR 본문: `Resolve #16`
     
5. 코드 리뷰 → PR 병합
6. 배포 전 `release ← dev` 병합

```bash
git switch release
git merge dev
git push origin release
```


#### 프로젝트 디렉토리 구조

```plaintext
./
├── api/
│   ├── apiClient.ts              # Fetch 기반 공통 API 클라이언트 (accessToken 자동 처리)
│   └── domains/                  # 도메인 기반 API 분리
│       ├── board/
│       │   ├── dtos/
│       │   │   ├── requests.ts
│       │   │   └── responses.ts
│       │   └── service.ts
│       └── ...
├── auth/                         # 인증 관련 로직
├── config/                       # 링크 및 설정 정보
├── contexts/                     # Context API 관련
├── hooks/                        # 커스텀 훅 모음
├── locales/                      # 다국어 지원
│   ├── en.json
│   ├── ko.json
│   └── lib/
│       └── i18n.ts
├── pages/                        # Next.js 라우트 페이지
│   └── contents/board/...        # 게시판 종류별 페이지 구조
├── widgets/                      # 재사용 UI 및 구조적 컴포넌트
│   ├── components/
│   └── structures/
├── utils/                        # 유틸 함수
├── layout.tsx                    # 공통 레이아웃
├── globals.scss                  # 전역 스타일
└── favicon.ico
```


#### 다국어(i18n) 지원

* 번역 JSON: `locales/en.json`, `locales/ko.json`
* 설정 파일: `locales/lib/i18n.ts`
* 언어 상태: `useLanguage.tsx`

### Backend



### Infra and DevOps

#### Architecture

<figure>
<img src="https://github.com/user-attachments/assets/3bd7fc62-7a10-461c-812e-a20ec1f7f45e" width=90%/>
<figcaption><br /><sub>※ 실제 운영 환경을 기반으로 구성된 AWS 인프라 아키텍처</sub></figcaption>
</figure>

#### Infrastructure

- **IaC 도구**: `Terraform`
    - 디렉토리 구조: `dev/`, `prod/`, `modules/`로 분리하여 환경별 구성 관리
    - `modules/` 디렉토리에는 `vpc`, `subnet`, `ec2`, `nat`, `rds`, `sg`, `s3` 등 공통 인프라 리소스를 모듈화하여 재사용성과 유지보수성 향상
    - Dev/Prod 환경에 맞는 변수만 주입하여 동일한 구조를 효율적으로 분기 구성
    - 모든 리소스는 선언형 코드 기반으로 자동 생성/삭제 가능

- **네트워크 구조**:
    - **Dev**: ALB 기반 퍼블릭 접근 구조, 프론트/백엔드 테스트 서버는 프라이빗 서브넷에 위치하며 Bastion 서버를 통해 접근
    - **Prod**: Elastic IP를 활용한 고정 IP 기반 배포, 프론트엔드 서버는 퍼블릭 서브넷에 위치하여 외부 접근 허용, 백엔드 서버는 프라이빗 서브넷에 위치해 내부 통신만 가능
    - Bastion 서버는 각각의 퍼블릭 서브넷에 구성되어, Dev/Prod의 모든 프라이빗 리소스에 보안 터널링 지원

#### DevOps, CI/CD

- **CI 도구**: `GitHub Actions`
  - `develop → release` 브랜치 전략 기반 CI/CD 파이프라인 설계
  - Secrets 관리로 민감 정보 보호 (ex. `.env.production`, `application-secret.properties`)
  
- **CD 방식**:
  - **Frontend**:
    - `.env.production`은 GitHub Secrets에서 복호화 후 이미지 빌드시 반영
    - `docker system prune`으로 배포 시 캐시 자동 정리
    - Nginx 설정으로 보안 헤더 및 백엔드와 내부 통신 처리
    
  - **Backend**:
    - EC2 서버에 `application-secret.properties` 파일 동적 생성 및 마운트
    - 컨테이너 재실행 전 ECR 최신 이미지 pull 및 기존 컨테이너 제거
    
- **보안 강화**:
  - `OWASP ZAP` 취약점 점검 자동화
  - 고정 IP 기반 취약점 보고서 생성 및 관리자 제출 완료
  - CSP, X-Frame-Options, Referrer-Policy 등 Nginx 보안 헤더 설정 완료
