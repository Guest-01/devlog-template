# 개발 블로그 템플릿 사용 가이드

이 템플릿을 사용하여 자신만의 개발 블로그를 쉽게 만들 수 있습니다.

## 🚀 시작하기

### 1. 기본 설정

`src/config/site.ts` 파일을 수정하여 사이트의 모든 개인 정보를 한 곳에서 관리하세요. 이 파일을 수정하면 블로그 전체에 자동으로 반영됩니다.

```typescript
// src/config/site.ts

export const SITE = {
  name: 'TIL', // 사이트 이름 (네비게이션 로고)
  title: 'TIL - Today I Learned', // 기본 페이지 제목 (브라우저 탭)
  description: 'A personal blog for sharing what I learn.', // SEO를 위한 기본 사이트 설명
  author: {
    name: '홍재훈', // 작성자 이름
    profile: '/profile-picture.png', // 프로필 사진 경로 (선택 사항)
    email: 'your-email@example.com', // 이메일 주소
    github: 'https://github.com/your-username', // GitHub 프로필 URL
    linkedin: 'https://linkedin.com/in/your-username', // LinkedIn 프로필 URL
  },
};
```

이 파일을 수정하면 네비게이션 메뉴, 페이지 제목, 작성자 정보 등이 자동으로 업데이트됩니다.

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
    "description": [
      "안녕하세요, 개발자 홍재훈입니다.",
      "3년차 풀스택 개발자로서 사용자 중심의 웹 애플리케이션 개발에 집중하고 있습니다. 새로운 기술을 빠르게 습득하고 팀과 협업하며 문제를 해결하는 것을 좋아합니다."
    ]
  },
  "skills": {
    "frontend": [
      "React",
      "Vue.js", 
      "TypeScript",
      "Next.js",
      "Tailwind CSS"
    ],
    "backend": [
      "Node.js",
      "Express",
      "NestJS",
      "PostgreSQL",
      "MongoDB"
    ],
    "devopsAndTools": [
      "Docker",
      "AWS",
      "Git",
      "GitHub Actions",
      "Vercel"
    ]
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

## 📝 개발 명령어

```bash
npm run dev          # 개발 서버 실행 (localhost:4321)
npm run build        # 프로덕션 빌드 (./dist/ 폴더에 생성)
npm run preview      # 빌드 미리보기

npm run astro add <integration>    # 통합 추가
npm run astro check               # TypeScript 및 Astro 검사
npm run astro -- --help          # CLI 도움말
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

모든 데이터 구조는 TypeScript로 타입이 정의되어 있어 안전한 개발이 가능합니다. 특히, `tsconfig.json`에서 `"strict": true`로 설정되어 있어 더욱 엄격한 타입 검사를 제공합니다.

## 🔧 문제 해결

### 빌드 오류
- TypeScript 오류: `npm run astro check`로 타입 확인
- 마크다운 오류: 프론트매터 형식 확인

### 콘텐츠가 표시되지 않을 때
- 파일 경로 확인
- JSON 형식 유효성 검사
- 프론트매터 날짜 형식 확인 (YYYY-MM-DD)

이 템플릿을 사용하여 멋진 개발 블로그를 만들어보세요! 🎉