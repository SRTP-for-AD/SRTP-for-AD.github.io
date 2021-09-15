# FOR TYRO
Please read this part carefully if you are a **tyro** who knows nothing about **LaTeX** and **git**, or you can skip.

> NOTE: the guidance below is for **PC** (Windows). If you are currently using a Mac or Linux, you can **refer** to the guidance below.

## build a LaTeX environment

LaTeX is a high-quality typesetting system and it is the de facto standard (general standard) for the communication and publication of **scientific documents**. And because the file type `.tex` is a kind of flat file, which saves only content but no format, it can be easily changed the format as you want and can be controlled by git, a version control system.

To build a LaTeX environment on your **PC**, the recommended combination is **TeXLive** and **VS Code**. TeXLive is a full featured TeX environment and VS Code is a GUI-friendly editor.

Paragraph below is the steps for installing **TeXLive** and **VS Code**. You can also try to install other environments and use the default editor in the TeX package.

### install TeXLive

* visit [Tsinghua Open Source Mirror for CTAN](https://mirrors.tuna.tsinghua.edu.cn/CTAN/systems/texlive/Images/), and download the latest version of TeXLive
  ![texlive in tuna](https://cdn.jsdelivr.net/gh/xiaodl813/FigureBed//20210509144544.png)
* double-click the `texlive2021-20210325.iso` and open it in your Explorer, and double-click the `install-tl-advanced.bat` to install
  ![iso](https://cdn.jsdelivr.net/gh/xiaodl813/FigureBed//20210509145136.png)
  > NOTE: The version of the screenshot above is TeXLive2020, but the step has no difference between 2020 and 2021 version.
* after choosing the installation root, click the "安装" to install, and you may wait about 30 minutes until it complete
  ![installer](https://cdn.jsdelivr.net/gh/xiaodl813/FigureBed//20210509145556.png)
  > NOTE: A pure-English installation root (as shown above) is recommended. You'd better NOT install TeXLive under a path with Chinese characters or spaces.
* after installation, remember to unmount the `.iso` file
* open `Windows Powershell` and run the commend `xelatex -v` to check if TeXLive is successfully installed
  ![pwsh](https://cdn.jsdelivr.net/gh/xiaodl813/FigureBed//20210914045419.png)
  The message shown above means you have installed the TeXLive successfully.

### install and configure VS Code

* visit [the download page of VS Code](https://code.visualstudio.com/Download) first, and download the latest version of VS Code
* install VS Code
* localize the VS Code (install `Chinese (Simplified) Language Pack`)
  ![localization](https://cdn.jsdelivr.net/gh/xiaodl813/FigureBed//20210914050316.png)
* install `LaTeX Workshop` (the LaTeX support plugin)
  ![LaTeX Workshop](https://cdn.jsdelivr.net/gh/xiaodl813/FigureBed//20210914050602.png)
  > NOTE: I've installed the plugin, so it's "uninstall" here.
* Press `Ctrl+Shift+P` or click "查看(V)":right:"命令面板" to open Command Palette, and input `json` to find `Preference: Open Settings`
  ![Command Palette](https://cdn.jsdelivr.net/gh/xiaodl813/FigureBed//20210914052940.png)
* add the following code in the braces, then save and exit the file
  ```json
  // LaTeX
  //"latex-workshop.latex.autoBuild.run": "never",
  "latex-workshop.message.error.show": false,
  "latex-workshop.message.warning.show": false,
  "latex-workshop.latex.tools": [
    {
      "name": "latexmk",
      "command": "latexmk",
      "args": [
        "-synctex=1",
        "-interaction=nonstopmode",
        "-file-line-error",
        "-pdf",
        "%DOCFILE%"
      ]
    },
    {
      "name": "xelatex",
      "command": "xelatex",
      "args": [
        "-synctex=1",
        "-interaction=nonstopmode",
        "-file-line-error",
        "%DOCFILE%"
      ]
    },
    {
      "name": "pdflatex",
      "command": "pdflatex",
      "args": [
        "-synctex=1",
        "-interaction=nonstopmode",
        "-file-line-error",
        "%DOCFILE%"
      ]
    },
    {
      "name": "lualatex",
      "command": "lualatex",
      "args": [
        "-synctex=1",
        "-interaction=nonstopmode",
        "-file-line-error",
        "%DOCFILE%"
      ]
    },
    {
      "name": "bibtex",
      "command": "bibtex",
      "args": [
        "%DOCFILE%"
      ]
    },
    {
      "name": "biber",
      "command": "biber",
      "args": [
        "%DOCFILE%"
      ]
    }
  ],
  "latex-workshop.latex.recipes": [
    {
      "name": "xelatex",
      "tools": [
        "xelatex"
      ]
    },
    {
      "name": "pdflatex",
      "tools": [
        "pdflatex"
      ]
    },
    {
      "name": "lualatex",
      "tools": [
        "lualatex"
      ]
    },
    {
      "name": "bibtex",
      "tools": [
        "bibtex"
      ]
    },
    {
      "name": "latexmk",
      "tools": [
        "latexmk"
      ]
    },
    {
      "name": "xelatex*2",
      "tools": [
        "xelatex",
        "xelatex"
      ]
    },
    {
      "name": "xelatex -> bibtex -> xelatex*2",
      "tools": [
        "xelatex",
        "bibtex",
        "xelatex",
        "xelatex"
      ]
    },
    {
      "name": "xelatex -> biber -> xelatex*2",
      "tools": [
        "xelatex",
        "biber",
        "xelatex",
        "xelatex"
      ]
    },
    {
      "name": "pdflatex -> bibtex -> pdflatex*2",
      "tools": [
        "pdflatex",
        "bibtex",
        "pdflatex",
        "pdflatex"
      ]
    }
  ],
  "latex-workshop.view.pdf.viewer": "tab",
  "latex-workshop.latex.clean.fileTypes": [
    "*.aux",
    "*.bbl",
    "*.blg",
    "*.idx",
    "*.ind",
    "*.lof",
    "*.lot",
    "*.out",
    "*.toc",
    "*.acn",
    "*.acr",
    "*.alg",
    "*.glg",
    "*.glo",
    "*.gls",
    "*.ist",
    "*.fls",
    "*.log",
    "*.fdb_latexmk"
  ],
  "latex-preview.command": "xelatex",
  ```

## install git on your PC

Git is a free and open source distributed version control system. It can help you on control the version of your code, including `.tex` files for article and `.r` files for R script. 

You can install git in steps below. :point_down:

* visit [Git](https://git-scm.com/), and download the latest version
* install Git :point_right: [This is the tutorial](https://www.cnblogs.com/xueweisuoyong/p/11914045.html)
* check if Git was installed successfully by using `git --version` in `Windows Powershell`
  ![Git Version](https://cdn.jsdelivr.net/gh/xiaodl813/FigureBed//20210914054742.png)

Before you start trying, I **STRONGLY RECOMMEND** you to read [this tutorial](https://zhuanlan.zhihu.com/p/85556528). It's a tyro-friendly and clear tutorial for **git** and **VS Code**. You will know how to control the version of `.tex` file after reading it.

## Have a try!