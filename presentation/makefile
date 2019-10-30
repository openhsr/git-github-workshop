# Makefile to build the LaTeX Git Presentation
# 
# Naoki Pross - 2019/10/30

SOURCE := presentation.tex
OUTPUT := $(patsubst %.tex, %.pdf, $(SOURCE))
OUTDIR := build

TEX     := xelatex 
TEXARGS := --interaction=nonstopmode --output-directory $(OUTDIR) --8bit

all: $(OUTPUT)

$(OUTDIR):
	mkdir $@

%.pdf: %.tex $(OUTDIR)
	@echo "Compiling $<"
	$(TEX) $(TEXARGS) $<
	@echo "Copying"
	cp -u $(OUTDIR)/$@ ./
