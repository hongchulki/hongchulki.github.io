# Chulki Hong — 개인 홈페이지

[Quarto](https://quarto.org) 로 만든 정적 사이트이며 GitHub Pages 로 배포합니다.
사이트의 기본 언어는 영어이고, 한국어 소개 페이지(`ko.qmd`)가 메뉴의 "한국어"로 연결됩니다.
마크다운 파일(`.qmd`)만 고치면 되고, `main` 브랜치에 올리면 GitHub Actions 가 자동으로 빌드·배포합니다.

## 처음 한 번만 하는 일

1. GitHub 에서 **공개(public)** 저장소를 만듭니다. 이름은 반드시 `hongchulki.github.io` 여야 합니다.
2. 이 폴더의 파일을 전부 그 저장소의 `main` 브랜치에 올립니다.
3. 저장소 **Settings → Pages → Build and deployment → Source** 를 **GitHub Actions** 로 바꿉니다.
4. 저장소의 **Actions** 탭에서 "Publish site" 작업이 끝나면(1–2분) `https://hongchulki.github.io` 에서 사이트가 열립니다.

## 아직 비워 둔 것 (나중에 채우는 법)

- **사진** — `profile.jpg` 를 이 폴더에 넣고, `index.qmd` 와 `ko.qmd` 머리말의 `# image: profile.jpg` 줄 주석을 풉니다.
- **이메일** — `_quarto.yml`(상단 메뉴 아이콘), `index.qmd`, `ko.qmd` 에 주석으로 남겨 둔 `envelope` 항목의 주석을 풀고 주소를 넣습니다.
- **저술 목록** — `publications.yml` 을 채운 뒤, `publications.qmd` 머리말의 `draft: true` 줄을 지우고 `_quarto.yml` 의 `Publications` 메뉴 주석을 풉니다. 그 전까지 이 페이지는 배포 사이트에 포함되지 않습니다.
- **CV** — `cv.qmd` 의 자리표시 항목(Field, University, Year 등)을 실제 내용으로 바꿉니다.

## 파일 구성

| 파일 | 역할 |
|---|---|
| `_quarto.yml` | 사이트 전체 설정 — 제목, 메뉴, 테마, 주소 |
| `index.qmd` | 첫 화면(영문 소개) |
| `ko.qmd` | 한국어 소개 |
| `research.qmd` | 연구 소개 |
| `publications.qmd` + `publications.yml` + `pubs.ejs` | 저술 목록. **항목은 `publications.yml` 에서만** 고치면 됨 |
| `posts.qmd` + `posts/` | 글 목록(Writing)과 개별 글 |
| `cv.qmd` | 이력 |
| `styles.scss` | 글꼴·간격 등 모양 조정 |
| `.github/workflows/publish.yml` | 자동 배포 설정 (손댈 필요 없음) |

## 자주 하는 일

**저술 추가** — `publications.yml` 에 한 덩어리를 추가합니다. 한글 논문은 제목·출처를 한글 그대로 적으면 됩니다.

```yaml
- year: 2026
  kind: Article          # Book / Article / Report / Translation / Chapter …
  title: "제목"
  venue: "학술지명, 00권 0호, 00–00쪽"
  url: "https://..."     # 없으면 줄 삭제
  note: "in Korean"      # 없으면 줄 삭제
```

**글 쓰기** — `posts/` 안에 폴더를 만들고 `index.qmd` 를 둡니다.

```
posts/2026-11-01-some-title/index.qmd
```

```markdown
---
title: "글 제목"
date: 2026-11-01
categories: [Essays]
description: "한 줄 요약"
lang: ko          # 한국어 글이면 이 줄을 넣고, 영어 글이면 빼세요
---

본문.
```

**소식 갱신** — `index.qmd`(영문) 과 `ko.qmd`(국문) 의 News / 최근 소식 목록을 고칩니다.

파일을 고친 뒤 GitHub 에 올리면(커밋·푸시, 또는 GitHub 웹 화면에서 직접 편집) 1–2분 뒤 사이트에 반영됩니다.

## 내 컴퓨터에서 미리 보기 (선택)

[quarto.org/docs/get-started](https://quarto.org/docs/get-started/) 에서 Quarto 를 설치한 뒤, 이 폴더에서

```
quarto preview
```

를 실행하면 브라우저에 실시간 미리보기가 뜹니다. 파일을 저장할 때마다 자동으로 다시 그립니다.

## 개인 도메인 (선택)

`hongchulki.com` 같은 도메인을 쓰려면 저장소 **Settings → Pages → Custom domain** 에 입력하고, 도메인 등록 업체에서 GitHub 안내대로 DNS 레코드를 추가하면 됩니다. HTTPS 는 자동으로 적용됩니다.
