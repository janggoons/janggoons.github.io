# 장윤재 블로그 (janggoons.github.io)

Jekyll + [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/) 테마로 만든 블로그입니다.
GitHub에 올리기만 하면 GitHub Pages가 자동으로 사이트를 만들어 줍니다. 컴퓨터에 따로 설치할 것은 없습니다.

> 기존 `Dropbox/personal-website/`(HTML 한 페이지)의 내용은 모두 이 블로그의 About · Research · Lectures 페이지로 옮겼습니다.

## 폴더 구성

```
personal-blog/
├── _config.yml          ← 사이트 전체 설정 (제목, 프로필, 검색, 댓글)
├── index.html           ← 첫 화면 (소개 한 줄 + 최근 글 목록)
├── _posts/              ← ✍️ 블로그 글 (YYYY-MM-DD-제목.md)
├── _pages/              ← 고정 페이지 (About, Research, Books, Lectures, Activity, 카테고리·태그 모아보기)
├── _data/
│   ├── navigation.yml   ← 상단 메뉴
│   ├── publications.yml ← 📄 논문·발표·보고서·학위논문 (Research 페이지에 종류별·연도별 자동 표시)
│   ├── news.yml         ← 📰 활동 소식 (첫 화면 최근 5건 + Activity 페이지 전체)
│   └── badges.yml       ← 논문 배지 이름 (SSCI, KCI …)
├── _includes/pub-list.html ← 논문 목록 출력 틀 (수정할 일 거의 없음)
├── assets/css/main.scss ← 색상·글꼴·배지 디자인
├── assets/images/       ← 사진·그림
└── Gemfile              ← 내 컴퓨터에서 미리보기할 때만 사용
```

## 처음 배포하기 (한 번만)

1. https://github.com 에 `janggoons` 계정으로 로그인합니다.
2. 오른쪽 위 **+ → New repository**를 누르고, 이름을 **`janggoons.github.io`**로 정해 **Public**으로 만듭니다.
3. 이 폴더의 파일을 올립니다. 둘 중 편한 방법을 쓰세요.
   - **웹에서 올리기**: 저장소 화면의 **uploading an existing file** → 이 폴더 안의 파일과 폴더를 **모두 드래그** → Commit changes
     (`_`로 시작하는 폴더도 빠짐없이 올려야 합니다)
   - **Git 명령으로 올리기** (PowerShell):
     ```powershell
     cd C:\Users\owner\Dropbox\personal-blog
     git init -b main
     git add .
     git commit -m "블로그 시작"
     git remote add origin https://github.com/janggoons/janggoons.github.io.git
     git push -u origin main
     ```
4. 저장소 **Settings → Pages**에서 Source를 **Deploy from a branch**, Branch를 **main / (root)**로 지정합니다.
5. 2~3분 뒤 https://janggoons.github.io 에 접속합니다. 진행 상황은 저장소의 **Actions** 탭에서 볼 수 있습니다.

## 새 글 쓰기

`_posts/` 폴더에 `2026-10-01-ai-ethics-class.md` 같은 이름으로 파일을 만듭니다.
파일 이름에는 날짜와 영문 제목을 쓰고, 실제로 보이는 제목은 파일 안의 `title:`에 적습니다.

```markdown
---
title: "생성형 AI 윤리 수업을 마치고"
categories:
  - 강의
tags:
  - AI윤리
  - 수업설계
---

본문을 마크다운으로 씁니다.
```

- 카테고리를 `강의`로 지정한 글은 **Lectures** 페이지 아래에 자동으로 모입니다.
- 그림은 `assets/images/`에 넣고 본문에 `![설명](/assets/images/파일명.png)`로 넣습니다.
- 저장한 뒤 GitHub에 올리면(웹 업로드 또는 `git add . ; git commit -m "글 추가" ; git push`) 1~2분 뒤 반영됩니다.

## 논문 · 소식 추가하기

- **논문**: `_data/publications.yml`의 해당 종류(`kind`) 구역에 항목 하나를 추가합니다. Research 페이지에 연도별로 자동 정렬되어 표시됩니다. 형식은 파일 맨 위 설명을 참고하세요.
- **활동 소식**: `_data/news.yml` 맨 위에 `date`·`text`·`link`(선택) 세 줄을 추가합니다. 첫 화면에 바로 반영됩니다.
- **특강·강의**: `_pages/lectures.md`의 표에 한 줄 추가합니다.
- **저서**: `_pages/books.md`에 한 줄 추가합니다.

> 2026-09-30에 Google Sites(sites.google.com/view/janggoons) 내용을 모두 옮겼습니다. 이후로는 이 블로그를 기준으로 관리하세요.

## 아직 채우지 않은 것

| 항목 | 위치 |
|------|------|
| 프로필 사진 | `assets/images/profile.jpg`를 넣고 `_config.yml`의 `avatar:` 줄 주석(`#`) 해제 |
| Google Scholar · ORCID 주소 | `_config.yml`의 `author.links`에서 주석 해제 후 URL 입력 |
| 논문 DOI | `_data/publications.yml` 각 항목에 `doi:` 추가 (현재는 KCI·출판사 링크로 연결) |

## 선택 기능

### 댓글 켜기 (giscus, 무료)
1. 저장소 **Settings → General → Features**에서 **Discussions**를 켭니다.
2. https://github.com/apps/giscus 에서 앱을 설치하고, 이 저장소에 권한을 줍니다.
3. https://giscus.app/ko 에 저장소 이름을 넣으면 `repo_id`와 `category_id`가 나옵니다.
4. `_config.yml`의 `comments:` 부분에서 `provider: false`를 지우고, 주석 처리된 giscus 설정을 풀어 두 값을 채웁니다.

### 스킨(색 테마) 바꾸기
`_config.yml`의 `minimal_mistakes_skin`을 `air`, `mint`, `dark` 등으로 바꿉니다.
글자색·포인트 색은 `assets/css/main.scss`에서 조정합니다.

### 내 컴퓨터에서 미리보기 (선택)
[Ruby+Devkit](https://rubyinstaller.org/)을 설치한 뒤 다음을 실행합니다.
```powershell
cd C:\Users\owner\Dropbox\personal-blog
bundle install
bundle exec jekyll serve
```
그다음 브라우저에서 http://localhost:4000 을 엽니다.
