# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

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
- `src/config/site.ts`: 사이트 전역 설정 (이름, 네비게이션 등)
- `src/content/`: Content Collections (블로그 포스트)
  - `config.ts`: 스키마 정의
  - `blog/`: 마크다운 블로그 포스트
- `src/data/`: JSON 데이터 파일
  - `projects.json`: 프로젝트 정보
  - `resume.json`: 이력서 정보
- `src/layouts/Layout.astro`: 메인 레이아웃 (네비게이션, 다크모드 포함)
- `src/pages/`: 페이지 컴포넌트 (동적 콘텐츠 로딩)
- `src/types/`: TypeScript 타입 정의

### 콘텐츠 관리 시스템
- **블로그**: Astro Content Collections로 마크다운 파일 관리
- **프로젝트**: JSON 기반 구조화된 데이터
- **이력서**: JSON 기반 구조화된 데이터
- **설정**: TypeScript 설정 파일로 개인화

### 주요 기능
- 다크모드 지원 (시스템 설정 감지, 로컬 저장소 유지)
- 반응형 디자인
- Content Collections로 타입 안전성 보장
- 자동 날짜 정렬 및 포맷팅
- FOUC 방지 최적화

## 템플릿 사용법

### 1. 개인화 설정
`src/config/site.ts`에서 개인 정보 수정:
- 이름, 이메일, 소셜 링크
- 네비게이션 메뉴 구성
- 사이트 메타데이터

### 2. 콘텐츠 추가
- **블로그**: `src/content/blog/` 에 마크다운 파일 추가
- **프로젝트**: `src/data/projects.json` 수정
- **이력서**: `src/data/resume.json` 수정

### 3. 자동 기능
- 블로그 포스트 자동 정렬 (최신순)
- 타입 안전성 검증
- 다크모드 자동 적용

## 스타일링 시스템
- 컴포넌트별 스코프 스타일
- 일관된 다크모드 색상 시스템
- 반응형 디자인 (768px 브레이크포인트)
- 고정폭 폰트 날짜 표시

## 개발 상태
- ✅ Content Collections 설정 완료
- ✅ 동적 콘텐츠 로딩 구현
- ✅ 다크모드 완전 지원
- ✅ TypeScript 타입 정의 완료
- ✅ 템플릿화 완료

## 기술 스택
- **프레임워크**: Astro 5.12.0
- **언어**: TypeScript (strict 모드)
- **콘텐츠**: Content Collections + JSON
- **스타일링**: 스코프 CSS
- **타입 체크**: Zod 스키마 + TypeScript