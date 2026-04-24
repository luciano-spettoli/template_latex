# Template LaTeX project

This is a template for a LaTeX project.


## Download

Downloads are available in these formats:
- **PDF**: PDF document
- **EPUB MathML**: reflowable ebook, with math content in MathML format;
- **EPUB SVG**: reflowable ebook, with math content rendered as SVG;

|  Downloads                                                                          |
|:-----------------------------------------------------------------------------------:|
|         [PDF](https://luciano-spettoli.github.io/template_latex/sample.pdf)         |
| [EPUB MathML](https://luciano-spettoli.github.io/template_latex/sample-mathml.epub) |
|    [EPUB SVG](https://luciano-spettoli.github.io/template_latex/sample-svg.epub)    |


## Building

### Requirements
The documents are typeset in LaTeX,
and can be generated from the source code with any TeX distribution.


### Generate PDF
To generate the `PDF` file, run this command from within the `src` directory:
```shell
latexmk main.tex
```
The resulting file is placed in the `output` directory (outside of `src`).

#### TeX engines
Compilation is possible with the pdfLaTeX and LuaLaTeX compilation engines;
the engine used by default is LuaLaTeX.

To compile with pdfLaTeX, set the `-pdflatex` option when running `latexmk`:
```shell
latexmk -pdflatex main.tex
```
or change `$pdf_mode = 4` to `$pdf_mode = 1` in the `latexmkrc` file.


### Generate ebook

> [!NOTE]
> It is recommended to have [`tidy`](https://github.com/htacg/tidy-html5) installed.

For generating an ebook in `EPUB3` format with mathematical notation encoded in `MathML`,
run this command from within the `src` directory:
```shell
tex4ebook -B ../build_epub3 -d ../output -f epub3 main.tex mathml
```

For `SVG` Maths, use this command:
```shell
tex4ebook -B ../build_ebook_svg -d ../output -f epub main.tex svg
```

For `PNG` Maths, use this command:
```shell
tex4ebook -B ../build_ebook_png -d ../output -f epub main.tex png
```

> [!NOTE]
> The `epub` option in the above two commands can be replaced by any format among `epub`, `epub3`, `mobi`, `azw`, `azw3`;
> but in order to generate ebooks in `mobi`, `azw` and `azw3` formats,
> [calibre](https://github.com/kovidgoyal/calibre) needs to be installed,
> because `tex4ebook` uses the command `ebook-convert`, provided by calibre.

> [!NOTE]
> The commands described above use PDFTeX as engine.
> Compilation with LuaTeX is currently not working.  
> In any case, to use LuaTeX as engine anyway, use `tex4ebook -l` in place of `tex4ebook` in the commands.


### Reproducible builds

PDF builds are reproducible.  
In order to reproduce a PDF build,
use the same TeX distribution, version, and engine as the target file,
set the environment variable `SOURCE_DATE_EPOCH` to match that of the target build
(and consider setting `FORCE_SOURCE_DATE=1` too),
and use the same `-jobname` as the target build:
```shell
SOURCE_DATE_EPOCH=0 FORCE_SOURCE_DATE=1 latexmk main.tex -jobname="jobname"
```
All the required parameters can be found [here](https://luciano-spettoli.github.io/template_latex/build_env.txt).


### PDF standards compliance

The PDF files are conformant with
the [PDF/A-4f](https://pdfa.org/resource/iso-19005-4-pdf-a-4/) standard,
and the accessibility standards
[PDF/UA-2](https://pdfa.org/iso-14289-2-pdfua-2/)
and [WTPDF-1.0 (Well-Tagged PDF)](https://pdfa.org/wtpdf);
their PDF version is [PDF 2.0](https://pdfa.org/resource/iso-32000-2/).

When compiling from source, it is possible to choose different standards:
- to build a PDF satisfying [PDF/A-3a](https://pdfa.org/resource/iso-19005-3-pdf-a-3/)
  and the accessibility standard [PDF/UA-1](https://pdfa.org/resource/iso-14289-pdfua/),
  under PDF version [PDF 1.7](https://pdfa.org/resource/iso-32000-1/),
  compile with this command:
  ```shell
  latexmk -g -usepretex='\def\PDFAA{}' main.tex
  ```
- to build a PDF satisfying [PDF/A-2u](https://pdfa.org/resource/iso-19005-2-pdf-a-2/),
  under PDF version [PDF 1.7](https://pdfa.org/resource/iso-32000-1/),
  compile with this command:
  ```shell
  latexmk -g -usepretex='\def\NOTAG{}' main.tex
  ```

#### Compliance validation
Verifying that a PDF file is conformant to certain PDF standards
can be done with [VeraPDF](https://verapdf.org/),
either online at [https://demo.verapdf.org/](https://demo.verapdf.org/),
or locally.
To test a PDF file locally, run the following command (note that it requires VeraPDF to be installed):
```shell
verapdf --flavour 0 --format text path/to/file.pdf
```


## Contributing

More details are provided in [CONTRIBUTING.md](CONTRIBUTING.md).


## License

This work is released into the public domain.
See [LICENSE](LICENSE).
