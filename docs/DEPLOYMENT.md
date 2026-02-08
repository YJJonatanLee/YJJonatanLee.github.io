# 배포 가이드

이 문서는 웹 이력서를 GitHub Pages에 배포하는 방법을 설명합니다.

## 📍 현재 배포 상태

- **배포 URL**: https://yjjonatanlee.github.io/
- **저장소**: https://github.com/YJJonatanLee/YJJonatanLee.github.io
- **자동 배포**: GitHub Actions 사용

---

## 🚀 초기 배포 (완료)

### 1단계: GitHub 저장소 생성
1. https://github.com/new 접속
2. Repository name: `YJJonatanLee.github.io`
3. Public 선택
4. Create repository 클릭

### 2단계: 코드 푸시
```bash
git remote add origin https://github.com/YJJonatanLee/YJJonatanLee.github.io.git
git branch -M main
git push -u origin main
```

### 3단계: GitHub Pages 활성화
1. 저장소 → Settings → Pages
2. Source: `main` 브랜치 선택
3. Save 클릭

---

## 🔄 콘텐츠 업데이트 및 재배포

### 콘텐츠 수정
1. `_data` 폴더의 YAML 파일 수정
2. Git commit & push

```bash
# 변경사항 확인
git status

# 파일 추가
git add .

# 커밋
git commit -m "docs: Update career information"

# 푸시 (자동 배포 트리거)
git push origin main
```

### 배포 확인
1. GitHub 저장소 → Actions 탭
2. 최신 워크플로우 확인
3. 1-2분 후 https://yjjonatanlee.github.io/ 접속

---

## 🛠 문제 해결

### 배포 실패
**문제**: Actions에서 빌드 실패
**해결**:
1. Actions 탭에서 오류 로그 확인
2. Jekyll 빌드 오류 수정
3. 재푸시

### 404 Not Found
**문제**: 사이트 접속 불가
**해결**:
1. Settings → Pages에서 Source 확인
2. 저장소 이름이 `YJJonatanLee.github.io`인지 확인
3. 배포 완료까지 1-2분 대기

### Push 인증 오류
**문제**: `Authentication failed`
**해결**:
Personal Access Token 생성:
1. GitHub → Settings → Developer settings
2. Personal access tokens → Tokens (classic)
3. Generate new token (classic)
4. `repo` 권한 체크
5. 생성된 토큰을 비밀번호 대신 사용

---

## 🎯 고급 배포 옵션

### 커스텀 도메인 (선택)
1. 도메인 구매 (예: namecheap, godaddy)
2. DNS 설정:
   ```
   A    @    185.199.108.153
   A    @    185.199.109.153
   A    @    185.199.110.153
   A    @    185.199.111.153
   ```
3. GitHub Pages → Custom domain에 도메인 입력
4. Enforce HTTPS 체크

### 브랜치 전략
- `main`: 프로덕션 (배포용)
- `develop`: 개발 중인 기능
- `feature/*`: 새 기능 개발

```bash
# 새 기능 개발
git checkout -b feature/add-blog-section
# ... 작업 ...
git commit -m "feat: Add blog section"
git push origin feature/add-blog-section

# PR 생성 후 main에 merge
```

---

## 📊 배포 모니터링

### GitHub Actions
- **위치**: 저장소 → Actions 탭
- **확인사항**:
  - Build and Deploy 워크플로우 성공 여부
  - 빌드 시간 (보통 1-2분)
  - 오류 로그

### Google Search Console (선택)
1. https://search.google.com/search-console 접속
2. 사이트 등록
3. sitemap.xml 제출: `https://yjjonatanlee.github.io/sitemap.xml`

---

## 🔒 보안

### HTTPS
- GitHub Pages는 자동으로 HTTPS 제공
- Settings → Pages → Enforce HTTPS 체크 확인

### 환경 변수
민감한 정보는 GitHub Secrets에 저장:
1. 저장소 → Settings → Secrets and variables → Actions
2. New repository secret 클릭
3. Name과 Value 입력

---

## ✅ 배포 체크리스트

배포 전 확인사항:
- [ ] 로컬에서 `bundle exec jekyll serve` 테스트
- [ ] 모든 링크 작동 확인
- [ ] 반응형 디자인 확인
- [ ] SEO 메타 태그 확인
- [ ] Git commit message 작성
- [ ] `git push origin main` 실행
- [ ] GitHub Actions 성공 확인
- [ ] 배포된 사이트 접속 테스트
