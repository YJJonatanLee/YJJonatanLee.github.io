# 웹 이력서 프로젝트 Todo List

## 📋 프로젝트 개요
GitHub Pages와 Jekyll을 사용하여 `이력서-이영준.docx`의 내용을 웹 이력서로 변환

---

## ✅ 할 일 목록

### 1단계: 준비 및 분석
- [ ] `이력서-이영준.docx` 파일 내용 확인 및 분석
- [ ] 필요한 섹션 정리 (학력, 경력, 스킬, 프로젝트 등)
- [ ] 이력서 디자인 컨셉 결정

### 2단계: Jekyll 프로젝트 설정
- [ ] Jekyll 설치 확인 (`jekyll --version`)
- [ ] Jekyll 프로젝트 초기화
- [ ] GitHub Pages 호환 설정 (`_config.yml`)
- [ ] 필요한 플러그인 및 테마 선정
- [ ] 프로젝트 디렉토리 구조 생성

### 3단계: 데이터 파일 구조 설계 (쉬운 관리를 위해)
> 💡 **핵심**: `_data` 폴더에 YAML 파일로 관리하면 코드 수정 없이 내용만 쉽게 추가/수정 가능

- [ ] `_data` 폴더 생성
- [ ] `_data/links.yml` - 소셜 미디어 및 개인 링크 (GitHub, LinkedIn, 블로그 등)
- [ ] `_data/career.yml` - 경력 사항 (회사명, 기간, 직책, 업무 등)
- [ ] `_data/projects.yml` - 프로젝트 목록 (제목, 설명, 기술스택, 링크 등)
- [ ] `_data/publications.yml` - 논문 및 출판물 (제목, 저자, 학회/저널, 년도 등)
- [ ] `_data/education.yml` - 학력 사항
- [ ] `_data/skills.yml` - 기술 스택 및 스킬
- [ ] `_data/certifications.yml` - 자격증 및 수상 (선택사항)

**데이터 파일 예시 구조:**
```yaml
# _data/career.yml
- company: "회사명"
  position: "직책"
  period: "2023.01 - 현재"
  description: "업무 설명"
  achievements:
    - "주요 성과 1"
    - "주요 성과 2"
```

### 4단계: 콘텐츠 작성
- [ ] 메인 페이지 (`index.md` 또는 `index.html`) 작성
- [ ] 개인 정보 섹션 작성
- [ ] 데이터 파일 기반 동적 섹션 템플릿 작성
  - [ ] 링크 섹션 (for loop으로 `site.data.links` 출력)
  - [ ] 경력 섹션 (for loop으로 `site.data.career` 출력)
  - [ ] 프로젝트 섹션 (for loop으로 `site.data.projects` 출력)
  - [ ] 논문 섹션 (for loop으로 `site.data.publications` 출력)
  - [ ] 학력 섹션 (for loop으로 `site.data.education` 출력)
  - [ ] 스킬 섹션 (for loop으로 `site.data.skills` 출력)

### 4단계: 디자인 및 스타일링
- [ ] CSS 파일 작성 (`assets/css/style.css`)
- [ ] 반응형 디자인 구현 (모바일, 태블릿, 데스크톱)
- [ ] 색상 테마 적용
- [ ] 타이포그래피 설정
- [ ] 아이콘 및 이미지 추가

### 5단계: 기능 구현
- [ ] 네비게이션 메뉴 구현
- [ ] 섹션 간 부드러운 스크롤 추가
- [ ] 연락처 정보 (이메일, GitHub, LinkedIn 등) 링크 추가
- [ ] PDF 다운로드 버튼 추가 (선택사항)
- [ ] 다크모드 지원 (선택사항)

### 6단계: 로컬 테스트
- [ ] 로컬에서 Jekyll 서버 실행 (`bundle exec jekyll serve`)
- [ ] 모든 페이지 및 링크 동작 확인
- [ ] 다양한 화면 크기에서 테스트
- [ ] 브라우저 호환성 확인

### 7단계: GitHub Pages 배포
- [ ] GitHub 저장소 생성 (`username.github.io` 형식 권장)
- [ ] 프로젝트 파일 커밋 및 푸시
- [ ] GitHub Pages 설정 활성화
- [ ] 배포 확인 및 URL 접속 테스트

### 8단계: 최종 점검 및 개선
- [ ] SEO 최적화 (메타 태그, 설명 등)
- [ ] 성능 최적화 (이미지 압축, CSS/JS 최소화)
- [ ] 접근성 개선 (alt 태그, ARIA 라벨 등)
- [ ] 오타 및 맞춤법 검사
- [ ] Google Analytics 추가 (선택사항)

---

## 📝 참고사항
- Jekyll 공식 문서: https://jekyllrb.com/docs/
- GitHub Pages 가이드: https://docs.github.com/en/pages
- 무료 Jekyll 테마: http://jekyllthemes.org/

## 💡 추가 아이디어
- [ ] 블로그 섹션 추가
- [ ] 포트폴리오 갤러리
- [ ] 애니메이션 효과
- [ ] 다국어 지원 (한국어/영어)
