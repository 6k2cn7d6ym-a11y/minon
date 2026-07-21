# MINONHOMEPAGE — Claude Code / 팀 세션 작업 가이드

유한회사 민온(MINON Ltd.) 공식 홈페이지. 도메인 `minon.kr`, GitHub Pages 정적 호스팅.

이 문서는 **부트스트랩 문서**다. 지금은 빈칸이 많다. 대표님(Jim)이 결정할 때마다 이 문서를 갱신해서 살아있는 기준점으로 쓴다.

두 청중이 함께 본다:
1. **Jim이 Claude Code로 직접 이 리포에 편집할 때** — 아래 규칙 그대로.
2. **민온 디스패처 팀 세션이 이 프로젝트 방을 열 때** — 현재 상태·미결 결정 파악.

---

## 0. 가장 중요한 것

1. **파일 구조가 극단적으로 단순하다.** 루트에 `index.html` 한 개, `CNAME` 한 개, 끝. 빌드 스텝 없음, 프레임워크 없음, 번들러 없음. 이 단순성이 자산이다 — 함부로 부풀리지 말 것.
2. **배포는 GitHub Pages 자동.** `main` 브랜치에 push하면 minon.kr에 반영된다. 별도 배포 커맨드 없음. **push 전 대표님 확인 필수.**
3. **도메인은 `minon.kr`.** `CNAME` 파일이 이걸 고정한다. 삭제·수정 절대 금지. (git log를 보면 과거에 CNAME 삭제/재생성이 반복됐음 — 다시는 안 됨.)
4. **`index.html` 한 파일에 HTML·CSS·JS 전부 인라인.** 현재 1083줄. 분리 여부는 대표님 결정 사안 (§5 참조).
5. **툴 rejection ≠ 대표님 거부.** 시스템 rejection·타임아웃일 수 있음. "거부하셨다"고 단정하지 말고 상태만 보고.

---

## 1. 작업자(Jim) 프로필

- 유한회사 MINON 대표. 1인 개발자 + 실전 트레이더.
- **좋은 말만 하면 화낸다.** 근거 있는 반박 환영. 동의만 하는 어시스턴트 싫어함.
- **결정은 직접 내림.** 디자인·카피·구조 결정은 옵션 제시하고 **물어봄**. 멋대로 정하지 않음.
- **감정 없는 논리·빠른 반복.**
- **여성.** 총무 업무(한울회·한빛회) 병행.

---

## 2. 현재 상태 (2026-07-17 기준)

### 파일 구조

```
MINONHOMEPAGE/
├── CNAME              — "minon.kr" (한 줄, 절대 건드리지 말 것)
├── index.html         — 1083줄, HTML+CSS+JS 인라인 단일 파일
├── .gitignore         — sandbox/ 제외
├── sandbox/           — 개발팀 사원 팸 실험 공간 (.gitignore, 커밋 안 됨)
├── worklog/           — 팀 세션 일별 워크로그 폴더 (README.md만 있음, 실 작업 기록 아직 없음)
└── .git/              — origin: github.com/6k2cn7d6ym-a11y/minon
```

### 최근 git 이력 (요약)

| 커밋 | 내용 |
|---|---|
| `5bbe1c4` | P-05 잔잔, P-06 모아내, P-07 오롯 제품 카드 추가 (2026-07-09) |
| `7f76f9b` | 파일 업로드 (초기) |
| CNAME 삭제/생성 반복 | 과거 이력. 다시는 반복 금지. |

### 사이트 구조 (`index.html` 현재 내용)

- **Header** — 브랜드 마크 + `About` / `Products` / `Contact` 앵커 내비
- **Hero** — "민온" 대형 세리프, "사람들의 일상에 닿는 소프트웨어를 만듭니다."
- **About** — 법인 소개, 설립일 2025.07.02, "빠르게 크는 것보다 오래 쓰이는 것"
- **Products** — P-01 ~ P-07:
  - P-01 클럽매치온 (Live · clubmatchon.netlify.app)
  - P-02 소유온 (In Development · Personal)
  - P-03 RECON (Personal Tool)
  - P-04 스틸온 (In Operation · B2B)
  - P-05 잔잔 (Live · janjan.pages.dev)
  - P-06 모아내 (Live · moane.pages.dev)
  - P-07 오롯 (Live · orot.pages.dev)
- **Contact** — `contact@minon.kr`, "Response within 3 business days"
- **Footer** — Seoul, KR / © MMXXV MINON Ltd.

### 디자인 토큰 (있는 그대로)

```
--paper: #F3EFE3        (배경 종이)
--paper-deep: #EBE6D4   (카드 배경)
--paper-warm: #E8E1CB
--ink: #0F0F0E          (본문)
--ink-soft: #3A3731
--ink-muted: #7A7669
--hairline: #C8C1AD
--accent: #8C3D26       (포인트)
--accent-soft: #B05A3C

폰트: Pretendard Variable / Instrument Serif / JetBrains Mono
```

톤: 종이 질감(SVG grain, body::after) + 세리프 대형 타이틀. 조용한 스튜디오 톤.

---

## 3. 배포 흐름

### 지금

1. `index.html` 편집
2. **대표님 확인**
3. `git add index.html && git commit -m "..." && git push origin main`
4. GitHub Pages가 minon.kr에 자동 반영 (보통 1~2분)

### 안 하는 것

- `firebase deploy` (여긴 GitHub Pages임, dispatcher랑 다름)
- CNAME 수정·삭제
- `.github/workflows/` 생성 (아직 필요 없음, GitHub Pages 기본 빌드로 충분)

---

## 4. 편집 시 지켜야 할 규칙

### HTML/CSS/JS 편집
1. `index.html` 하나만 편집 (지금 구조 유지)
2. 로컬 검증: 브라우저에서 `file:///Users/jim/projects/MINONHOMEPAGE/index.html` 열어 확인
3. **대표님 승인 후** push
4. push 후 minon.kr에서 실사용 확인 (캐시 있음, 필요시 hard reload)

### 제품 카드 추가 (P-08~)
- `id="products"` 섹션의 `.product-list` 안에 `<div class="product ...">` 또는 `<a class="product clickable ...">` 추가
- 인덱스 `P—08` 형식 (em dash `—`, 하이픈 아님), 이름(한글) + `.en` 영문/부제, 설명 1~2줄, `.tag`, `.product-status`
- Live 링크면 `<a href="..." target="_blank" rel="noopener noreferrer">`, 개발 중이면 `<div>`

### 카피·문구 수정
- **대표님이 직접 정한다.** 어시스턴트는 옵션만 제시. "이 문장이 낫습니다" 같은 단독 판단 금지.

### 워크로그 규칙
- 유의미한 작업 완료 시 `worklog/YYYY-MM-DD.md`에 append
- 파일 없으면 새로 생성 (worklog/README.md 형식 참고)
- 팀 세션이든 CLI 세션이든 동일 적용

---

## 5. 대표님이 채워야 할 빈칸 (미결 결정)

지금 이 문서에 명확히 답이 없는 것들. 결정 나올 때마다 여기 지우고 §2·§4로 옮긴다.

- **[미정] SEO·성능 목표** — 현재 Lighthouse 점수 측정 안 됨. 목표치 없음.
- **[미정] 애널리틱스** — GA·Plausible·자체 로그 중 뭐 붙일지, 안 붙일지 결정 없음.
- **[미정] 다국어(en) 정식 지원 여부** — 지금은 곳곳에 영문 부제만 섞음. 완전 이중언어 페이지 만들지 미정.
- **[미정] 채용·회사 소개 페이지 확장 여부** — 지금은 About 한 섹션. 팀·연혁·비전 등 추가할지 미정.
- **[미정] 블로그·릴리스 노트 섹션** — 각 앱 업데이트 소식 홈페이지에 실을지 미정. 실으면 정적 파일이면 관리 부담.
- **[미정] 단일 파일 유지 vs 분리** — `index.html` 1083줄이 어디까지 커질지. CSS/JS 별도 파일로 뽑을 임계점 결정 필요.
- **[미정] 제품 상세 페이지** — 각 제품 카드 클릭 시 자체 상세 페이지로 갈지, 현재처럼 외부 사이트로만 링크할지.
- **[미정] `contact@minon.kr` 실제 수신처** — 메일 포워딩·MX 설정 상태 확인 필요.
- **[미정] 개인정보처리방침·이용약관 페이지** — B2B(스틸온)·PWA 배포로 필요해질 시점 미정.
- **[미정] 코드 저장소 소유권** — 현재 origin이 `6k2cn7d6ym-a11y/minon` (개인 계정처럼 보임). MINON 조직 계정으로 옮길지 결정 필요.

---

## 6. 소소한 것

- **origin:** `git@github.com:6k2cn7d6ym-a11y/minon.git`
- **호스팅:** GitHub Pages (main 브랜치 루트)
- **도메인:** `minon.kr` (CNAME 파일이 고정)
- **이메일:** `contact@minon.kr` (수신 확인 필요 — 위 §5 참조)
- **설립일 (사이트 표기):** 2025.07.02
- **sandbox/ 폴더:** 개발팀 사원 팸 실험 공간. `.gitignore`에서 제외. 여기서 라이브러리 실험은 결재 불요, 프로덕션 승격 시 팀장이 의존성 결재 상신.

---

## 7. 다음 단계 후보 (Roadmap · 우선순위 없음)

대표님이 순서 정하는 자리. 지금은 옵션만 나열.

- [ ] Lighthouse 실측 → 성능·접근성 개선 (특히 SVG grain의 렌더 비용)
- [ ] `og:image` 실제 이미지 파일 추가 (지금은 og image 없음, 링크 미리보기 밋밋함)
- [ ] `robots.txt` · `sitemap.xml` 추가
- [ ] 제품 카드 hover·focus 상태 재점검 (a11y)
- [ ] 각 제품 상세 페이지 여부 결정 (§5)
- [ ] 채용 페이지 or 회사 이야기 페이지 (§5)
- [ ] `contact@minon.kr` 수신·응답 파이프라인 (dispatcher 팀 세션에 연결할지?)
- [ ] repo 소유권 이전 (§5)
- [ ] 릴리스 노트/블로그 (§5)
- [ ] P-08 이후 신규 제품 추가 준비 (소유온 런칭 시, 기타 신제품)

---

## 8. 다른 프로젝트와의 관계

이 홈페이지가 소개하는 제품들의 실제 저장소 (참고용):

| 홈페이지 표기 | 실제 폴더 (`~/projects/`) | 상태 |
|---|---|---|
| P-01 클럽매치온 | `CLUBMATCHON` / `clubmatchon-v2` / `CLUBMATCHONMOBILE` | Live |
| P-02 소유온 | (미확인 — 폴더 이름 확인 필요) | Dev |
| P-03 RECON | `RECON` / `recon-bot` / `ReconKR` | Personal |
| P-04 스틸온 | (미확인) | B2B 운영 중 |
| P-05 잔잔 | `janjan` / `janjan_buildkit` / `janjan_cap` | Live |
| P-06 모아내 | `MOANE` | Live |
| P-07 오롯 | `OROT` / `OROT_manual` | Live |

**민온 디스패처(`minon-dispatcher`)는 홈페이지에 노출 안 됨** — 내부 운영 도구라 의도된 비공개. 유지.

---

_이 문서는 부트스트랩용이다. 결정이 쌓이면 §5·§7이 줄고 §2·§4가 두꺼워지도록 유지한다._
