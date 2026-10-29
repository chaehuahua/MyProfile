# 채다연 포트폴리오 (MyProfile)

전북대학교 바이오메디컬공학부 3학년 채다연의 개인 소개 웹사이트입니다.
Hugo의 [Terminal 테마](https://github.com/panr/hugo-theme-terminal)를 사용해 만들고, GitHub Actions로 GitHub Pages에 자동 배포합니다.

- 공개 사이트: <https://chaehuahua.github.io/MyProfile/>
- 저장소: <https://github.com/chaehuahua/MyProfile>
- 배포 기록(Actions): <https://github.com/chaehuahua/MyProfile/actions>

> 테마 원본 README는 [THEME-README.md](THEME-README.md)로 옮겨 두었습니다.

## 필요한 도구와 버전

| 도구 | 버전 | 용도 |
| --- | --- | --- |
| Hugo **extended** | 0.154.5 | 사이트 빌드 (`.github/workflows/hugo-pages.yml`의 `HUGO_VERSION`과 같게 맞춤) |
| Python | 3.9 이상 (Actions는 3.12) | 배포용 빌드 스크립트 `.github/pages_build.py` 실행 |
| Git | 아무 최신 버전 | 커밋·push |

Hugo는 [공식 릴리스 페이지](https://github.com/gohugoio/hugo/releases/tag/v0.154.5)에서 운영체제에 맞는 `hugo_extended_0.154.5_...` 파일을 받아 PATH에 넣습니다.
설치 확인: `hugo version` 결과에 `v0.154.5`와 `+extended`가 보여야 합니다.

## 내 컴퓨터에서 사이트 확인하기

```bash
# 1) 저장소 받기
git clone https://github.com/chaehuahua/MyProfile.git
cd MyProfile

# 2) 미리보기 서버 실행 (저장하면 자동 새로고침)
cd site
hugo server --config config.toml,pages.json
# → 브라우저에서 http://localhost:1313/MyProfile/ 열기, 끝내려면 Ctrl+C
```

배포와 똑같은 방식으로 빌드해 보려면 저장소 맨 위 폴더에서 실행합니다.

```bash
python .github/pages_build.py --build
# → public/ 폴더에 결과가 생기고 "빌드 완료"가 출력되면 성공
```

## 내용을 고치려면 어떤 파일을 열까

실제 사이트는 **`site/` 폴더**에서 만들어집니다. 저장소 맨 위의 `layouts/`, `assets/`, `exampleSite/` 등은 테마 원본 ZIP에 들어 있던 파일로, 빌드에 쓰이지 않습니다.

| 고칠 것 | 파일 |
| --- | --- |
| 사이트 제목·부제·메뉴·푸터 문구 | `site/config.toml` |
| 홈 화면 소개 | `site/content/_index.md` |
| 소개(관심 분야·학습 목표·기술) | `site/content/about.md` |
| 대표 활동 글과 캡처 이미지 | `site/content/posts/first-webpage/` (`index.md` + `.jpg`) |
| 새 활동 글 추가 | `site/content/posts/새-폴더/index.md` 만들기 |
| 색상·글꼴·모바일 메뉴 등 스타일 | `site/static/style.css` (테마 CSS를 덮어씀) |
| 화면 구조(메뉴·로고·본문 바로가기·404) | `site/layouts/` (테마 템플릿을 같은 이름으로 덮어씀) |
| 테마 색상 변수 | `site/themes/template/assets/css/terminal.css` |
| 배포 주소·Hugo 테마 설정 | `site/pages.json` (배포 스크립트가 만든 파일, 보통 고치지 않음) |

## 수정 후 배포하고 확인하기

```bash
git add .
git commit -m "content: 바꾼 내용을 한 줄로 설명"
git push origin main
```

1. **Actions 확인:** <https://github.com/chaehuahua/MyProfile/actions> 에서 방금 push한 커밋의 `Deploy Hugo to GitHub Pages` 실행이 노란 점(진행 중) → 초록 체크(성공)로 바뀌는지 봅니다. `build`와 `deploy` 두 단계가 모두 성공해야 합니다.
2. **실패했다면:** 빨간 X를 눌러 `Build and fix project URL paths` 단계의 로그에서 `ERROR` 줄을 확인합니다. 대부분 Markdown 앞부분(`+++ ... +++`)의 따옴표 누락이나 잘못된 파일 경로입니다.
3. **공개 화면 확인:** 1~2분 뒤 <https://chaehuahua.github.io/MyProfile/> 를 새로고침합니다. 이전 화면이 보이면 `Ctrl+Shift+R`(Mac은 `Cmd+Shift+R`)로 캐시 없이 다시 엽니다.

처음 한 번만 필요한 설정: GitHub 저장소 **Settings → Pages → Build and deployment → Source**를 **GitHub Actions**로 선택합니다.
