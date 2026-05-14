# 📈 삼성전자 주식 대시보드

실시간 삼성전자(005930) 주가 분석 대시보드 — 네이버 파이낸스 기반 기술적 지표, 반도체 섹터 비교, AI 매매신호 제공.

![Status](https://img.shields.io/badge/Status-Live-brightgreen) ![License](https://img.shields.io/badge/License-MIT-blue) ![Language](https://img.shields.io/badge/Language-한국어-red) ![Data](https://img.shields.io/badge/Data-Naver_Finance-03C75A)

---

## 🚀 라이브 데모

👉 **[GitHub Pages 데모 보기](https://your-username.github.io/samsung-dashboard)**

> `your-username`을 본인의 GitHub 아이디로 변경하세요.

---

## 📸 미리보기

| 영역 | 설명 |
|------|------|
| 상단 패널 | 삼성전자 / SK하이닉스 실시간 시세, USD 환산, 거래량 |
| 통계 카드 | 현재가 · 4주 최고/최저 · 거래량 · 거래대금 |
| 가격 차트 | 90일 일봉 + MA-20 + 매수/매도 신호 + 4주 범위 |
| RSI 차트 | 14일 RSI (과매수/과매도 구간 표시) |
| 반도체 섹터 | 삼성, SK하이닉스, TSMC, 엔비디아, 마이크론, 인텔 |
| AI 추천 게이지 | RSI + MACD 기반 종합 매매 추천 |
| 기술적 지표 표 | 섹터 동종 비교 + 7일 스파크라인 |
| 뉴스 피드 | 네이버 파이낸스 RSS 실시간 기사 |

---

## ✨ 주요 기능

| 기능 | 설명 |
|------|------|
| 📊 실시간 주가 | **네이버 파이낸스** 4단계 폴백 체계로 정확한 KRW 가격 조회 |
| 📈 기술적 지표 | MA-20, RSI(14), MACD(12/26/9) 실시간 계산 |
| 🎯 매매신호 | RSI 크로스오버 + MACD 시그널 기반 자동 매수/매도 표시 |
| 🔬 섹터 비교 | 국내외 반도체 6종목 동시 조회 + 스파크라인 |
| 🤖 AI 추천 | 점수 기반 투자 추천 반원 게이지 |
| 📰 뉴스 피드 | 네이버 파이낸스 RSS 연동 실시간 기사 |
| 💾 CSV 내보내기 | 90일 OHLCV + 지표 + 신호 데이터 다운로드 |
| 🔄 자동 갱신 | 5분마다 자동 갱신 + 수동 갱신 버튼 |

---

## 🛠 데이터 소스

이 대시보드는 **네이버 파이낸스**를 1차 데이터 소스로 사용하며, CORS 우회를 위해 공개 프록시를 경유합니다.

```
우선순위:
1. Naver Polling API   (polling.finance.naver.com — 가장 빠른 실시간)
2. Naver Mobile API    (m.stock.naver.com — 통합 시세)
3. Naver HTML 스크래핑 (finance.naver.com/item/main.naver)
4. Yahoo Finance KRX   (005930.KS — 최후 수단)
```

> ⚠️ **가격 검증:** 조회된 가격이 ₩100,000 미만이면 자동으로 다음 소스로 넘어갑니다.  
> 삼성전자는 2018년 50:1 액면분할 이후 현재 ₩280,000 ~ ₩300,000 수준에서 거래됩니다.

---

## 🚀 사용 방법

### 방법 1 — 로컬에서 바로 열기

```bash
git clone https://github.com/your-username/samsung-dashboard.git
cd samsung-dashboard
open index.html          # macOS
start index.html         # Windows
xdg-open index.html      # Linux
```

> ⚠️ 로컬 파일에서는 CORS로 인해 API 호출이 차단될 수 있습니다.

### 방법 2 — 로컬 서버 실행 (권장)

```bash
# Python 3
python -m http.server 8080
# → http://localhost:8080 접속

# Node.js (npx)
npx serve .
# → http://localhost:3000 접속
```

### 방법 3 — GitHub Pages 배포

1. 이 저장소를 본인 계정으로 Fork 또는 Push
2. **Settings → Pages → Source:** `main` 브랜치, `/ (root)` 폴더 선택
3. 저장 → `https://your-username.github.io/samsung-dashboard` 접속

### 방법 4 — Vercel 원클릭 배포

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/your-username/samsung-dashboard)

`vercel.json`이 포함되어 있어 Vercel에 그대로 배포 가능합니다.

---

## 📐 기술 스택

| 항목 | 내용 |
|------|------|
| **언어** | 순수 HTML / CSS / JavaScript (프레임워크 없음) |
| **차트** | [Chart.js 4.4.1](https://www.chartjs.org/) |
| **폰트** | Noto Sans KR, JetBrains Mono (Google Fonts) |
| **데이터** | 네이버 파이낸스 (KRW), Yahoo Finance (USD 종목) |
| **CORS 프록시** | allorigins.win → corsproxy.io → codetabs.com (순서대로 폴백) |
| **배포** | GitHub Pages / Vercel (정적 파일) |

---

## 📁 프로젝트 구조

```
samsung-dashboard/
├── index.html      # 메인 대시보드 (단일 파일 앱)
├── vercel.json     # Vercel 배포 설정
├── LICENSE         # MIT 라이선스
└── README.md       # 이 문서
```

---

## 📊 지표 설명

| 지표 | 계산 방법 | 신호 기준 |
|------|-----------|-----------|
| **MA-20** | 20일 단순이동평균 | 가격이 MA 위 → 상승 추세 |
| **RSI(14)** | 14일 상대강도지수 | 30↑ 매수, 70↓ 매도 |
| **MACD** | EMA(12) − EMA(26) | 시그널선 상향돌파 → 매수 |
| **시그널** | MACD의 EMA(9) | MACD 하향돌파 → 매도 |

**AI 추천 점수 계산:**
```
점수 = RSI 균형점수 (RSI가 50에 가까울수록 높음)
     + MACD 강세 보너스 (+15 / -15)
범위: 5 ~ 95
```

---

## ⚠️ 면책 조항

> 본 대시보드는 **정보 제공 목적**으로만 제작되었으며, 투자 조언이 아닙니다.  
> 모든 투자 결정은 본인의 판단과 책임 하에 이루어져야 합니다.  
> 데이터 정확성을 보장하지 않으며, 실제 투자 시 공식 데이터 소스를 반드시 확인하세요.

---

## 📜 라이선스

[MIT License](LICENSE) — 자유롭게 사용, 수정, 배포 가능합니다.

---

## 🤝 기여

버그 리포트, 기능 제안, PR 모두 환영합니다!

1. 저장소 Fork
2. 새 브랜치 생성 (`git checkout -b feature/새기능`)
3. 변경 후 커밋 (`git commit -m "feat: 새기능 추가"`)
4. Push (`git push origin feature/새기능`)
5. Pull Request 생성
