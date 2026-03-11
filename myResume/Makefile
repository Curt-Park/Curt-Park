install:
	wget https://github.com/jgm/pandoc/releases/download/3.9/pandoc-3.9-1-amd64.deb
	sudo dpkg -i pandoc-3.9-1-amd64.deb
	rm pandoc-3.9-1-amd64.deb
	sudo apt updat
	sudo apt install -y texlive-latex-base texlive-latex-extra texlive-fonts-recommended weasyprint


html:
	for f in *.md; do \
		FILE_NAME=`basename $$f | sed 's/.md//g'`; \
		echo $$FILE_NAME.html; \
		pandoc --standalone --template=template.html --include-in-header style.css \
			--lua-filter=pdc-links-target-blank.lua \
			--from markdown --to html \
			--output $$FILE_NAME.html $$f \
			--metadata pagetitle=$$FILE_NAME;\
	done


pdf: html
	weasyprint resume.html resume.pdf
