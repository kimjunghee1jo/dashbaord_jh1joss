# 📈 삼성전자 주식 대시보드

실시간 삼성전자(005930.KS) 주가 분석 대시보드 — 기술적 지표, 반도체 섹터 비교, AI 매매신호 제공.

![Dashboard Preview](https://img.shields.io/badge/Status-Live-brightgreen) ![License](https://img.shields.io/badge/License-MIT-blue) ![Language](https://img.shields.io/badge/Language-한국어-red)

---

## 🚀 바로 실행 (GitHub Pages)

👉 **[라이브 데모 보기](https://your-username.github.io/samsung-dashboard)**

> `your-username`을 본인의 GitHub 아이디로 변경하세요.

---

## ✨ 주요 기능

| 기능 | 설명 |
|------|------|
| 📊 실시간 주가 | Yahoo Finance API 연동, 5분마다 자동 갱신 |
| 📈 기술적 지표 | MA-20, RSI(14), MACD 차트 |
| 🎯 매매신호 | RSI 크로스오버 + MACD 기반 자동 매수/매도 신호 |
| 🔬 섹터 비교 | 삼성전자, SK하이닉스, TSMC, 엔비디아 등 동종 비교 |
| 🤖 AI 추천 | 종합 점수 기반 투자 추천 게이지 |
| 📰 뉴스 피드 | 클릭 시 전체 기사 모달 팝업 |
| 💾 CSV 내보내기 | 가격/신호 데이터 다운로드 |
| 🏦 키움증권 | Open API+ 연동 구조 (로컬 HTS 환경 필요) |

---

## 🛠 사용 방법

### 방법 1 — 로컬에서 바로 열기

```bash
git clone https://github.com/your-username/samsung-dashboard.git
cd samsung-dashboard
# index.html을 브라우저로 열기
open index.html          # macOS
start index.html         # Windows
xdg-open index.html      # Linux
```

> ⚠️ 일부 브라우저는 로컬 파일에서 CORS를 차단할 수 있습니다. 아래 방법을 권장합니다.

### 방법 2 — 로컬 서버 실행

```bash
# Python 3
python -m http.server 8080

# 브라우저에서 접속
# http://localhost:8080
```

### 방법 3 — GitHub Pages 배포 (권장)

1. 이 저장소를 Fork 또는 본인 계정에 Push
2. GitHub → Settings → Pages → Source: `main` 브랜치, `/root` 폴더 선택
3. 저장 후 `https://your-username.github.io/samsung-dashboard` 에서 접속

---

## 🏦 키움증권 Open API 연동 (선택 사항)

실제 키움증권 실시간 데이터를 받으려면 로컬 환경에서 별도 설정이 필요합니다.

**요구 사항:**
- Windows 환경 (키움증권 HTS는 Windows 전용)
- 키움증권 계좌 및 Open API+ 신청
- Python 3.x + `pykiwoom` 라이브러리

```bash
pip install pykiwoom
```

**간단한 현재가 조회 예시:**

```python
from pykiwoom.kiwoom import Kiwoom
import pythoncom

kiwoom = Kiwoom()
kiwoom.CommConnect(block=True)

# 삼성전자 현재가 조회
price = kiwoom.GetMasterLastPrice("005930")
print(f"삼성전자 현재가: {price}원")
```

> 키움증권 API는 웹 브라우저에서 직접 호출이 불가하므로, 로컬 Python 서버를 통해 REST API로 중계하는 구조가 필요합니다. 현재 대시보드는 Yahoo Finance 프록시를 기본으로 사용합니다.

---

## 📐 기술 스택

- **프론트엔드:** 순수 HTML/CSS/JavaScript (프레임워크 없음)
- **차트:** [Chart.js 4.4.1](https://www.chartjs.org/)
- **폰트:** Noto Sans KR, JetBrains Mono (Google Fonts)
- **데이터:** Yahoo Finance v8 Chart API (allorigins CORS 프록시)
- **배포:** GitHub Pages 지원

---

## 📁 프로젝트 구조

```
samsung-dashboard/
├── index.html        # 메인 대시보드 (전체 앱이 단일 파일)
└── README.md         # 이 문서
```

---

## 📊 지표 설명

| 지표 | 설명 |
|------|------|
| **MA-20** | 20일 단순이동평균선 |
| **RSI(14)** | 14일 상대강도지수. 30 이하 과매도, 70 이상 과매수 |
| **MACD** | 단기(12일) EMA - 장기(26일) EMA |
| **시그널** | MACD의 9일 EMA |
| **매수신호** | RSI가 30을 상향 돌파하거나 MACD가 시그널선 상향 돌파 |
| **매도신호** | RSI가 70을 하향 돌파하거나 MACD가 시그널선 하향 돌파 |

---

## ⚠️ 면책 조항

> 본 대시보드는 **정보 제공 목적**으로만 제작되었으며, 투자 조언이 아닙니다.  
> 모든 투자 결정은 본인의 판단과 책임 하에 이루어져야 합니다.  
> 데이터 정확성을 보장하지 않으며, 실제 투자에 활용 시 공식 데이터 소스를 반드시 확인하세요.

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
