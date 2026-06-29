# Jiyeon Kang — 블로그

작업물 / AI 공부 / 논문 분석을 기록하기 위한 Jekyll 기반 GitHub Pages 블로그입니다.
가독성을 최우선으로 두고 디자인했습니다 (넓은 줄 간격, 적당한 글 너비, 차분한 색).

---

## 1. 폴더 구조

```
.
├── _config.yml          # 사이트 제목, 설명 등 기본 설정
├── _data/categories.yml # 카테고리 이름(작업물/AI 공부/논문 분석) 정의
├── _layouts/             # 페이지 틀 (default / home / post / category)
├── _includes/            # head, header, footer 조각
├── _posts/                # 실제 글 (파일명 규칙: YYYY-MM-DD-제목.md)
├── assets/css/style.css  # 전체 디자인
├── index.md               # 홈
├── projects.md             # "작업물" 목록 페이지
├── ai-study.md              # "AI 공부" 목록 페이지
├── paper-review.md           # "논문 분석" 목록 페이지
└── about.md                   # 소개 페이지
```

---

## 2. GitHub에 올리기

### 저장소 만들기

GitHub 계정 이름이 `Jiyeon-Kang-125` 이므로, **개인 메인 사이트**로 쓰려면
저장소 이름을 정확히 아래와 같이 만들어야 합니다.

```
Jiyeon-Kang-125.github.io
```

(다른 이름으로 만들면 `https://jiyeon-kang-125.github.io/저장소이름/` 형태가 되고,
이때는 `_config.yml`의 `baseurl: ""` 을 `baseurl: "/저장소이름"` 으로 바꿔주세요.)

### 업로드 명령어

이 폴더를 통째로 다운로드한 뒤, 터미널에서:

```bash
cd jiyeon-blog
git init
git add .
git commit -m "블로그 초기 세팅"
git branch -M main
git remote add origin https://github.com/Jiyeon-Kang-125/Jiyeon-Kang-125.github.io.git
git push -u origin main
```

### GitHub Pages 켜기

1. 저장소 → **Settings** → **Pages**
2. **Source**: `Deploy from a branch` 선택
3. **Branch**: `main` / `(root)` 선택 후 저장

몇 분 후 `https://jiyeon-kang-125.github.io` 에서 확인할 수 있어요.
(저장소 이름이 `username.github.io` 형태면 보통 자동으로 Pages가 켜져 있습니다.)

---

## 3. 새 글 쓰는 방법

`_posts` 폴더에 다음 규칙으로 파일을 만드세요.

```
파일명: YYYY-MM-DD-제목.md   (예: 2026-07-03-rag-구조-정리.md)
```

파일 맨 위에 이렇게 적어주세요 (front matter):

```yaml
---
layout: post
title: "글 제목"
date: 2026-07-03
categories: [ai-study]      # projects / ai-study / paper-review 중 하나
excerpt: "목록에 보일 한두 줄 요약"
---

본문은 여기부터 마크다운으로 씁니다.
```

- `categories: [projects]` → 작업물 페이지에 자동으로 모임
- `categories: [ai-study]` → AI 공부 페이지에 자동으로 모임
- `categories: [paper-review]` → 논문 분석 페이지에 자동으로 모임

카테고리를 비워두면(`categories: []`) 홈의 "최근 글"에만 보이고
세 카테고리 페이지에는 나타나지 않습니다 (공지성 글 등에 사용).

---

## 4. 글쓰기에 쓸 수 있는 요소

`_posts/2026-06-29-welcome.md` 에 실제 사용 예시가 들어있습니다.

| 하고 싶은 것 | 쓰는 방법 |
|---|---|
| 형광펜 강조 | `<mark>강조할 텍스트</mark>` |
| 여백 노트(보충 설명) | `<aside class="note">내용</aside>` |
| 코드 블록 | \`\`\`python 처럼 언어명과 함께 |
| 인용 | `> 인용문` |

---

## 5. 로컬에서 미리보기 (선택)

Ruby가 설치되어 있다면:

```bash
gem install bundler jekyll
bundle init
echo 'gem "github-pages", group: :jekyll_plugins' >> Gemfile
bundle install
bundle exec jekyll serve
```

`http://localhost:4000` 에서 확인할 수 있어요. 필수는 아니고, GitHub에 push만 해도
GitHub Pages가 자동으로 빌드해줍니다.

---

## 6. 자주 바꾸게 될 곳

- **사이트 제목 / 한 줄 소개**: `_config.yml` 의 `title`, `tagline`
- **카테고리 이름**: `_data/categories.yml`
- **색상**: `assets/css/style.css` 맨 위 `:root { ... }` 의 `--moss`, `--indigo`, `--amber`
- **소개 글**: `about.md`
