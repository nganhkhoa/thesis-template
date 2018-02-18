# SYSSEC thesis-template
Clone the git and compile with `latexmk`. Heavily inspired by the mas-template. 
If you run into any issues with this template, open a new issue on github. Thanks.

## TODO List
* Logo

## Compile

We recommend you to use the provided Dockerfile to ease your use of this template.

0. [install Docker](https://docs.docker.com/install/)

1. Build the setup container with `$ docker build -t syssec/tex-setup -f Dockerfile.setup .` This needs only to be done once.

2. Now build the main container with `$ docker build -t syssec/tex -f Dockerfile .` This needs to be repeated after every change in your file

3. Invoke `latexmk` in the docker container with 
`$ docker run syssec/tex latexmk [flags] file-to-compile`

4. Copy your compiled pdf from the container to the host system with 
`docker cp container-id:/syssec-build/file-to-compile.pdf`. You get the container ID from the last built container with `$ docker ps -alq`

We also provide you with the `compile.sh` script, which automatically compiles and copies the template for you. So you dont have to bother with step 2 to 4. Step 1 remains **mandatory**.

To use the script just use `$ sh compile.sh syssec-thesis`.


## Packages you need to install to use the template

If you are on a Debian based system, install these packages from the repositories

* texlive-base
* texlive-latex-recommended
* texlive-latex-extra
* texlive-science
* texlive-bibtex-extra
* latexmk
* biber

You will also need the `ccicons` and `tracklang` package. Both can be found in the tlmgr repositories.

The `needed_package.sh` script will print you the used packages.

```bash
$tlmgr install missingpackage.sty
```

If tlmgr can not find the right packages, you can download them manually. 

## How to use this template
You can use this template to write your thesis or to write a report. Just change the option in the `syssec-thesis.tex` preamble.
The `syssec-thesis.tex` should only be used to glue together your document. Your writings should be put in seperate tex files. Use the `\input{path/to/.tex}` command to assemble your document. This keeps your project structured and tidy.

Every `.tex` file contains small manuals on how to use it.

You are free to modify this template.

If you want to compile your files, just invoke `latexmk` which will do the work for you. To clean up, just use `latexmk -c`. This will leave only the PDF file in the folder. 
