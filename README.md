# Chicago_ko — Korean Chicago Citation Style

Version: v0.1  
Author: [Your Name]  
License: MIT  

---

## 📘 개요

Chicago_ko는 **BibLaTeX 기반의 한국어 시카고 인용 스타일**입니다.  
기존 `biblatex-chicago`를 기반으로, 한국 학술 환경에 맞게 다음 요소를 수정하였습니다:

- 📚 인용 규칙: 각주(footnote) 방식 기본 설정 (`autocite=footnote`)
- 💬 ibid 한글화: “이전 자료와 같음”
- 🧍 이름 순서 유지: 성 + 이름 그대로 표시
- 🌐 웹자료 인용: “검색일자”, “출처” 등 한글화
- 🧾 언어 파일(.lbx) 통합: ‘쪽’, ‘판’, ‘역’ 등 용어 현지화

---

## 📁 파일 구조
```
chicago_ko/
│
├── chicago_ko.bbx   # 참고문헌(Bibliography) 형식 정의  
├── chicago_ko.cbx   # 인용(Citation) 규칙 정의  
├── chicago_ko.lbx   # 한국어 문자열 정의  
├── examples/  
│   ├── sample.bib  
│   └── chicago_ko-test.tex  
└── README.md  
```
---

## ⚙️ 사용법

\usepackage[backend=biber,style=chicago_ko]{biblatex}  
\addbibresource{sample.bib}  

이 논의는 선행연구와 일치한다.\autocite{hong2004}

---

## 📄 출력 예시

1. 홍욱희, 『3조원의 환경논쟁, 새만금』, 지성사, 2004, 88쪽.  
2. 이전 자료와 같음, 92쪽.

---

## 🧠 향후 개선

- “앞의 책(op.cit.)” 지원  
- 학위논문, AI 인용 항목 추가  
- GitHub Actions 기반 LaTeX 빌드 자동화  
- KCI 스타일 비교 연구  

---

Project Goal:  
한국어 학계 및 국제 협업 환경에서 사용 가능한 표준화된 한국형 시카고 스타일 구축
