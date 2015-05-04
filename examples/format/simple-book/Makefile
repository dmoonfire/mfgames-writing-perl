#
# Variables
#

# Programs
ROOT				 = ../../..
FORMAT_MARKDOWN_PDF  = $(ROOT)/format-markdown-pdf
FORMAT_MARKDOWN_EPUB = $(ROOT)/format-markdown-epub
FORMAT_MARKDOWN_ODT  = $(ROOT)/format-markdown-odt
KINDLEGEN            = kindlegen
LIBREOFFICE    		 = libreoffice

# Paths
BUILD = build

#
# Primary Targets
#

all: $(BUILD)/book.epub $(BUILD)/book.pdf $(BUILD)/kindle.mobi $(BUILD)/smashwords.doc

clean:
	rm -rf *~ $(BUILD)

$(BUILD)/book.pdf: book.markdown
	if [ ! -d $(BUILD) ];then mkdir $(BUILD); fi
	$(FORMAT_MARKDOWN_PDF) book.markdown --output=$(BUILD)/book.pdf --include --format=trade,standard-title,toc --filter-links=.no-print

$(BUILD)/book.epub: book.markdown
	if [ ! -d $(BUILD) ];then mkdir $(BUILD); fi
	$(FORMAT_MARKDOWN_EPUB) book.markdown --output=$(BUILD)/book.epub --cover=book.jpg

$(BUILD)/kindle.epub: book.markdown
	if [ ! -x $(shell which $(KINDLEGEN)) ]; then \
		echo "Cannot run kindlegen to convert"; \
		echo "Looking for: $(KINDLEGEN)"; \
		false; \
	fi
	if [ ! -d $(BUILD) ];then mkdir $(BUILD); fi
	$(FORMAT_MARKDOWN_EPUB) book.markdown --output=$(BUILD)/kindle.epub --filter=links=.no-amazon --cover=book.jpg

$(BUILD)/kindle.mobi: $(BUILD)/kindle.epub
	if [ ! -x $(shell which $(KINDLEGEN)) ]; then \
		echo "Cannot run kindlegen to convert"; \
		echo "Looking for: $(KINDLEGEN)"; \
		false; \
	fi
	$(KINDLEGEN) $(BUILD)/kindle.epub

$(BUILD)/smashwords.odt: book.markdown
	if [ ! -x $(shell which $(LIBREOFFICE)) ]; then \
		echo "Cannot run Libreoffice to convert"; \
		echo "Looking for: $(LIBREOFFICE)"; \
		false; \
	fi
	if [ ! -d $(BUILD) ];then mkdir $(BUILD); fi
	$(FORMAT_MARKDOWN_ODT) book.markdown --output=$(BUILD)/smashwords.odt --include --filter-links=.no-smashwords

$(BUILD)/smashwords.doc: $(BUILD)/smashwords.odt
	if [ ! -x $(shell which $(LIBREOFFICE)) ]; then \
		echo "Cannot run Libreoffice to convert"; \
		echo "Looking for: $(LIBREOFFICE)"; \
		false; \
	fi
	cd $(BUILD) && $(LIBREOFFICE) --headless --convert-to doc smashwords.odt


