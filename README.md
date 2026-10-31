# Petakin Toolbox — 설치·관리 가이드

## 폴더 구성
- `index.html` : 방문자가 보는 사이트 (홈 즐겨찾기 + 전체 툴)
- `data/tools.json` : 툴 목록
- `data/categories.json` : 카테고리 목록과 순서
- `data/site.json` : 사이트 이름
- `icons/` : 아이콘 이미지
- `admin/` : 관리자 화면 (Decap CMS)

## 1. GitHub에 올리기 (명령어 없이 가능)
1. github.com 에서 새 저장소(Repository)를 만들어요. 이름 예: `petakin-toolbox`. Private이어도 괜찮아요.
2. 저장소 화면에서 **Add file → Upload files**를 누르고, 이 폴더 **안의 내용물 전체**를 끌어다 놓은 뒤 **Commit changes**를 눌러요.
   - `index.html`이 저장소 최상위에 있어야 해요.
   - 기본 브랜치 이름이 `main`이 아니라면 `admin/config.yml`의 `branch:` 값을 같은 이름으로 바꿔요.

## 2. Netlify에 연결하기
1. Netlify에서 **Add new project → Import an existing project → GitHub**를 선택하고, 위 저장소를 골라요.
2. Build command와 Publish directory는 **비워둔 채로** Deploy를 눌러요.
3. 1~2분 뒤 `xxxx.netlify.app` 주소가 생겨요. 프로젝트 설정에서 이름을 바꿀 수 있어요.

## 3. 관리자 로그인 켜기 (Identity + Git Gateway)
1. 프로젝트의 **Identity** 설정에서 Identity를 활성화해요.
2. **Registration**을 **Invite only(초대 전용)** 으로 바꿔요. 아무나 가입하지 못하게 하려면 꼭 필요해요.
3. 같은 화면 아래쪽 **Services → Git Gateway**에서 **Enable Git Gateway**를 눌러요.
4. **Invite users**로 본인(과 관리자들)의 이메일을 초대해요.
5. 받은 초대 메일의 링크를 누르면 사이트가 열리고, 비밀번호를 정하면 자동으로 `/admin/`으로 이동해요.

Netlify 화면의 메뉴 이름이나 위치는 바뀔 수 있어요. 안 보이면 프로젝트 설정에서 "Identity"를 검색하세요.

## 4. 툴 관리하기
- 사이트 오른쪽 위 **관리** 또는 `https://내주소/admin/`으로 들어가요.
- **툴 → 툴 목록**에서 추가·수정·삭제하고 **Publish(게시)** 를 누르면 GitHub에 저장되고, 1분쯤 뒤 사이트에 반영돼요.
- **한줄 니즈**가 가장 중요해요. 이 툴을 만든 이유를 한 문장으로 쓰면, 사이트에서 이름보다 크게 카피처럼 보여요. 홈에서는 즐겨찾기의 니즈가 큰 글씨로 돌아가며 나와요.
- **홈 즐겨찾기 순서**에 1~5를 넣으면 홈에 큰 아이콘으로 나와요. 0은 표시하지 않아요.
- 아이콘 이미지는 툴 편집 화면에서 바로 업로드할 수 있어요. 정사각형 이미지를 권장해요.
- 카테고리는 **설정 → 카테고리**에서 관리해요. 목록 순서가 사이트에 표시되는 순서예요. ID는 툴과 연결되는 값이라 정한 뒤에는 바꾸지 마세요.
- 모든 변경 기록은 GitHub에 남아서, 실수해도 이전 버전으로 되돌릴 수 있어요.

## 내 컴퓨터에서 미리 보기
`index.html`을 더블클릭하면 데이터를 못 불러와요. 폴더에서 터미널을 열고 아래 명령을 실행한 뒤 http://localhost:8000 으로 여세요.
```
python3 -m http.server 8000
```
(관리자 화면은 Netlify에 올린 뒤에만 동작해요.)
