# 콘텐츠 관리 가이드

이 문서는 웹 이력서의 콘텐츠를 쉽게 수정하는 방법을 설명합니다.

## 📂 데이터 파일 구조

모든 콘텐츠는 `_data` 폴더의 YAML 파일로 관리됩니다:

```
_data/
├── links.yml           # 연락처 링크
├── education.yml       # 학력
├── career.yml          # 경력 및 프로젝트
├── skills.yml          # 기술 스택
├── projects.yml        # 개인 프로젝트
├── publications.yml    # 논문/발표
└── additional.yml      # 자격증/수상/기타
```

---

## 🔧 파일별 수정 방법

### 1. links.yml - 연락처 정보

```yaml
- name: "이메일"
  icon: "email"
  url: "mailto:your-email@example.com"

- name: "GitHub"
  icon: "github"
  url: "https://github.com/your-username"

- name: "전화번호"
  icon: "phone"
  url: "tel:010-1234-5678"
```

**수정 시 주의사항**:
- `url`의 형식 유지 (`mailto:`, `https://`, `tel:`)
- 링크 추가 시 동일한 형식으로 추가

---

### 2. education.yml - 학력

```yaml
- degree: "석사"
  school: "대학교 이름"
  major: "전공"
  location: "서울, 대한민국"
  period: "2020.03 - 2022.02"
  gpa: "4.3 / 4.5"
```

**추가 방법**: 위 형식을 복사하여 리스트에 추가

---

### 3. career.yml - 경력

```yaml
- company: "(주) 회사명"
  position: "직책"
  division: "부서"
  period: "2021.03 - 2022.03"
  duration: "1년 1개월"
  description: "회사 및 역할 설명"
  
  projects:
    - name: "프로젝트명"
      period: "2021.03 - 2021.09"
      role: "자신 인식 모델 개발"
      tasks:
        - "작업 내용 1"
        - "작업 내용 2"
      tech: "Python, TensorFlow, OpenCV"
```

**프로젝트 추가**: `projects` 리스트에 동일한 형식으로 추가

---

### 4. skills.yml - 기술 스택

```yaml
categories:
  - category: "프로그래밍 언어"
    skills:
      - name: "Python"
        level: 90
      - name: "JavaScript"
        level: 75
```

**스킬 추가**:
1. 적절한 카테고리 찾기
2. `skills` 리스트에 추가
3. `level`은 0-100 사이 값 (프로그레스 바 표시)

---

### 5. projects.yml - 프로젝트

```yaml
- title: "프로젝트 제목"
  title_en: "Project Title in English"  # 선택사항
  period: "2024.01 - 2024.03"
  organization: "기관/회사명"
  role: "역할"  # 선택사항
  description: "프로젝트 설명"
  achievements:
    - "주요 성과 1"
    - "주요 성과 2"
  tech: "Python, Django, React"
  type: "project"  # project, research, thesis
```

---

### 6. publications.yml - 논문/발표

```yaml
- title: "논문 제목 (영문)"
  title_kr: "논문 제목 (한글)"
  authors: "첫번째저자, 두번째저자, 세번째저자"
  year: 2023
  venue: "학회명"  # 논문인 경우
  organization: "기관명"  # 발표인 경우
  type: "학위논문"  # 학위논문, 포스터발표 등
```

---

### 7. additional.yml - 자격증/수상

#### 수상
```yaml
awards:
  - name: "수상명"
    issuer: "주최기관"
    date: "2023.12"
    description: "수상 내용"
```

#### 자격증
```yaml
certifications:
  - name: "자격증명"
    issuer: "발급기관"
    date: "2023.06"
```

#### 기타 경력
```yaml
other_experiences:
  - title: "강사"
    organization: "기관명"
    period: "2023.03 - 2023.06"
    description: "강의 내용"
```

---

## 💡 수정 팁

### YAML 형식 주의사항

1. **들여쓰기**: 스페이스 2칸 사용 (탭 사용 금지)
   ```yaml
   # ✅ 올바른 예
   - name: "항목"
     value: "값"
   
   # ❌ 잘못된 예 (들여쓰기 오류)
   - name: "항목"
   value: "값"
   ```

2. **특수문자**: 콜론(`:`)이나 따옴표(`"`)가 포함된 경우 전체를 따옴표로 감싸기
   ```yaml
   description: "머신러닝: 딥러닝 모델 개발"
   ```

3. **리스트**: 각 항목 앞에 `-` 붙이기
   ```yaml
   skills:
     - name: "Python"
     - name: "JavaScript"
   ```

4. **여러 줄**: `|` 또는 `>` 사용
   ```yaml
   description: |
     첫 번째 줄
     두 번째 줄
   ```

### 문법 검증

수정 후 YAML 문법 확인:
- 온라인 도구: https://www.yamllint.com/
- VS Code: YAML 확장 설치
- 로컬 테스트: `bundle exec jekyll serve`

---

## 🔄 변경사항 적용 방법

### 로컬 테스트
```bash
# Jekyll 서버 실행
bundle exec jekyll serve

# 브라우저에서 확인
# http://localhost:4000
```

### 배포
```bash
# 변경사항 스테이징
git add _data/

# 커밋 (의미 있는 메시지 작성)
git commit -m "docs: Update career section"

# GitHub에 푸시
git push origin main
```

1-2분 후 https://yjjonatanlee.github.io/ 에서 반영 확인

---

## 📝 커밋 메시지 컨벤션

```
feat: 새 기능 추가
docs: 문서 수정 (이력서 내용 업데이트)
fix: 버그 수정
style: 디자인 변경
refactor: 코드 리팩토링
```

예시:
```bash
git commit -m "docs: Add new project to projects.yml"
git commit -m "docs: Update career information"
git commit -m "feat: Add new skill category"
```

---

## ⚠️ 주의사항

1. **백업**: 수정 전 파일 백업 권장
2. **문법 확인**: Push 전 로컬에서 반드시 테스트
3. **이미지**: 이미지는 `assets/images/` 폴더에 저장
4. **Git 이력**: 큰 변경 전 새 브랜치 생성 권장

---

## 🆘 문제 해결

### Jekyll 빌드 실패
```bash
# 오류 메시지 확인
bundle exec jekyll serve

# YAML 문법 오류일 가능성 높음
# yamllint로 검증
```

### 변경사항이 반영되지 않음
1. 브라우저 캐시 삭제 (Cmd+Shift+R)
2. GitHub Actions 확인
3. 1-2분 대기 후 재확인

### Git Push 오류
```bash
# 최신 코드 받아오기
git pull origin main

# 충돌 해결 후
git push origin main
```
