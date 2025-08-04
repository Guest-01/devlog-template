# GEMINI.md

This file provides guidance to Gemini when working with code in this repository.

## 프로젝트 개요
재사용 가능한 개발 블로그 템플릿입니다. Astro 5.12.0 + Content Collections 기반의 정적 사이트 생성기로, 콘텐츠 기반 구조를 사용합니다.

## 주요 명령어

### 개발 서버
```bash
npm run dev          # 개발 서버 실행 (localhost:4321)
npm run build        # 프로덕션 빌드 (./dist/ 폴더에 생성)
npm run preview      # 빌드 미리보기
```

### Astro CLI
```bash
npm run astro add <integration>    # 통합 추가
npm run astro check               # TypeScript 및 Astro 검사
npm run astro -- --help          # CLI 도움말
```

## 코드 아키텍처

### 디렉토리 구조
- `src/config/site.ts`: 사이트의 전역 설정 (이름, 작성자 정보, 소셜 링크 등)
- `src/content/`: Content Collections (블로그 포스트)
  - `config.ts`: 스키마 정의
  - `blog/`: 마크다운 블로그 포스트
- `src/data/`: 페이지별 콘텐츠 데이터
  - `projects.json`: 프로젝트 정보
  - `resume.json`: 이력서 정보 (프로필 설명 포함)
- `src/layouts/Layout.astro`: 메인 레이아웃 (네비게이션, 다크모드 포함)
- `src/pages/`: 페이지 컴포넌트
- `src/types/`: TypeScript 타입 정의

### 정보 관리 시스템
- **전역 설정 (`src/config/site.ts`)**: 사이트 이름, 전체 페이지에 걸쳐 사용될 작성자 정보 등 거의 변경되지 않는 값을 관리합니다.
- **콘텐츠 데이터 (`src/data/`)**: 프로젝트, 이력서 등 특정 페이지에 표시되며 자주 업데이트될 수 있는 구조화된 콘텐츠를 관리합니다.
- **블로그 콘텐츠 (`src/content/`)**: 마크다운 기반의 블로그 게시물을 Astro Content Collections로 관리합니다.

### 주요 기능
- 다크모드 지원 (시스템 설정 감지, 로컬 저장소 유지)
- 반응형 디자인
- Content Collections로 타입 안전성 보장
- 자동 날짜 정렬 및 포맷팅
- FOUC 방지 최적화

## 템플릿 사용법

### 1. 개인화 설정
`src/config/site.ts`에서 사이트 및 작성자 정보를 수정하세요:

```typescript
export const SITE = {
  name: 'Your Site Name', // 사이트 이름
  title: 'Your Site Title', // 기본 페이지 제목
  description: 'Your site description for SEO.', // SEO용 설명
  author: {
    name: '홍재훈', // 작성자 이름
    email: 'your-email@example.com', // 이메일 주소
    github: 'https://github.com/your-username', // GitHub 프로필 URL
    linkedin: 'https://linkedin.com/in/your-username', // LinkedIn 프로필 URL
  },
};
```

### 2. 콘텐츠 추가
- **블로그**: `src/content/blog/`에 마크다운 파일 추가
- **프로젝트**: `src/data/projects.json` 수정
- **이력서**: `src/data/resume.json` 수정 (특히 `profile.description`)

## 개발 상태
- ✅ 전역 설정(`site.ts`) 및 데이터 분리 완료
- ✅ Content Collections 설정 완료
- ✅ 동적 콘텐츠 로딩 구현
- ✅ 다크모드 완전 지원
- ✅ TypeScript 타입 정의 및 오류 수정 완료

## 기술 스택
- **프레임워크**: Astro 5.12.0
- **언어**: TypeScript (strict 모드)
- **콘텐츠**: Content Collections + JSON
- **스타일링**: 스코프 CSS
- **타입 체크**: Zod 스키마 + TypeScript