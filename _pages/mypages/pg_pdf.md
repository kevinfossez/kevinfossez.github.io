---
layout: archive
permalink: /misc/commands_pdf/
title: How-to pdf
description: Last update on June 12, 2020
---


# Convert from/to pdf

## Convert a pdf into a djvu file (about 10% of the pdf size)

```bash
pdf2djvu -o output_file input_file
```

## Convert a pdf into a png file (single page)

```bash
pdftoppm input_file.pdf output_file -png -f 1 -singlefile -rx 300 -ry 300
```
(here page number is "1", dpi quality is "300")


## Convert a djvu file into a pdf file

```bash
djvups doc.djvu doc.ps
ps2pdf doc.ps
```

## Convert all eps files in a directory into pdf files

```bash
find . -name "*.eps" -exec epstopdf {} \;
```

## Convert a jpg file into a pdf file

```bash
convert -compress jpeg -quality 85 p*.jpg out.pdf
pdf2ps out.pdf out.ps
ps2pdf f.ps
```

## Convert an epub file into a pdf file

```bash
ebook-convert foo.epub foo.pdf
```

With more options for a better output:

```bash
ebook-convert foo.epub foo.pdf --margin-bottom "75" --margin-top "75" --margin-left "75" --margin-right "75" --pdf-serif-family "Calibri" --pdf-sans-family "Calibri" --base-font-size "14" --pdf-mono-font-size "12" --paper-size "a4" --change-justification "justify"
```

In Mac OS:  

```bash
brew cask install calibre
export PATH=/Applications/calibre.app/Contents/MacOS/:$PATH
ebook-convert book.epub book.pdf --margin-bottom "75" --margin-top "75" --margin-left "50" --margin-right "50" --pdf-serif-family "Calibri" --pdf-sans-family "Calibri" --base-font-size "12" --pdf-mono-font-size "12" --paper-size "a4" --change-justification "justify"
```


## Convert a svg file into a pdf file

### Method that works well (not necessary in MacOS)

```bash
rsvg-convert -f pdf -o t.pdf t.svg
```

### Method that works less well

```bash
cairosvg image.svg -o image.pdf
```

### Idem (in python3)

```python
import cairosvg
cairosvg.svg2pdf(url='image.svg', write_to='image.pdf')
```


# Manipulate a pdf file


## Concatenate several pdf files

```bash
pdftk 1.pdf 2.pdf 3.pdf cat output 123.pdf
```

## Rotate by 180 degrees pdf file

### Single-page file ("1")

```bash
pdftk in.pdf cat 1south output out.pdf 
```

### All pages ("1-end")

```bash
pdftk in.pdf cat 1-endsouth output out.pdf
```

## Extract pages from different pdf files (without removing them from the original files...)

```bash
pdftk A=f1.pdf B=f2.pdf cat A12-14 B2-34 A15 output outf.pdf
```

## Extract one page from a djvu file

```bash
djvused landau4.djvu -e 'select 22; save-page out22.djvu'
```

## Concatenate pages from different djvu files

```bash
djvm -c doc.djvu out18.djvu out19.djvu out20.djvu out21.djvu out22.djvu out23.djvu
```

# Extract pieces of a pdf file

## Extract an element from a pdf file (figure, anything)

Cuts by "290", "140", etc. points on the bottom, left, etc.

```bash
pdfcrop --margins '-290 -140 -290 -130' old.pdf new.pdf
```
Then remove "hidden stuffs" around the extracted piece that pdfcrop did not remove:

```bash
pdf2ps out.pdf out.ps
ps2pdf f.ps
```

Or better:

```bash
pdfcrop --margins 0 old.pdf new.pdf
```


# Reduce the size of a pdf

```bash
convert -density 300x300 -quality 2 -compress jpeg input.pdf out.pdf
```

