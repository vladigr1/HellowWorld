# MetaProgramming

Set of things that are more about process of creating code.

## make

Most common build system out there.\
when you run `make`, it have consults a file called `makefile` in the current directory.

```makefile
paper.pdf: paper.tex plot-data.png
	pdflatex paper.tex

plot-%.png: %.dat plot.py
	./plot.py -i $*.dat -o $@
```