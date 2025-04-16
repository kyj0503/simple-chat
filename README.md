# React + TypeScript + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type-aware lint rules:

```js
export default tseslint.config({
  extends: [
    // Remove ...tseslint.configs.recommended and replace with this
    ...tseslint.configs.recommendedTypeChecked,
    // Alternatively, use this for stricter rules
    ...tseslint.configs.strictTypeChecked,
    // Optionally, add this for stylistic rules
    ...tseslint.configs.stylisticTypeChecked,
  ],
  languageOptions: {
    // other options...
    parserOptions: {
      project: ['./tsconfig.node.json', './tsconfig.app.json'],
      tsconfigRootDir: import.meta.dirname,
    },
  },
})
```

You can also install [eslint-plugin-react-x](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-x) and [eslint-plugin-react-dom](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-dom) for React-specific lint rules:

```js
// eslint.config.js
import reactX from 'eslint-plugin-react-x'
import reactDom from 'eslint-plugin-react-dom'

export default tseslint.config({
  plugins: {
    // Add the react-x and react-dom plugins
    'react-x': reactX,
    'react-dom': reactDom,
  },
  rules: {
    // other rules...
    // Enable its recommended typescript rules
    ...reactX.configs['recommended-typescript'].rules,
    ...reactDom.configs.recommended.rules,
  },
})
```

# Simple Chat

실시간 채팅을 위한 React 웹 애플리케이션입니다.

## 기능

- GitHub 계정을 통한 로그인
- 실시간 채팅
- 다양한 채팅방 지원

## 환경 설정

이 프로젝트를 실행하기 위해서는 환경 변수 설정이 필요합니다. `.env.example` 파일을 참조하여 `.env` 파일을 생성해주세요.

1. 프로젝트 루트에 `.env` 파일 생성
2. 다음 환경 변수를 설정:

```
# API URL for backend services
VITE_API_URL=http://localhost:8080

# WebSocket URL for chat
VITE_WS_URL=http://localhost:8080/ws/chat

# Message topics and prefixes
VITE_TOPIC_PREFIX=/topic
VITE_APP_PREFIX=/app

# GitHub OAuth settings
VITE_GITHUB_CLIENT_ID=your_github_client_id_here
VITE_REDIRECT_URI=http://localhost:5173/callback
```

> **참고**: Vite 프로젝트에서는 모든 환경 변수가 `VITE_` 접두사로 시작해야 브라우저에서 접근할 수 있습니다.

## 설치 및 실행

```bash
# 의존성 설치
npm install

# 개발 서버 실행
npm run dev

# 빌드
npm run build
```

## 보안 참고사항

- `.env` 파일은 절대로 git에 커밋하지 마세요. 
- GitHub OAuth 클라이언트 ID는 안전하게 관리해야 합니다.
- 프로덕션 환경에서는 적절한 보안 조치를 취해야 합니다.
