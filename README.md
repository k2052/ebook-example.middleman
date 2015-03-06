# Middleman Ebook Example

An example of how create an ebook using Markdown + XHTML + CSS as the starting formats.
From there; pdf, epub and mobi are built. If you have ever looked at an ebook generation toolchain and thought "how would I do this manually?" this is your repo. You'll have to get your hands dirty but in return you get maximal flexibility and maximum customization.

XHTML is written using Slim and assembled using Middleman. PDF is generated using PDFkit. Epub is generated using Eeepub. Mobbi is generated from the epub using kindlegen.

## Installation

First install all the gems:

```sh
$ bundle install
```

Then install wkhtmltopdf:

On OS X:

```sh
$ brew install wkhtmltopdf
```

On Ubuntu:

```sh
$ sudo apt-get install wkhtmltopdf
```

See https://github.com/pdfkit/pdfkit/wiki/Installing-WKHTMLTOPDF for other platforms

## Usage

Write your book using Markdown and place the files in manuscript/. Then include chapters in source/index.html using partials. For example:

    == partial "../manuscript/Chapt1"

Use CSS for theming and remember to use something like Epubcheck to make sure you haven't introduced any errors.

## Building

To build all the formats:

    $ bundle exec rake build:pdf

To see other build options:

    $  bundle exec rake -T

Good luck with your writing adventures!
