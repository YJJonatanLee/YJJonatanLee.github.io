# 이영준 | AI/ML Engineer

![Hero Section](https://raw.githubusercontent.com/YJJonatanLee/YJJonatanLee.github.io/main/.github/hero-preview.png)

**🌐 Live Website**: [https://yjjonatanlee.github.io/](https://yjjonatanlee.github.io/)

AI/ML 엔지니어 이영준의 웹 이력서입니다. Jekyll과 GitHub Pages를 사용하여 제작되었습니다.

---

## ✨ 주요 특징

- 🎨 **다크 테마 카드 기반 디자인** - 전문적이고 현대적인 느낌
- 📱 **완전 반응형** - 모바일, 태블릿, 데스크톱 모든 기기 지원
- 🔧 **쉬운 관리** - YAML 데이터 파일로 콘텐츠 관리
- ⚡ **빠른 로딩** - GitHub Pages 기반 정적 사이트
- 🎭 **애니메이션 효과** - 스크롤 시 부드러운 페이드인 효과

---

## 🛠 기술 스택

- **Frontend**: HTML5, CSS3, JavaScript
- **Static Site Generator**: Jekyll 4.2.2
- **Hosting**: GitHub Pages
- **Framework**: Liquid Template Engine
- **Build**: GitHub Actions

---

## 📂 프로젝트 구조

```
.
├── _config.yml              # Jekyll 설정
├── _data/                   # 데이터 파일 (YAML)
│   ├── links.yml           # 연락처/소셜 링크
│   ├── education.yml       # 학력
│   ├── career.yml          # 경력
│   ├── skills.yml          # 기술 스택
│   ├── projects.yml        # 프로젝트
│   ├── publications.yml    # 논문/발표
│   └── additional.yml      # 자격증/수상/기타
├── assets/
│   └── css/
│       └── style.css       # 커스텀 스타일
├── index.html              # 메인 페이지
├── Gemfile                 # Ruby 의존성
└── README.md               # 프로젝트 문서
```

---

## 🚀 로컬 실행 방법

### 1. 저장소 클론
```bash
git clone https://github.com/YJJonatanLee/YJJonatanLee.github.io.git
cd YJJonatanLee.github.io
```

### 2. 의존성 설치
```bash
bundle install
```

### 3. 로컬 서버 실행
```bash
bundle exec jekyll serve
```

`http://localhost:4000`에서 확인하실 수 있습니다.

---

## 📝 콘텐츠 수정 방법

### 새 프로젝트 추가
`_data/projects.yml` 파일에 다음 형식으로 추가:

```yaml
- title: "프로젝트 제목"
  period: "2026.01 - 2026.03"
  organization: "회사/기관명"
  description: "프로젝트 설명"
  achievements:
    - "주요 성과 1"
    - "주요 성과 2"
  tech: "Python, Django, React"
  type: "project"
```

### 새 경력 추가
`_data/career.yml` 파일 수정

### 기술 스택 업데이트
`_data/skills.yml` 파일 수정

### 변경사항 배포
```bash
git add .
git commit -m "콘텐츠 업데이트"
git push origin main
```

GitHub Actions가 자동으로 빌드 및 배포합니다 (보통 1-2분 소요).

---

## 🎨 디자인 특징

### 색상 팔레트
- **배경**: `#0f172a` (Deep Navy)
- **카드**: `#1e293b` (Slate)
- **텍스트**: `#f1f5f9` (Light Gray)
- **액센트**: `#3b82f6` → `#8b5cf6` (Blue to Purple Gradient)

### 카드 효과
- 호버 시 위로 5px 이동
- 부드러운 블루 그림자 효과
- 트랜지션: 0.3s ease

---

## 📊 섹션 구성

1. **Hero** - 이름, 직무, 소개, 연락처
2. **학력** - 석사/학사 학위
3. **경력** - 주요 경력 및 프로젝트
4. **기술 스택** - 카테고리별 스킬 (프로그레스 바)
5. **프로젝트 & 연구** - 주요 프로젝트 및 논문
6. **논문 & 발표** - 학술 발표 이력
7. **자격증 & 수상** - 자격증 및 수상 경력
8. **기타 경력** - 강사, 인턴 등

---

## 🔄 업데이트 이력

- **2026.02.08** - 초기 배포
  - 다크 테마 카드 기반 디자인 구현
  - 7개 섹션 구성
  - GitHub Pages 배포

---

## 📧 연락처

- **Email**: younghe42286@gmail.com
- **GitHub**: [@YJJonatanLee](https://github.com/YJJonatanLee)

---

## 📄 라이선스

© 2026 이영준. All rights reserved.

---

**Built with ❤️ using Jekyll & GitHub Pages**
