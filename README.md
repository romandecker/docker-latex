Docker-Container for simple LaTeX-Builds
========================================

This container aims to provide a simple way to build LaTeX documents out of the
box. You can basically perform any compilation task using this image, although a
simple script is provided to perform a `latexmk`-powered continuous build.

Usage
-----

The container expects your LaTeX-documents mounted at `/latex`, so if you want
to start a continuous build from your cwd, simply run:

    docker run --rm -v `pwd`:/latex theromanempire/latex autobuild yourfile.tex

Which will compile your tex-file to a PDF-Document, including BibTex & SyncTex
support, and watch your files for changes and recompile everything whenever a
change happens. All this is done through the magic of `latexmk`.

Adding additional cls-files
-----------------------------

`TEXMFHOME` is located at `/root/texmf` within the container. Simply put your
files there (in the correct hierarchy). And re-run `texhash` and `mktexlsr
/root/texmf` so that LaTeX will find them.
