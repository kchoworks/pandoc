# `pandoc` 사용법

## 한글 포함시

- `template.tex` 파일 작성: `lualatex`에서 한글 사용 및 글꼴 설정
  ```
  \usepackage{kotex}
  \setmainfont{SourceHanSerifKR}
  \setsansfont{SourceHanSansKR}
  \setmonofont{D2coding}
  ```
  [참고] 이밖에 유용한 명령어들: 
  `\setmainhangulfont`, `\setmainhanjafont`, `\setmainfallbackfont`,
  `\setsanshangulfont`, `\setsanshanjafont`, `\setsansfallbackfont`,
  `\setmonohangulfont`, `\setmonohanjafont`, `\setmonofallbackfont`,
  `\newhangulfontfamily`, `\newhanjafontfamily`, `\newfallbackfontfamily`, 
  `\addhangulfontfeature`, `\addhanjafontfeature`, `\addfallbackfontfeature`,
  `\hangulfontspec`, `\hanjafontspec`, `\fallbackfontspec`


- 마크다운 파일(여기서는 `test.md`) 작성:
  ```
  # 1수준
  한글을 씁니다.

  ## 2수준
  한글을 씁니다.
  ```


- 코맨드 창에서:

    - `pdf` 출력시
      ```
      > pandoc test.md -o test.pdf --include-in-header=template.tex --latex-engine=lualatex

      또는

      > pandoc test.md -o test.pdf --include-in-header=template.tex --variable=mainfont:"SourceHanSansKR" --latex-engine=lualatex
      ```

    - `tex` 출력시
      ```
      > pandoc test.md -o test.tex --include-in-header=template.tex --latex-engine=lualatex

      또는

      > pandoc test.md -o test.tex --include-in-header=template.tex --variable=mainfont:"SourceHanSansKR" --latex-engine=lualatex
      ```

      후에 `test.tex`을 compile



[참고] `pandoc`(version 1.19.2.1) 명령줄 옵션
```
pandoc [OPTIONS] [FILES]
  -f FORMAT, -r FORMAT  --from=FORMAT, --read=FORMAT
  -t FORMAT, -w FORMAT  --to=FORMAT, --write=FORMAT
  -o FILENAME           --output=FILENAME
                        --data-dir=DIRECTORY
  -R                    --parse-raw
  -S                    --smart
                        --old-dashes
                        --base-header-level=NUMBER
                        --indented-code-classes=STRING
  -F PROGRAM            --filter=PROGRAM
                        --normalize
  -p                    --preserve-tabs
                        --tab-stop=NUMBER
                        --track-changes=accept|reject|all
                        --file-scope
                        --extract-media=PATH
  -s                    --standalone
                        --template=FILENAME
  -M KEY[:VALUE]        --metadata=KEY[:VALUE]
  -V KEY[:VALUE]        --variable=KEY[:VALUE]
  -D FORMAT             --print-default-template=FORMAT
                        --print-default-data-file=FILE
                        --dpi=NUMBER
                        --no-wrap
                        --wrap=auto|none|preserve
                        --columns=NUMBER
                        --toc, --table-of-contents
                        --toc-depth=NUMBER
                        --no-highlight
                        --highlight-style=STYLE
  -H FILENAME           --include-in-header=FILENAME
  -B FILENAME           --include-before-body=FILENAME
  -A FILENAME           --include-after-body=FILENAME
                        --self-contained
                        --html-q-tags
                        --ascii
                        --reference-links
                        --reference-location=block|section|document
                        --atx-headers
                        --chapters
                        --top-level-division=section|chapter|part
  -N                    --number-sections
                        --number-offset=NUMBERS
                        --no-tex-ligatures
                        --listings
  -i                    --incremental
                        --slide-level=NUMBER
                        --section-divs
                        --default-image-extension=extension
                        --email-obfuscation=none|javascript|references
                        --id-prefix=STRING
  -T STRING             --title-prefix=STRING
  -c URL                --css=URL
                        --reference-odt=FILENAME
                        --reference-docx=FILENAME
                        --epub-stylesheet=FILENAME
                        --epub-cover-image=FILENAME
                        --epub-metadata=FILENAME
                        --epub-embed-font=FILE
                        --epub-chapter-level=NUMBER
                        --latex-engine=PROGRAM
                        --latex-engine-opt=STRING
                        --bibliography=FILE
                        --csl=FILE
                        --citation-abbreviations=FILE
                        --natbib
                        --biblatex
  -m[URL]               --latexmathml[=URL], --asciimathml[=URL]
                        --mathml[=URL]
                        --mimetex[=URL]
                        --webtex[=URL]
                        --jsmath[=URL]
                        --mathjax[=URL]
                        --katex[=URL]
                        --katex-stylesheet=URL
                        --gladtex
                        --trace
                        --dump-args
                        --ignore-args
                        --verbose
                        --bash-completion
                        --list-input-formats
                        --list-output-formats
                        --list-extensions
                        --list-highlight-languages
                        --list-highlight-styles
  -v                    --version
  -h                    --help
```
