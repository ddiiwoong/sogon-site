<!--
  ddiiwoong/sogon-site 의 **저장소 첫 화면** 원본이다. 게시 브랜치(`gh-pages`) 루트의
  `README.md` 로 올라간다 — GitHub 은 기본 브랜치의 README 를 저장소 페이지에 렌더하고,
  이 저장소의 기본 브랜치가 `gh-pages` 다.

  웹사이트 파일이 아니다. 그래서 `SITE_FILES`(= scripts/build-site.sh)에 넣지 않았고,
  대신 `scripts/publish-landing.sh` 의 `PROTECTED` 에 넣어 묵은 파일 스캔이 지우지 못하게
  했다. 고친 뒤에는 손으로 올린다:

    gh api repos/ddiiwoong/sogon-site/contents/README.md -X PUT \
      -f message=... -f branch=gh-pages -f sha=<현재 blob sha> \
      -f content=<base64>

  **버전 번호를 적지 않는다.** 이 파일은 `check_site_version.py` 의 검사 대상이 아니므로
  판올림 때 아무도 갱신하지 않는다 — 항상 최신을 가리키는 `/releases/latest` 로 링크한다.
-->

# Sogon

**말하면 커서에 들어갑니다.** 메뉴 바에 상주하는 macOS 받아쓰기 앱입니다. 전역 단축키를 누른 채
말하면 전사하고, 원하면 LLM으로 다듬어 녹음을 시작할 때 커서가 있던 자리에 넣습니다.

➡️ **[sogon.dev](https://sogon.dev/)** · [사용 설명서](https://sogon.dev/guide/) ·
[구성 흐름도](https://sogon.dev/architecture.html) ·
[문제 해결](https://sogon.dev/guide/docs/troubleshooting/) ·
[문의하기](https://github.com/ddiiwoong/sogon-site/issues/new/choose)

## 설치

```
brew install --cask ddiiwoong/tap/sogon
```

Homebrew를 쓰지 않으면 [최신 릴리스](https://github.com/ddiiwoong/sogon-site/releases/latest)에서
`Sogon.dmg`를 받아 열고 `Sogon.app`을 `/Applications`로 옮깁니다. 공개 릴리스라 로그인이
필요하지 않습니다. Developer ID로 서명하고 Apple 공증을 마친 빌드라 Gatekeeper 경고가 뜨지
않습니다.

| 요구 | |
| --- | --- |
| macOS | 14 (Sonoma) 이상 |
| 칩 | Apple Silicon (arm64) 전용 |

설치 뒤에는 Sogon이 직접 업데이트를 받습니다 — `brew upgrade`는 필요하지 않습니다.

## 이 저장소에 있는 것

배포와 웹사이트를 담습니다. **앱 소스 코드는 여기 없습니다** (공개하지 않습니다).

| | |
| --- | --- |
| Releases | `Sogon.dmg` — 서명·공증된 빌드 |
| `appcast.xml` | 인앱 업데이트 피드 (Sparkle) |
| `index.html` · `en.html` · `style.css` | 랜딩 페이지 |
| `architecture.html` · `architecture-en.html` | 구성 흐름도 — 층과 호출 방향 |
| `guide/` | 사용 설명서 (Docusaurus 빌드 산출물) |
| `.github/ISSUE_TEMPLATE/` | 이슈 양식 |
| Issues | 버그·질문·기능 제안 |

기본 브랜치가 `gh-pages`라서 저장소 첫 화면에 웹사이트 파일이 보입니다. 소스 트리가 아닙니다.

## 구성

앱 소스는 공개하지 않지만 **구조는 공개합니다.**
[구성 흐름도](https://sogon.dev/architecture.html)([en](https://sogon.dev/architecture-en.html))가
층과 호출 방향, 상태를 한 곳에 모으는 규칙, 프로토콜로 교체 가능한 지점을 담습니다. 소스 코드는
담지 않습니다.

## 문의

[이슈를 열어](https://github.com/ddiiwoong/sogon-site/issues/new/choose) 주세요 — 버그·질문·기능
제안 세 가지 양식이 있습니다. 버그라면 먼저
[문제 해결](https://sogon.dev/guide/docs/troubleshooting/)을 보시고, 거기 없으면
[진단 정보](https://sogon.dev/guide/docs/troubleshooting/diagnostics/)를 만들어 첨부해 주시면
왕복이 줄어듭니다.

---

## English

**Speak, and it lands at your cursor.** Sogon is a macOS dictation app that lives in the menu bar.
Hold a global shortcut, speak, and it transcribes — optionally cleaning the text up with an LLM —
then inserts it where your cursor was when you started.

➡️ **[sogon.dev/en.html](https://sogon.dev/en.html)** · [Guide](https://sogon.dev/guide/en/) ·
[Architecture](https://sogon.dev/architecture-en.html) ·
[Troubleshooting](https://sogon.dev/guide/en/docs/troubleshooting/) ·
[Open an issue](https://github.com/ddiiwoong/sogon-site/issues/new/choose)

```
brew install --cask ddiiwoong/tap/sogon
```

Or download `Sogon.dmg` from the
[latest release](https://github.com/ddiiwoong/sogon-site/releases/latest) — no sign-in needed. The
build is Developer ID signed and notarized by Apple. Requires macOS 14 (Sonoma) or later on Apple
Silicon. Sogon updates itself, so `brew upgrade` is not required.

This repository hosts the distribution artifacts and the website — **not the app's source code.**
Its default branch is `gh-pages`, which is why you see website files here rather than a source tree.
The source stays closed, but the structure does not: the
[architecture diagram](https://sogon.dev/architecture-en.html) covers the layers and the direction
calls flow, the rule that gathers state in one place, and which seams are swappable protocols.
