# 웹 이력서 프로젝트 기술 가이드

> 이 문서는 웹 초보자를 위한 프로젝트 기술 스택 및 구현 방법을 설명합니다.

---

## 📚 목차

1. [프로젝트 개요](#프로젝트-개요)
2. [기술 스택 소개](#기술-스택-소개)
3. [Jekyll이란?](#jekyll이란)
4. [프로젝트 구조 이해하기](#프로젝트-구조-이해하기)
5. [HTML 구조 분석](#html-구조-분석)
6. [CSS 스타일링 분석](#css-스타일링-분석)
7. [JavaScript 동작 분석](#javascript-동작-분석)
8. [데이터 관리 방식 (YAML)](#데이터-관리-방식-yaml)
9. [배포 프로세스](#배포-프로세스)
10. [추가 학습 자료](#추가-학습-자료)

---

## 프로젝트 개요

이 프로젝트는 **Jekyll을 사용한 정적 웹사이트**로, GitHub Pages에 배포되는 개인 이력서 웹사이트입니다.

### 핵심 특징
- ✅ **정적 사이트**: 서버 없이 HTML/CSS/JS만으로 동작
- ✅ **데이터 분리**: 코드와 콘텐츠가 분리됨 (유지보수 용이)
- ✅ **자동 배포**: GitHub에 푸시하면 자동으로 웹사이트 업데이트
- ✅ **반응형 디자인**: 모바일, 태블릿, 데스크톱 모두 지원

---

## 기술 스택 소개

### 1️⃣ **Jekyll** (정적 사이트 생성기)
- **역할**: YAML 데이터와 템플릿을 HTML로 변환
- **언어**: Ruby 기반
- **사용 위치**: 전체 프로젝트의 빌드 시스템

### 2️⃣ **HTML** (구조)
- **역할**: 웹페이지의 뼈대와 콘텐츠 구조 정의
- **사용 파일**: `index.html`
- **주요 기술**:
  - Semantic HTML (의미있는 태그 사용)
  - Liquid 템플릿 문법 (Jekyll의 템플릿 언어)

### 3️⃣ **CSS** (스타일링)
- **역할**: 디자인, 색상, 레이아웃, 애니메이션
- **사용 파일**: `assets/css/style.css`
- **주요 기술**:
  - CSS Variables (재사용 가능한 변수)
  - Flexbox & Grid (레이아웃)
  - CSS Animations (부드러운 효과)
  - Media Queries (반응형 디자인)

### 4️⃣ **JavaScript** (동적 기능)
- **역할**: 사용자 인터랙션과 애니메이션 제어
- **사용 위치**: `index.html` 하단의 `<script>` 태그
- **주요 기술**:
  - Intersection Observer API (스크롤 애니메이션)
  - DOM 조작 (요소 선택 및 제어)

### 5️⃣ **Liquid** (템플릿 엔진)
- **역할**: 데이터를 HTML에 자동으로 삽입
- **문법**: `{{ }}`, `{% %}`
- **사용 위치**: `index.html` 전체

### 6️⃣ **YAML** (데이터 포맷)
- **역할**: 콘텐츠 데이터 저장
- **사용 위치**: `_data/` 폴더의 모든 `.yml` 파일

### 7️⃣ **GitHub Pages** (호스팅)
- **역할**: 웹사이트를 인터넷에 무료로 배포
- **자동화**: GitHub Actions로 자동 빌드 및 배포

---

## Jekyll이란?

### Jekyll의 역할

Jekyll은 **템플릿 + 데이터 → HTML 변환기**입니다.

```
┌─────────────────┐
│  템플릿 파일     │  index.html (with Liquid syntax)
│  (index.html)   │  + 
│       +         │  _data/*.yml (YAML 데이터)
│  데이터 파일     │
│  (_data/*.yml)  │
└────────┬────────┘
         │
         ▼
    [Jekyll Build]
         │
         ▼
┌─────────────────┐
│  순수 HTML      │  최종 결과물
│  (_site/)       │  (브라우저가 읽을 수 있는 HTML)
└─────────────────┘
```

### Jekyll 설정 파일: `_config.yml`

**위치**: 프로젝트 루트
**역할**: Jekyll의 전역 설정 및 사이트 정보 정의

```yaml
# 사이트 정보 (어디서든 사용 가능)
title: 이영준 | AI/ML Engineer
email: younghe42286@gmail.com
description: AI/ML 엔지니어의 이력서

# GitHub Pages 설정
url: "https://yjjonatanlee.github.io"
github_username: YJJonatanLee

# Jekyll 플러그인
plugins:
  - jekyll-feed  # RSS 피드 생성
```

**사용 예시** (HTML에서 `{{ site.title }}` 같은 형태로 접근):
```html
<title>{{ site.title }}</title>
<!-- 결과: <title>이영준 | AI/ML Engineer</title> -->
```

---

## 프로젝트 구조 이해하기

```
프로젝트 루트/
│
├── _config.yml              ← Jekyll 설정 파일
│
├── _data/                   ← 📊 모든 콘텐츠 데이터 (YAML)
│   ├── links.yml           ← 연락처/소셜 링크
│   ├── education.yml       ← 학력
│   ├── career.yml          ← 경력
│   ├── skills.yml          ← 기술 스택
│   ├── projects.yml        ← 프로젝트
│   ├── publications.yml    ← 논문/발표
│   └── additional.yml      ← 자격증/수상
│
├── assets/                  ← 정적 자원
│   ├── css/
│   │   └── style.css       ← 🎨 모든 CSS 스타일
│   └── images/             ← 이미지 파일
│
├── index.html               ← 🏠 메인 HTML 파일 (Liquid 템플릿)
│
├── docs/                    ← 📚 프로젝트 문서
│
├── Gemfile                  ← Ruby 의존성 관리
├── Gemfile.lock
├── _site/                   ← Jekyll 빌드 결과 (자동 생성, Git 무시)
├── robots.txt               ← 검색 엔진 크롤러 설정
└── sitemap.xml              ← SEO용 사이트맵
```

### 주요 파일 설명

| 파일/폴더 | 역할 | 수정 빈도 |
|---------|------|---------|
| `_config.yml` | Jekyll 전역 설정, 사이트 메타정보 | 거의 없음 |
| `_data/*.yml` | 이력서 콘텐츠 (학력, 경력, 프로젝트 등) | **자주** |
| `index.html` | 템플릿 구조 (레이아웃 변경 시) | 가끔 |
| `assets/css/style.css` | 디자인 수정 (색상, 레이아웃) | 가끔 |
| `Gemfile` | Ruby 라이브러리 의존성 | 거의 없음 |

---

## HTML 구조 분석

**파일**: `index.html`

### 1. Front Matter (상단 3줄)

```yaml
---
layout: none
---
```

- **의미**: Jekyll에게 "이 파일을 처리해줘"라고 알림
- `layout: none`: 다른 레이아웃 템플릿을 사용하지 않음

### 2. HTML 기본 구조

```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <!-- 메타 정보, CSS 링크 -->
</head>
<body>
  <!-- 콘텐츠 섹션들 -->
  <script>
    <!-- JavaScript 코드 -->
  </script>
</body>
</html>
```

### 3. `<head>` 섹션의 주요 요소

#### 3-1. 메타 태그 (SEO 최적화)

```html
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="{{ site.description }}">
<meta name="keywords" content="이영준, AI Engineer, ...">
```

- `charset="UTF-8"`: 한글 등 다국어 지원
- `viewport`: 모바일 반응형 설정
- `description`, `keywords`: Google 검색 최적화

#### 3-2. Open Graph 메타 태그 (소셜 미디어 공유)

```html
<meta property="og:type" content="website">
<meta property="og:title" content="{{ site.title }}">
<meta property="og:description" content="{{ site.description }}">
```

- **역할**: 링크를 공유할 때 미리보기 이미지와 제목 표시
- **적용 예**: 카카오톡, 페이스북, 트위터에서 링크 공유 시

#### 3-3. Google Fonts 로드

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">
```

- **폰트**: Inter (400~800 굵기)
- **최적화**: `preconnect`로 로딩 속도 개선

#### 3-4. Structured Data (JSON-LD)

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Person",
  "name": "이영준",
  "jobTitle": "AI/ML Engineer",
  ...
}
</script>
```

- **역할**: Google에게 "이 사이트는 개인 이력서입니다"라고 구조화된 정보 제공
- **효과**: Google 검색 결과에서 더 풍부한 정보 표시 가능

### 4. `<body>` 섹션 구조

전체 구조는 **여러 섹션의 연속**입니다:

```html
<body>
  <!-- 1. Hero 섹션 (최상단 프로필) -->
  <section class="hero">...</section>

  <!-- 2. 학력 섹션 -->
  <section class="section" id="education">...</section>

  <!-- 3. 경력 섹션 -->
  <section class="section" id="career">...</section>

  <!-- 4. 기술 스택 섹션 -->
  <section class="section" id="skills">...</section>

  <!-- 5. 프로젝트 섹션 -->
  <section class="section" id="projects">...</section>

  <!-- 6. 논문 섹션 -->
  <section class="section" id="publications">...</section>

  <!-- 7. 자격증/수상 섹션 -->
  <section class="section" id="additional">...</section>

  <!-- 8. 기타 경력 섹션 -->
  <section class="section" id="other">...</section>

  <!-- 9. Footer -->
  <footer>...</footer>

  <!-- 10. JavaScript -->
  <script>...</script>
</body>
```

### 5. Liquid 템플릿 문법 (Jekyll)

#### 5-1. 변수 출력 `{{ }}`

```html
<h1>{{ site.title }}</h1>
<!-- _config.yml에 정의된 title 변수를 출력 -->
```

#### 5-2. 반복문 `{% for %}`

```liquid
{% for edu in site.data.education %}
  <div class="card">
    <h3>{{ edu.degree }}</h3>
    <div>{{ edu.school }}</div>
  </div>
{% endfor %}
```

- **의미**: `_data/education.yml` 파일의 각 항목을 반복하며 HTML 생성
- **결과**: education.yml에 2개 항목이 있으면 2개의 카드가 생성됨

#### 5-3. 조건문 `{% if %}`

```liquid
{% if project.achievements %}
  <ul>
    {% for achievement in project.achievements %}
      <li>{{ achievement }}</li>
    {% endfor %}
  </ul>
{% endif %}
```

- **의미**: `achievements` 필드가 있을 때만 `<ul>` 리스트 표시

#### 5-4. 문자열 필터 `| split`

```liquid
{% assign techs = project.tech | split: ", " %}
{% for tech in techs %}
  <span class="tag">{{ tech }}</span>
{% endfor %}
```

- **입력**: `"Python, Django, React"`
- **처리**: `, `로 분리하여 배열로 만듦
- **출력**: `["Python", "Django", "React"]`
- **결과**: 각 항목에 대해 `<span class="tag">` 생성

---

## CSS 스타일링 분석

**파일**: `assets/css/style.css`

### 1. CSS 기본 구조

```css
/* 1. Reset (브라우저 기본 스타일 제거) */
* { margin: 0; padding: 0; box-sizing: border-box; }

/* 2. CSS 변수 정의 */
:root { --bg-primary: #0f172a; ... }

/* 3. 기본 요소 스타일 */
body { ... }

/* 4. 컴포넌트별 스타일 */
.hero { ... }
.card { ... }

/* 5. 반응형 디자인 */
@media (max-width: 768px) { ... }

/* 6. 애니메이션 */
@keyframes fadeInUp { ... }
```

### 2. CSS Variables (CSS 변수)

**정의 위치**: `:root { }` 블록

```css
:root {
  /* 색상 팔레트 */
  --bg-primary: #0f172a;      /* 진한 네이비 배경 */
  --bg-secondary: #1e293b;    /* 조금 밝은 배경 */
  --text-primary: #f1f5f9;    /* 흰색에 가까운 텍스트 */
  --accent-primary: #3b82f6;  /* 파란색 강조 */
  --accent-secondary: #8b5cf6; /* 보라색 강조 */
  
  /* 그림자 */
  --shadow-card: 0 4px 12px rgba(0, 0, 0, 0.4);
  
  /* 폰트 */
  --font-primary: 'Inter', sans-serif;
}
```

**사용 방법**:
```css
.card {
  background: var(--bg-card);
  color: var(--text-primary);
  box-shadow: var(--shadow-card);
}
```

**장점**:
- ✅ 색상 변경 시 한 곳만 수정하면 전체 적용
- ✅ 디자인 일관성 유지
- ✅ 다크/라이트 테마 전환 시 용이

### 3. 레이아웃 기술

#### 3-1. Flexbox (1차원 레이아웃)

```css
.hero {
  display: flex;
  align-items: center;       /* 세로 중앙 정렬 */
  justify-content: center;   /* 가로 중앙 정렬 */
}
```

- **사용 위치**: Hero 섹션, Social Links
- **역할**: 요소를 가운데 정렬

#### 3-2. CSS Grid (2차원 레이아웃)

```css
.cards-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
  gap: 2rem;
}
```

- **의미**:
  - `auto-fill`: 공간이 허용하는 만큼 열 자동 생성
  - `minmax(350px, 1fr)`: 최소 350px, 남은 공간 균등 분배
  - `gap: 2rem`: 카드 사이 간격 32px
- **결과**: 화면 크기에 따라 자동으로 1열, 2열, 3열로 변경

### 4. 색상 시스템

#### 다크 테마 색상 팔레트

| 변수명 | 색상 코드 | 용도 |
|--------|---------|------|
| `--bg-primary` | `#0f172a` | 메인 배경 (진한 네이비) |
| `--bg-secondary` | `#1e293b` | 서브 배경 (조금 밝은 네이비) |
| `--bg-card` | `#1e293b` | 카드 배경 |
| `--text-primary` | `#f1f5f9` | 주요 텍스트 (거의 흰색) |
| `--text-secondary` | `#cbd5e1` | 보조 텍스트 (밝은 회색) |
| `--text-muted` | `#94a3b8` | 약한 텍스트 (회색) |
| `--accent-primary` | `#3b82f6` | 파란색 강조 |
| `--accent-secondary` | `#8b5cf6` | 보라색 강조 |

#### 그라디언트 효과

```css
--accent-gradient: linear-gradient(135deg, #3b82f6 0%, #8b5cf6 100%);
```

- **적용 위치**:
  - Hero 섹션 제목 (텍스트 배경)
  - 섹션 제목 하단 밑줄
  - 스킬 프로그레스 바

### 5. 애니메이션

#### 5-1. Keyframe 애니메이션

```css
@keyframes fadeInUp {
  from {
    opacity: 0;              /* 투명 */
    transform: translateY(30px);  /* 아래에서 */
  }
  to {
    opacity: 1;              /* 불투명 */
    transform: translateY(0);     /* 원위치로 */
  }
}
```

**적용**:
```css
.hero h1 {
  animation: fadeInUp 0.8s ease-out 0.2s both;
  /*         이름    시간  효과   딜레이  */
}
```

- `0.8s`: 0.8초 동안 애니메이션
- `ease-out`: 끝날 때 천천히
- `0.2s`: 0.2초 후 시작
- `both`: 시작/끝 상태 유지

#### 5-2. Hover 효과 (Transition)

```css
.card {
  transition: all 0.3s ease;  /* 모든 속성 0.3초 동안 부드럽게 변화 */
}

.card:hover {
  transform: translateY(-5px);  /* 위로 5px 이동 */
  box-shadow: var(--shadow-card-hover);  /* 그림자 변경 */
  border-color: var(--accent-primary);   /* 테두리 파란색 */
}
```

**효과**: 카드에 마우스를 올리면 위로 살짝 떠오르며 파란 테두리 표시

#### 5-3. 무한 애니메이션 (Float)

```css
@keyframes float {
  0%, 100% { transform: translateY(0px); }
  50% { transform: translateY(-20px); }  /* 중간에 위로 20px */
}

.hero::before {
  animation: float 6s ease-in-out infinite;
  /* 6초마다 위아래로 천천히 움직임 */
}
```

**적용 위치**: Hero 섹션의 배경 원 (장식 효과)

### 6. 반응형 디자인 (Media Query)

```css
@media (max-width: 768px) {
  .hero h1 {
    font-size: 2.5rem;  /* 모바일에서 제목 크기 줄임 */
  }
  
  .cards-grid {
    grid-template-columns: 1fr;  /* 모바일에서 1열로 */
  }
  
  .social-links {
    flex-direction: column;  /* 세로 나열 */
  }
}
```

- **의미**: 화면 너비가 768px 이하일 때 스타일 변경
- **효과**: 모바일에서도 읽기 편한 레이아웃

---

## JavaScript 동작 분석

**위치**: `index.html` 하단의 `<script>` 태그

### 전체 코드

```javascript
// Intersection Observer for scroll animations
const observerOptions = {
  threshold: 0.1,              // 10%가 보이면 트리거
  rootMargin: '0px 0px -50px 0px'  // 하단 50px 마진
};

const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {  // 화면에 보이면
      entry.target.classList.add('visible');  // 'visible' 클래스 추가
    }
  });
}, observerOptions);

// Observe all cards and sections
document.querySelectorAll('.card, .section').forEach(el => {
  el.classList.add('fade-in');  // 처음엔 숨김 상태
  observer.observe(el);         // 관찰 시작
});

// Smooth scroll for anchor links
document.querySelectorAll('a[href^="#"]').forEach(anchor => {
  anchor.addEventListener('click', function (e) {
    e.preventDefault();
    const target = document.querySelector(this.getAttribute('href'));
    if (target) {
      target.scrollIntoView({
        behavior: 'smooth',
        block: 'start'
      });
    }
  });
});
```

### 기능 1: 스크롤 애니메이션 (Intersection Observer)

#### 작동 원리

1. **초기 상태**: 모든 `.card`와 `.section`에 `fade-in` 클래스 추가 (투명)
2. **관찰**: Intersection Observer가 요소가 화면에 들어오는지 감시
3. **트리거**: 요소의 10%가 화면에 보이면 `visible` 클래스 추가
4. **효과**: CSS의 `.fade-in.visible` 스타일이 적용되어 페이드인 효과

#### CSS 연동

```css
.fade-in {
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.6s ease-out, transform 0.6s ease-out;
}

.fade-in.visible {
  opacity: 1;
  transform: translateY(0);
}
```

### 기능 2: 부드러운 스크롤 (Smooth Scroll)

```javascript
document.querySelectorAll('a[href^="#"]').forEach(anchor => {
  anchor.addEventListener('click', function (e) {
    e.preventDefault();  // 기본 점프 동작 막기
    const target = document.querySelector(this.getAttribute('href'));
    if (target) {
      target.scrollIntoView({
        behavior: 'smooth',  // 부드럽게 스크롤
        block: 'start'       // 상단 정렬
      });
    }
  });
});
```

- **적용 대상**: `#education`, `#skills` 같은 앵커 링크
- **효과**: 클릭하면 해당 섹션으로 부드럽게 스크롤

---

## 데이터 관리 방식 (YAML)

### YAML이란?

**YAML** (YAML Ain't Markup Language)은 사람이 읽기 쉬운 데이터 직렬화 포맷입니다.

#### JSON vs YAML 비교

**JSON** (기계가 읽기 편함):
```json
{
  "name": "Python",
  "level": 90,
  "category": "Language"
}
```

**YAML** (사람이 읽기 편함):
```yaml
name: Python
level: 90
category: Language
```

### `_data` 폴더 구조

```
_data/
├── links.yml           ← 소셜 링크
├── education.yml       ← 학력
├── career.yml          ← 경력
├── skills.yml          ← 기술 스택
├── projects.yml        ← 프로젝트
├── publications.yml    ← 논문
└── additional.yml      ← 자격증/수상
```

### 예시 1: `education.yml`

```yaml
- degree: "석사, 컴퓨터공학"
  school: "한양대학교 ERICA"
  location: "경기도 안산시"
  period: "2024.03 - 2026.02"
  gpa: "GPA 4.16/4.5"

- degree: "학사, 정보통신공학"
  school: "성균관대학교"
  location: "경기도 수원시"
  period: "2016.03 - 2023.08"
  gpa: "GPA 3.24/4.5"
```

**HTML에서 사용**:
```liquid
{% for edu in site.data.education %}
  <h3>{{ edu.degree }}</h3>
  <div>{{ edu.school }}</div>
  <span>{{ edu.period }}</span>
{% endfor %}
```

### 예시 2: `skills.yml` (중첩 구조)

```yaml
categories:
  - category: "Programming Languages"
    skills:
      - name: "Python"
        level: 90
      - name: "C/C++"
        level: 75
  
  - category: "Deep Learning Frameworks"
    skills:
      - name: "PyTorch"
        level: 85
      - name: "TensorFlow"
        level: 70
```

**HTML에서 사용** (2중 반복문):
```liquid
{% for category in site.data.skills.categories %}
  <h3>{{ category.category }}</h3>
  {% for skill in category.skills %}
    <div>{{ skill.name }} - {{ skill.level }}%</div>
  {% endfor %}
{% endfor %}
```

### 예시 3: `projects.yml` (복잡한 구조)

```yaml
- title: "AI 챗봇 프로젝트"
  title_en: "AI Chatbot Project"
  organization: "ABC 회사"
  period: "2025.01 - 2025.06"
  role: "백엔드 개발자"
  description: "GPT 기반 고객 응대 챗봇 개발"
  achievements:
    - "응답 정확도 95% 달성"
    - "일 평균 1000건 문의 자동 처리"
  tech: "Python, FastAPI, OpenAI API, Docker"
```

**주요 필드 설명**:
- `title`: 프로젝트 제목 (필수)
- `achievements`: 리스트 형태 (여러 항목)
- `tech`: 쉼표로 구분된 문자열 (HTML에서 `split` 필터 사용)

---

## 배포 프로세스

### 전체 흐름

```
로컬 수정 → Git Push → GitHub Actions → Jekyll Build → GitHub Pages 배포
```

### 단계별 설명

#### 1️⃣ 로컬에서 콘텐츠 수정

```bash
# _data/projects.yml 파일 수정
vim _data/projects.yml

# 변경사항 확인 (옵션)
bundle exec jekyll serve
# → http://localhost:4000 에서 미리보기
```

#### 2️⃣ Git에 커밋 및 푸시

```bash
git add .
git commit -m "프로젝트 추가: AI 챗봇"
git push origin main
```

#### 3️⃣ GitHub Actions 자동 빌드

GitHub 저장소의 **Settings → Pages**에서 Source를 "GitHub Actions"로 설정하면:

1. `main` 브랜치에 푸시할 때마다 자동 빌드
2. Jekyll이 `_data/*.yml` + `index.html` → 순수 HTML 생성
3. `_site/` 폴더의 결과물을 `gh-pages` 브랜치에 배포

#### 4️⃣ GitHub Pages에서 서빙

- **URL**: `https://yjjonatanlee.github.io/`
- **업데이트 시간**: 보통 1-2분 내

### 배포 확인 방법

1. GitHub 저장소의 **Actions** 탭 확인
   - ✅ 녹색 체크: 빌드 성공
   - ❌ 빨간 X: 빌드 실패 (로그 확인)

2. 웹사이트 접속
   - 브라우저 캐시 새로고침: `Ctrl+Shift+R` (Windows) / `Cmd+Shift+R` (Mac)

---

## 추가 학습 자료

### 초보자를 위한 단계별 학습 경로

#### 1단계: HTML/CSS 기초
- **MDN Web Docs**: [HTML 튜토리얼](https://developer.mozilla.org/ko/docs/Learn/HTML)
- **MDN Web Docs**: [CSS 튜토리얼](https://developer.mozilla.org/ko/docs/Learn/CSS)
- **생활코딩**: [WEB1 - HTML & Internet](https://opentutorials.org/course/3084)

#### 2단계: JavaScript 기초
- **MDN Web Docs**: [JavaScript 기초](https://developer.mozilla.org/ko/docs/Learn/JavaScript)
- **모던 JavaScript 튜토리얼**: [javascript.info](https://ko.javascript.info/)

#### 3단계: Jekyll 이해
- **Jekyll 공식 문서**: [jekyllrb.com](https://jekyllrb.com/docs/)
- **Liquid 템플릿**: [Liquid 문법](https://shopify.github.io/liquid/)

#### 4단계: Git & GitHub
- **Pro Git 책**: [온라인 무료](https://git-scm.com/book/ko/v2)
- **GitHub Pages 가이드**: [공식 문서](https://docs.github.com/ko/pages)

### 주요 개념별 참고 자료

| 개념 | 추천 자료 |
|-----|---------|
| CSS Flexbox | [CSS Tricks - Flexbox Guide](https://css-tricks.com/snippets/css/a-guide-to-flexbox/) |
| CSS Grid | [CSS Tricks - Grid Guide](https://css-tricks.com/snippets/css/complete-guide-grid/) |
| Intersection Observer | [MDN - Intersection Observer](https://developer.mozilla.org/ko/docs/Web/API/Intersection_Observer_API) |
| YAML 문법 | [Learn YAML in Y Minutes](https://learnxinyminutes.com/docs/yaml/) |
| SEO 최적화 | [Google Search Central](https://developers.google.com/search/docs) |

---

## 이 프로젝트로 배울 수 있는 것들

### ✅ 웹 개발 기초 개념
- [x] HTML의 의미론적 구조 (Semantic HTML)
- [x] CSS 레이아웃 (Flexbox, Grid)
- [x] CSS 애니메이션과 트랜지션
- [x] JavaScript DOM 조작
- [x] 반응형 웹 디자인

### ✅ 현대적 웹 개발 패턴
- [x] 템플릿 엔진 (Liquid)
- [x] 데이터 주도 개발 (YAML 데이터 분리)
- [x] 컴포넌트 기반 설계 (카드 시스템)
- [x] CSS 변수 활용 (재사용성)

### ✅ DevOps & 배포
- [x] Git 버전 관리
- [x] GitHub Pages 배포
- [x] CI/CD (GitHub Actions)
- [x] 정적 사이트 생성 (SSG)

### ✅ 웹 최적화
- [x] SEO (검색 엔진 최적화)
- [x] 성능 최적화 (폰트 preload, 이미지 최적화)
- [x] 웹 접근성 (Semantic HTML, ARIA)

---

## 다음 단계: 프로젝트 커스터마이징

### 쉬운 수정부터 시작하기

#### 레벨 1: 색상 변경
`assets/css/style.css`의 CSS 변수 수정:
```css
:root {
  --accent-primary: #10b981;  /* 파란색 → 초록색 */
  --accent-secondary: #f59e0b; /* 보라색 → 주황색 */
}
```

#### 레벨 2: 콘텐츠 추가
`_data/projects.yml`에 새 프로젝트 추가:
```yaml
- title: "새 프로젝트"
  period: "2026.01 - 2026.03"
  description: "프로젝트 설명"
  tech: "Python, React"
```

#### 레벨 3: 새 섹션 추가
`index.html`에 새 섹션 추가:
```html
<section class="section" id="blog">
  <div class="container">
    <h2 class="section-title">블로그</h2>
    <!-- 콘텐츠 추가 -->
  </div>
</section>
```

---

## 문제 해결 (Troubleshooting)

### Q1: 로컬 서버가 실행되지 않아요
```bash
# Ruby와 Bundler 설치 확인
ruby -v
bundle -v

# Gemfile 의존성 재설치
bundle install

# Jekyll 서버 실행
bundle exec jekyll serve
```

### Q2: CSS 변경이 반영되지 않아요
- 브라우저 캐시 삭제: `Cmd+Shift+R` (Mac) / `Ctrl+Shift+R` (Windows)
- Jekyll 서버 재시작

### Q3: GitHub Pages 배포가 안 돼요
1. **Settings → Pages** 확인
   - Source: GitHub Actions 선택
2. **Actions** 탭에서 빌드 로그 확인
3. `_config.yml`의 `url` 확인:
   ```yaml
   url: "https://USERNAME.github.io"
   ```

---

## 마치며

이 문서를 통해 웹 이력서 프로젝트의 기술 스택과 구조를 이해하셨기를 바랍니다. 

**핵심 요약**:
1. **Jekyll**: YAML 데이터 → HTML 변환
2. **HTML**: 구조 (Liquid 템플릿)
3. **CSS**: 디자인 (변수, Flexbox, Grid, 애니메이션)
4. **JavaScript**: 동적 효과 (스크롤 애니메이션)
5. **YAML**: 콘텐츠 데이터 관리
6. **GitHub Pages**: 자동 배포

모르는 부분이 있다면 위의 학습 자료를 참고하시고, 직접 코드를 수정해보며 학습하시는 것을 추천드립니다!

---

**작성일**: 2026-02-09  
**작성자**: Antigravity AI Assistant  
**프로젝트 버전**: 1.0
