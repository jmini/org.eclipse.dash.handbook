all : \
	../output/eclipse.html ../output/eclipse.pdf \
	../output/polarsys.html ../output/polarsys.pdf \
	../output/locationtech.html ../output/locationtech.pdf \
	directories \
	images
.PHONY : all

directories : ../output ../output/images

../output : 
	mkdir -p ../output
	
../output/images : ../output
	mkdir -p ../output/images
	cp ../images/* ../output/images/

# IMAGES

images : \
	../output/images/project-creation.png \
	../output/images/post-creation.png \
	../output/images/release-cycle.png \
	../output/images/release-review.png \
	../output/images/paperwork.png \
	../output/images/cq-workflow.png \
	../output/images/project-lifecycle.png \
	../output/images/ip-log-generator.png
.PHONY : all

../output/images/project-creation.png : ../output/images images/project-creation.dot
	dot -Tpng images/project-creation.dot > ../output/images/project-creation.png
	
../output/images/post-creation.png : ../output/images images/post-creation.dot
	dot -Tpng images/post-creation.dot > ../output/images/post-creation.png

../output/images/release-cycle.png : ../output/images images/release-cycle.dot
	dot -Tpng images/release-cycle.dot > ../output/images/release-cycle.png

../output/images/release-review.png : ../output/images images/release-review.dot
	dot -Tpng images/release-review.dot > ../output/images/release-review.png
	
../output/images/paperwork.png : ../output/images images/paperwork.dot
	dot -Tpng images/paperwork.dot > ../output/images/paperwork.png

../output/images/cq-workflow.png : ../output/images images/cq-workflow.dot
	dot -Tpng images/cq-workflow.dot > ../output/images/cq-workflow.png
	
../output/images/project-lifecycle.png : ../output/images images/project-lifecycle.dot
	dot -Tpng images/project-lifecycle.dot > ../output/images/project-lifecycle.png
	
../output/images/ip-log-generator.png : ../output/images images/ip-log-generator.dot
	dot -Tpng images/ip-log-generator.dot > ../output/images/ip-log-generator.png

# ECLIPSE

../output/eclipse.book.xml : ../output eclipse.adoc config.adoc chapters/* images
	asciidoctor -b docbook -d book -o ../output/eclipse.book.xml eclipse.adoc
	
../output/eclipse.html : ../output eclipse.adoc config.adoc chapters/* images
	asciidoctor -a stylesheet=handbook.css -b html5 -d book -o ../output/eclipse.html eclipse.adoc

#../output/eclipse.html : ../output ../output/eclipse.book.xml
#	xsltproc -o ../output/eclipse.html /usr/share/sgml/docbook/xsl-ns-stylesheets/xhtml-1_1/docbook.xsl ../output/eclipse.book.xml

../output/eclipse.pdf : ../output ../output/eclipse.book.xml
	xsltproc -xinclude -o ../output/eclipse.fo \
		--param toc.section.depth 1 \
		--param ulink.footnotes 1 \
		--param admon.graphics 1 \
		--xinclude \
		/usr/share/sgml/docbook/xsl-ns-stylesheets/fo/docbook.xsl ../output/eclipse.book.xml
	fop -v ../output/eclipse.fo -pdf ../output/eclipse.pdf
	rm ../output/eclipse.fo


# POLARSYS

../output/polarsys.book.xml : ../output polarsys.adoc config.adoc chapters/* images
	asciidoctor -b docbook -d book -o ../output/polarsys.book.xml polarsys.adoc
	
../output/polarsys.html : ../output polarsys.adoc config.adoc chapters/* images
	asciidoctor -a stylesheet=github.css -b html5 -d book -o ../output/polarsys.html polarsys.adoc

../output/polarsys.pdf : ../output ../output/polarsys.book.xml
	xsltproc -xinclude -o ../output/polarsys.fo \
		--param toc.section.depth 1 \
		--param ulink.footnotes 1 \
		--param admon.graphics 1 \
		/usr/share/sgml/docbook/xsl-ns-stylesheets/fo/docbook.xsl ../output/polarsys.book.xml
	fop -v ../output/polarsys.fo -pdf ../output/polarsys.pdf
	rm ../output/polarsys.fo
	
# LOCATIONTECH

../output/locationtech.book.xml : ../output locationtech.adoc config.adoc chapters/* images
	asciidoctor -b docbook -d book -o ../output/locationtech.book.xml locationtech.adoc
	
../output/locationtech.html : ../output locationtech.adoc config.adoc chapters/* images
	asciidoctor -a stylesheet=github.css -b html5 -d book -o ../output/locationtech.html locationtech.adoc

../output/locationtech.pdf : ../output ../output/locationtech.book.xml
	xsltproc -xinclude -o ../output/locationtech.fo \
		--param toc.section.depth 1 \
		--param ulink.footnotes 1 \
		--param admon.graphics 1 \
		/usr/share/sgml/docbook/xsl-ns-stylesheets/fo/docbook.xsl ../output/locationtech.book.xml
	fop -v ../output/locationtech.fo -pdf ../output/locationtech.pdf
	rm ../output/locationtech.fo