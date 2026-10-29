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
