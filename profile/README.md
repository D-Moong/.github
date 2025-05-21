# $\text{\color{#00579C} 𝗛𝗚𝗨 𝗚𝗹𝗼𝗰𝗮𝗹 𝗛𝗼𝗺𝗲𝗽𝗮𝗴𝗲}$

> 한동대학교 공식 글로컬 홈페이지

## 📝 개요

$\text{\color{#00579C} 𝗛𝗚𝗨 𝗚𝗹𝗼𝗰𝗮𝗹 𝗛𝗼𝗺𝗲𝗽𝗮𝗴𝗲}$ 는 한동대학교의 **2024년 글로컬대학 30 최종 선정**에 따라 제작된 공식 홈페이지입니다.  
본 웹사이트는 **학교의 글로컬 프로젝트를 소개**하고, **학생 및 관계자 간의 원활한 소통을 지원하기 위해 개발**되었습니다.

주요 기능:
- 📌 **게시판 시스템** (공지사항, 커뮤니티 등)
- 🔐 **사용자 인증** (로그인 / 회원가입)
- 🌍 **다국어 지원** (한국어 & 영어)
- 📱 **다양한 기기 지원** (반응형 UI)

<br />

## 🛠 기술 스택

### $\text{\color{#00579C} 𝗙𝗿𝗼𝗻𝘁𝗲𝗻𝗱}$

![Next.js](https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=next.js&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![CSS Modules](https://img.shields.io/badge/CSS_Modules-1572B6?style=for-the-badge&logo=css3&logoColor=white)

- **Framework:** `Next.js` (React 기반 SSR/SSG 지원)
- **Styling:** `CSS Modules` (컴포넌트별 스타일 관리)
- **State Management:** `Context API` (전역 상태 관리)
- **Internationalization:** `i18n` (다국어 지원)
- **API Request:** `Fetch API` (REST API 연동)

### $\text{\color{#00579C} 𝗕𝗮𝗰𝗸𝗲𝗻𝗱}$

![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=for-the-badge&logo=spring-boot&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)

- **Framework:** `Spring Boot` (백엔드 API 구축)
- **Database:** `PostgreSQL` (RDBMS)
- **Authentication:** JWT 기반 인증

### $\text{\color{#00579C} 𝗗𝗲𝗽𝗹𝗼𝘆𝗺𝗲𝗻𝘁 𝗮𝗻𝗱 𝗗𝗲𝘃𝗢𝗽𝘀}$
![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonWebServices&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)

- **Version Control:** `Git & GitHub` (소스 코드 관리)
- **CI/CD:** AWS 환경에서 배포 예정
- **Infrastructure:** `AWS EC2` + `RDS (PostgreSQL)`

<br />

## ☁️ 인프라 및 DevOps 구성

<sub>※ 실제 운영 환경을 기반으로 구성된 AWS 인프라 아키텍처</sub>
<img src="https://github.com/user-attachments/assets/3bd7fc62-7a10-461c-812e-a20ec1f7f45e" width=90%/>

### $\text{\color{#00579C} 𝗜𝗻𝗳𝗿𝗮𝘀𝘁𝗿𝘂𝗰𝘁𝘂𝗿𝗲}$

- **IaC 도구**: `Terraform`
    - 디렉토리 구조: `dev/`, `prod/`, `modules/`로 분리하여 환경별 구성 관리
    - `modules/` 디렉토리에는 `vpc`, `subnet`, `ec2`, `nat`, `rds`, `sg`, `s3` 등 공통 인프라 리소스를 모듈화하여 재사용성과 유지보수성 향상
    - Dev/Prod 환경에 맞는 변수만 주입하여 동일한 구조를 효율적으로 분기 구성
    - 모든 리소스는 선언형 코드 기반으로 자동 생성/삭제 가능

- **네트워크 구조**:
    - **Dev**: ALB 기반 퍼블릭 접근 구조, 프론트/백엔드 테스트 서버는 프라이빗 서브넷에 위치하며 Bastion 서버를 통해 접근
    - **Prod**: Elastic IP를 활용한 고정 IP 기반 배포, 프론트엔드 서버는 퍼블릭 서브넷에 위치하여 외부 접근 허용, 백엔드 서버는 프라이빗 서브넷에 위치해 내부 통신만 가능
    - Bastion 서버는 각각의 퍼블릭 서브넷에 구성되어, Dev/Prod의 모든 프라이빗 리소스에 보안 터널링 지원

### $\text{\color{#00579C} 𝗗𝗲𝘃𝗢𝗽𝘀, 𝗖𝗜/𝗖𝗗}$

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
