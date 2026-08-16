# 권혁선 개발자 포트폴리오

Vue 3, TypeScript, Vite로 제작한 GitHub Pages용 단일 페이지 포트폴리오입니다.

## 내 정보로 변경하기

`src/App.vue` 상단의 `profile`에서 이메일과 GitHub 주소를 변경하세요. 프로젝트와 기술 스택도 같은 파일의 `projects`, `skills` 배열에서 수정할 수 있습니다.

## 로컬 실행

```bash
npm install
npm run dev
```

## GitHub Pages 배포

1. GitHub에서 새 저장소를 만듭니다.
2. 이 프로젝트를 저장소의 `main` 브랜치에 올립니다.
3. **Settings → Pages → Build and deployment → Source**에서 **GitHub Actions**를 선택합니다.
4. Actions 작업이 끝나면 Pages 주소로 사이트가 공개됩니다.

저장소 이름과 관계없이 동작하도록 Vite의 `base`를 상대 경로로 설정했습니다.
