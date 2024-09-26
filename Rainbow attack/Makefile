BUILD=build
LATEX=latexmk -recorder -pdf -pdflatex="pdflatex --shell-escape %O %S" \
		-outdir=$(BUILD)
MAIN=rainbow

all: rainbow.pdf

preview:
	$(LATEX) -pvc -interaction=nonstopmode $(MAIN).tex

%.pdf: latexmkbuild
	$(LATEX) $(patsubst %.pdf, %.tex, $@)
	ln -fs $(BUILD)/$@

clean:
	rm -rf $(BUILD)
	rm -f $(MAIN)*.pdf

# This recipe is always made (because it is phony). Because we need to rely on
# latexmk to check for file dependencies.
latexmkbuild:
	mkdir -p $(BUILD)


.PHONY: all latexmkbuild
