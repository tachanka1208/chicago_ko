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

## ⚙️ 설치 및 사용법 (Instructions)

### 1️⃣ 설치

1. GitHub에서 패키지를 클론하거나 ZIP으로 다운로드  
       git clone https://github.com/tachanka1208/Chicago_ko.git

2. `.bbx`, `.cbx`, `.lbx` 파일을 LaTeX 프로젝트의 루트 폴더에 복사  
       yourproject/
       │
       ├── main.tex
       ├── chicago_ko.bbx
       ├── chicago_ko.cbx
       └── chicago_ko.lbx

3. Biber 엔진을 사용하도록 설정  
   (Overleaf에서는 Settings → Compiler → `biber` 선택)

---

### 2️⃣ 문서 설정

    \usepackage[backend=biber,style=chicago_ko]{biblatex}
    \addbibresource{sample.bib}

본문 인용 예시:

    이 논의는 선행연구와 일치한다.\autocite{hong2004}

---

### 3️⃣ 컴파일 순서

1. pdflatex main.tex  
2. biber main  
3. pdflatex main.tex  
4. pdflatex main.tex  

이 과정을 거치면 참고문헌이 올바르게 연결된 PDF가 생성됩니다.

---

### 4️⃣ 출력 예시

1. 홍욱희, 『3조원의 환경논쟁, 새만금』, 지성사, 2004, 88쪽.  
2. 이전 자료와 같음, 92쪽.

---

## 💻 오프라인 환경 설정 (Offline Environment)

Chicago_ko는 **Vim, Neovim, 또는 CLI 환경**에서도 완전히 동일하게 작동합니다.  
인터넷 연결이 필요하지 않으며, 모든 인용 처리는 Biber가 로컬에서 수행합니다.

---

### 1️⃣ 환경 준비

#### macOS / Linux
    sudo apt install texlive-full biber
    # 또는
    brew install --cask mactex

#### Windows
0. 
1. https://tug.org/texlive/ 에서 TeX Live 설치  
2. 설치 시 “biber” 패키지를 포함시킬 것  
3. 환경 변수 PATH에 `C:\texlive\2025\bin\win32` 추가

---

### 2️⃣ Vim 또는 CLI에서 수동 컴파일

Vim 내부 또는 터미널에서:

    pdflatex main.tex
    biber main
    pdflatex main.tex
    pdflatex main.tex

Vim에서는 다음 명령으로 한 줄 실행 가능:

    :!pdflatex % && biber %:r && pdflatex % && pdflatex %

(%는 현재 파일 이름, %:r은 확장자 없는 이름)

---

### 3️⃣ Makefile로 자동화

반복 명령을 피하려면 프로젝트 루트에 `Makefile` 추가:

    FILE=main

    all:
        pdflatex $(FILE).tex
        biber $(FILE)
        pdflatex $(FILE).tex
        pdflatex $(FILE).tex

    clean:
        rm -f *.aux *.bbl *.bcf *.blg *.log *.out *.run.xml

실행:

    make

---

### 4️⃣ latexmk를 통한 자동 빌드 (선택)

`latexmk`는 BibLaTeX–Biber 과정을 자동으로 인식하여 전체를 처리합니다.

    latexmk -pdf main.tex

Vim 내부에서는:

    :!latexmk -pdf %

---

### 5️⃣ Vim 전용 설정 (vimtex 플러그인)

    Plug 'lervag/vimtex'

`.vimrc` 설정:

    let g:vimtex_compiler_method = 'latexmk'
    let g:vimtex_view_method = 'zathura'

Vim에서 `\ll` 명령으로 자동 컴파일 및 PDF 미리보기 가능.

---

### 6️⃣ 오프라인 참고문헌 처리

`.bib` 파일만 로컬에 있으면 완전히 오프라인 상태에서도 인용이 작동합니다.

예시:

    @book{hong2004,
      author    = {홍욱희},
      title     = {3조원의 환경논쟁, 새만금},
      publisher = {지성사},
      year      = {2004}
    }

`.tex` 문서에서는 다음처럼 호출:

    \usepackage[backend=biber,style=chicago_ko]{biblatex}
    \addbibresource{references.bib}

이후 위의 컴파일 절차를 따르면, 외부 네트워크 없이도 BibLaTeX–Biber가 완전 작동합니다.

---

## 📁 디렉토리 구조

chicago_ko/
│
├── chicago_ko.bbx  
├── chicago_ko.cbx  
├── chicago_ko.lbx  
├── examples/  
│   ├── sample.bib  
│   └── chicago_ko-test.tex  
└── README.md  

---

## 🧠 향후 개선

- “앞의 책(op.cit.)” 지원  
- 학위논문, AI 인용 항목 추가  
- GitHub Actions 기반 LaTeX 빌드 자동화  
- KCI 스타일 비교 연구  

---

Project Goal:  
한국어 학계 및 국제 협업 환경에서 사용 가능한 표준화된 한국형 시카고 스타일 구축
