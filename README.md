# 개발 블로그 템플릿

이 템플릿은 Astro 5.12.0과 Content Collections를 기반으로 구축된 재사용 가능한 개발 블로그 템플릿입니다. 콘텐츠 중심의 구조를 사용하여 쉽고 빠르게 자신만의 블로그를 만들 수 있습니다.

## ✨ 주요 기능

- **다크 모드 지원**: 사용자 시스템 설정 감지 및 수동 토글, FOUC 방지 최적화
- **반응형 디자인**: 모바일 및 데스크톱 환경 완벽 지원
- **타입 안전성**: Content Collections 및 TypeScript(strict 모드)를 통한 데이터 유효성 검사
- **자동 날짜 정렬 및 포맷팅**: 블로그 포스트 및 프로젝트 날짜 자동 처리
- **간결한 디자인**: 미니멀하고 타이포그래피 중심의 레이아웃
- **댓글 시스템**: giscus 통합 지원으로 GitHub 기반 댓글 기능

## 🚀 시작하기

### 1. 프로젝트 설치

```bash
git clone [이 저장소의 URL]
cd [클론된 저장소 이름]
npm install
```

### 2. 개발 서버 실행

```bash
npm run dev
```

개발 서버는 `localhost:4321`에서 실행됩니다.

### 3. 프로덕션 빌드 및 미리보기

```bash
npm run build
npm run preview
```

`npm run build`는 `./dist/` 폴더에 프로덕션 빌드를 생성하며, `npm run preview`로 빌드된 사이트를 미리 볼 수 있습니다.

## ⚙️ 템플릿 사용법

### 1. 개인화 설정

`src/config/site.ts` 파일을 수정하여 사이트의 전역 정보를 설정하세요. 이 파일의 변경 사항은 블로그 전체에 자동으로 반영됩니다.

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
  
  // giscus 댓글 시스템 설정
  comments: {
    // giscus.app에서 생성된 스크립트를 아래에 붙여넣으세요
    // 빈 문자열이면 댓글이 비활성화됩니다
    giscusScript: `
      <!-- giscus.app에서 생성된 스크립트를 여기에 붙여넣으세요 -->
    `.trim()
  }
};
```

### 2. 블로그 포스트 작성

`src/content/blog/` 디렉토리에 마크다운(`.md`) 파일을 생성하여 블로그 포스트를 작성합니다. 각 포스트는 다음과 같은 프론트매터를 포함해야 합니다.

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

**프론트매터 필드 설명:**
- `title`: 포스트 제목 (필수)
- `description`: 포스트 설명 (선택)
- `publishDate`: 발행 날짜 (필수, `YYYY-MM-DD` 형식)
- `updatedDate`: 수정 날짜 (선택)
- `tags`: 태그 배열 (선택, 기본값: `[]`)
- `draft`: 초안 여부 (선택, `true`로 설정 시 빌드에 포함되지 않음, 기본값: `false`)

### 3. 프로젝트 정보 수정

`src/data/projects.json` 파일을 수정하여 프로젝트 정보를 업데이트합니다. 각 프로젝트는 `id`, `title`, `description`, `status`, `period`, `technologies`, `links` 필드를 가집니다.

```json
{
  "projects": [
    {
      "id": "unique-project-id",
      "title": "프로젝트 제목",
      "thumbnail": "/path/to/thumbnail.png", // 썸네일 이미지 경로 (선택 사항)
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

### 4. 댓글 시스템 설정 (선택 사항)

블로그 포스트에 댓글 기능을 추가하려면 giscus를 설정하세요:

1. [giscus.app](https://giscus.app)에 접속
2. GitHub 저장소를 설정하고 giscus 앱을 설치
3. 설정을 완료하면 생성되는 `<script>` 태그 전체를 복사
4. `src/config/site.ts`의 `comments.giscusScript` 필드에 붙여넣기

```typescript
// src/config/site.ts
comments: {
  giscusScript: `
    <script src="https://giscus.app/client.js"
            data-repo="your-username/your-repo"
            data-repo-id="your-repo-id"
            data-category="General"
            data-category-id="your-category-id"
            data-mapping="pathname"
            data-strict="0"
            data-reactions-enabled="1"
            data-emit-metadata="0"
            data-input-position="bottom"
            data-theme="preferred_color_scheme"
            data-lang="ko"
            crossorigin="anonymous"
            async>
    </script>
  `.trim()
}
```

댓글을 비활성화하려면 `giscusScript`를 빈 문자열 `""` 로 설정하세요.

### 5. 이력서 정보 수정

`src/data/resume.json` 파일을 수정하여 이력서 정보를 업데이트합니다. 프로필 설명, 기술 스택, 경력, 학력 등을 포함할 수 있습니다.

```json
{
  "profile": {
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

## 📁 프로젝트 구조

```
src/
├── components/
│   └── Comments.astro  # 댓글 컴포넌트 (giscus 통합)
├── config/
│   └── site.ts         # 사이트 전역 설정
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

## 🎨 커스터마이징

### 다크 모드

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

## 🔧 문제 해결

### 빌드 오류
- TypeScript 오류: `npm run astro check`로 타입 확인
- 마크다운 오류: 프론트매터 형식 확인

### 콘텐츠가 표시되지 않을 때
- 파일 경로 확인
- JSON 형식 유효성 검사
- 프론트매터 날짜 형식 확인 (YYYY-MM-DD)

## 🤝 기여

이 템플릿에 기여하고 싶으시다면, 언제든지 풀 리퀘스트를 보내주세요! 버그 보고, 기능 제안 등 모든 기여를 환영합니다.

## 📄 라이선스

이 프로젝트는 MIT 라이선스 하에 배포됩니다. 자세한 내용은 `LICENSE` 파일을 참조하세요.

---

이 템플릿을 사용하여 멋진 개발 블로그를 만들어보세요! 🎉