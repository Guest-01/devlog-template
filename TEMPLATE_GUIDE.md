# 개발 블로그 템플릿 사용 가이드

이 템플릿을 사용하여 자신만의 개발 블로그를 쉽게 만들 수 있습니다.

## 🚀 시작하기

### 1. 기본 설정

각 페이지의 프론트매터 변수들을 수정하여 개인 정보를 설정하세요:

- **Layout.astro**: `siteName`, `siteTitle` 변수 수정 (전역 사이트 정보)
- **블로그/프로젝트/이력서 페이지**: `authorName` 변수 수정

```typescript
// src/layouts/Layout.astro에서만 설정
const siteName = "TIL"; // 좌상단 로고명
const siteTitle = "개발로그"; // 기본 페이지 제목
```

모든 사이트 정보는 Layout.astro에서 중앙 집중 관리되며, 개별 페이지에서는 필요시 `title` prop을 통해 페이지별 제목을 설정할 수 있습니다.

### 2. 블로그 포스트 작성

`src/content/blog/` 디렉토리에 마크다운 파일을 생성하여 블로그 포스트를 작성하세요:

```markdown
---
title: "포스트 제목"
description: "포스트 설명"
publishDate: 2024-03-15
tags: ["React", "JavaScript"]
draft: false
---

# 포스트 내용

마크다운으로 작성된 블로그 포스트 내용입니다.
```

#### 프론트매터 필드 설명:
- `title`: 포스트 제목 (필수)
- `description`: 포스트 설명 (선택)
- `publishDate`: 발행 날짜 (필수)
- `updatedDate`: 수정 날짜 (선택)
- `tags`: 태그 배열 (기본값: [])
- `draft`: 초안 여부 (기본값: false)

### 3. 프로젝트 정보 수정

`src/data/projects.json` 파일을 수정하여 프로젝트 정보를 업데이트하세요:

```json
{
  "projects": [
    {
      "id": "unique-project-id",
      "title": "프로젝트 제목",
      "description": "프로젝트 설명",
      "status": "진행중", // "진행중", "완료", "중단"
      "period": {
        "start": "2024.01",
        "end": "현재"
      },
      "technologies": ["React", "Node.js", "MongoDB"],
      "links": {
        "github": "https://github.com/username/repo",
        "demo": "https://your-demo.com"
      }
    }
  ]
}
```

### 4. 이력서 정보 수정

`src/data/resume.json` 파일을 수정하여 이력서 정보를 업데이트하세요:

```json
{
  "profile": {
    "name": "당신의 이름",
    "title": "직책",
    "description": [
      "자기소개 첫 번째 문단",
      "자기소개 두 번째 문단"
    ]
  },
  "skills": {
    "frontend": ["React", "Vue.js", "TypeScript"],
    "backend": ["Node.js", "Python", "PostgreSQL"],
    "devopsAndTools": ["Docker", "AWS", "Git"]
  },
  "experience": [
    {
      "company": "회사명",
      "position": "직책",
      "period": {
        "start": "2022.03",
        "end": "현재"
      },
      "achievements": [
        "주요 성과 1",
        "주요 성과 2"
      ]
    }
  ],
  "education": [
    {
      "institution": "대학교명",
      "degree": "학위",
      "period": {
        "start": "2017.03",
        "end": "2021.02"
      }
    }
  ]
}
```

## 🎨 커스터마이징

### 다크 모드

다크 모드는 기본으로 제공되며, 다음과 같은 특징을 가집니다:
- 사용자 시스템 설정에 따른 자동 적용
- 수동 토글 기능 (우상단 버튼)
- FOUC(Flash of Unstyled Content) 방지 최적화
- 로컬 스토리지를 통한 설정 유지

### 디자인 특징

- **미니멀 디자인**: 카드 없는 깔끔한 이력서 레이아웃
- **타이포그래피 중심**: 콘텐츠에 집중하는 심플한 스타일  
- **반응형**: 모바일부터 데스크톱까지 완벽 지원
- **모노스페이스 날짜**: 가독성 좋은 날짜 표시

### 스타일 수정

각 페이지의 스타일은 해당 `.astro` 파일의 `<style>` 섹션에서 수정할 수 있습니다.

### 네비게이션 메뉴 변경

`src/layouts/Layout.astro`의 네비게이션 링크를 직접 수정하여 메뉴를 변경할 수 있습니다:

```html
<div class="nav-links">
  <a href="/blog">블로그</a>
  <a href="/projects">프로젝트</a>
  <a href="/resume">이력서</a>
  <!-- 새 메뉴 추가 -->
</div>
```

## 📝 개발 명령어

```bash
# 개발 서버 실행
npm run dev

# 프로덕션 빌드
npm run build

# 빌드 미리보기
npm run preview

# 타입 체크
npm run astro check
```

## 🌟 추가 기능

### 새로운 블로그 포스트 생성

1. `src/content/blog/` 디렉토리에 새 `.md` 파일 생성
2. 프론트매터 작성
3. 마크다운 콘텐츠 작성
4. 자동으로 블로그 목록에 표시됨

### 프로젝트 추가

1. `src/data/projects.json`에 새 프로젝트 객체 추가
2. 자동으로 프로젝트 페이지에 표시됨

### 타입 안전성

모든 데이터 구조는 TypeScript로 타입이 정의되어 있어 안전한 개발이 가능합니다.

## 🚀 배포

### Vercel
1. GitHub에 리포지토리 푸시
2. Vercel에서 Import
3. 자동 배포 완료

### Netlify
1. `npm run build` 실행
2. `dist/` 폴더를 Netlify에 업로드

### GitHub Pages
1. GitHub Actions 워크플로우 설정
2. 자동 빌드 및 배포

## 📁 프로젝트 구조

```
src/
├── content/
│   ├── config.ts        # Content Collections 설정
│   └── blog/           # 블로그 포스트 (마크다운)
├── data/
│   ├── projects.json   # 프로젝트 데이터
│   └── resume.json     # 이력서 데이터
├── layouts/
│   └── Layout.astro    # 메인 레이아웃 (네비게이션, 다크모드 포함)
├── pages/
│   ├── index.astro     # 홈페이지
│   ├── blog.astro      # 블로그 목록
│   ├── blog/[slug].astro # 개별 블로그 포스트
│   ├── projects.astro  # 프로젝트 목록
│   └── resume.astro    # 이력서 (미니멀 디자인)
└── types/
    └── index.ts        # TypeScript 타입 정의
```

## 🔧 문제 해결

### 빌드 오류
- TypeScript 오류: `npm run astro check`로 타입 확인
- 마크다운 오류: 프론트매터 형식 확인

### 콘텐츠가 표시되지 않을 때
- 파일 경로 확인
- JSON 형식 유효성 검사
- 프론트매터 날짜 형식 확인 (YYYY-MM-DD)

이 템플릿을 사용하여 멋진 개발 블로그를 만들어보세요! 🎉