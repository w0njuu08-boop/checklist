# 하루 기록 · 플래너 (PWA)

습관 · 일정 · 할 일 · 기분 · 수면을 기록하는 개인용 하루 플래너입니다.
GitHub Pages에 올리면 브라우저에서 "홈 화면에 추가"로 진짜 앱처럼 설치해서 쓸 수 있어요.

## 폴더 구성

```
index.html          ← 앱 본체 (이 파일 하나로 동작)
manifest.json        ← 앱 이름/아이콘/색상 설정 (PWA 필수 파일)
service-worker.js    ← 오프라인에서도 열리게 해주는 캐시 스크립트
icons/
  icon-512.png        ← 앱 아이콘 (512x512)
  icon-192.png         ← 앱 아이콘 (192x192)
  icon-180.png         ← iOS 홈 화면용 아이콘
  favicon.png           ← 브라우저 탭 아이콘
```

## 1. GitHub 저장소 만들고 올리기

1. GitHub에서 새 저장소를 만듭니다 (예: `haru-record`). Public으로 만들어야 무료로 Pages를 쓸 수 있어요.
2. 이 폴더 안의 모든 파일을 저장소에 그대로 올립니다 (웹에서 "Add file → Upload files" 로 드래그해도 되고, git 커맨드를 써도 됩니다).

```bash
git init
git add .
git commit -m "하루 기록 플래너 초기 배포"
git branch -M main
git remote add origin https://github.com/내아이디/haru-record.git
git push -u origin main
```

## 2. GitHub Pages 켜기

1. 저장소 페이지 → **Settings → Pages**
2. **Source**를 `Deploy from a branch`로, **Branch**를 `main` / `(root)`로 설정 후 저장
3. 1~2분 뒤 상단에 뜨는 주소로 접속하면 앱이 열립니다.
   (`https://내아이디.github.io/haru-record/` 형태)

## 3. 휴대폰에 앱처럼 설치하기

- **안드로이드(Chrome)**: 접속 후 메뉴(⋮) → "홈 화면에 추가" → 설치
- **아이폰(Safari)**: 접속 후 공유 버튼(⬆️) → "홈 화면에 추가"

설치하면 아이콘이 홈 화면에 생기고, 브라우저 주소창 없이 앱처럼 전체 화면으로 열려요. 인터넷이 없어도 이전에 열었던 내용은 오프라인으로 계속 볼 수 있어요 (기록 데이터는 휴대폰 브라우저에 저장돼요).

## 4. 아이콘

세이지 배경의 캘린더 아이콘으로 이미 적용되어 있어요. `icons/` 안에는 실제 사용되는 4개 파일만 들어있습니다.

- `icon-512.png`, `icon-192.png` — 안드로이드/PWA 아이콘
- `icon-180.png` — 아이폰 홈 화면 아이콘
- `favicon.png` — 브라우저 탭 아이콘

다른 디자인으로 바꾸고 싶으면 말씀해주세요, 새 시안 만들어서 이 4개 파일만 교체해드릴게요.

## 참고: 진짜 앱스토어용 앱으로 만들고 싶다면

지금 상태로도 "홈 화면에 추가"만 하면 앱처럼 쓸 수 있지만, Play스토어/앱스토어에 정식 등록하고 싶다면 아래 무료 도구로 이 GitHub Pages 주소를 그대로 패키징할 수 있어요.

- **PWABuilder** (https://www.pwabuilder.com) — GitHub Pages 주소만 입력하면 Android/iOS 패키지를 만들어줍니다.

## 데이터 관련 안내

기록은 서버가 아니라 **브라우저(휴대폰)에만** 저장돼요 (localStorage). 그래서:
- 다른 기기에서 열면 기록이 안 보여요 (동기화 없음)
- 브라우저 데이터/캐시를 지우면 기록도 함께 삭제돼요

여러 기기 동기화나 백업이 필요하면 알려주세요, 이어서 만들어드릴게요.
