# How to make progit PDF with Knoppix
target lang is ja
## Knoppix
use this liveCD distro
http://www.rcis.aist.go.jp/project/knoppix/
> knoppix_v6.7.1CD_20110914-20111018.iso
http://ring.airnet.ne.jp/archives/linux/knoppix/iso/knoppix_v6.7.1CD_20110914-20111018.iso
KNOPPIX 6.7.1 CD LCAT

### uname -a
	Linux Microknoppix 3.0.4 #1 SMP PREEMPT Mon Oct 17 07:15:29 UTC 2011 i686 GNU/Linux

## Knoppix makes up to bootable USB
/usr/bin/flash-install
install to usb (SD 2GB) done

## make knoppix.img after USB boot
approx. 1048 B

## install Ruby
	$ sudo aptitude install ruby
	$ ruby -v
	ruby 1.8.7 (2010-08-16 patchlevel 302) [i486-linux]

## install Git
	$ sudo aptitude update
	$ sudo aptitude install git git-core
	$ git --version
	git version 1.7.2.5

## clone progit repo
https://github.com/progit/progit
### SSH protocol: NG
https://github.com/progit/progit.git
### Git protocol: OK
git://github.com/progit/progit.git

## ./makepdfs ja
	$./makepdfs ja
		Missing dependencies: pandoc, xelatex.
		Install these and try again.

## install xetex, pandoc 
	$ sudo aptitude install texlive-xetex texlive-common pandoc

###  xetex	
	$ xetex --version
	XeTeX 3.1415926-2.2-0.9995.2 (TeX Live 2009/Debian)
	kpathsea version 5.0.0
	Copyright 2009 SIL International and Jonathan Kew.
	There is NO warranty.  Redistribution of this software is
	covered by the terms of both the XeTeX copyright and
	the Lesser GNU General Public License.
	For more information about these matters, see the file
	named COPYING and the XeTeX source.
	Primary author of XeTeX: Jonathan Kew.
	Compiled with ICU version 3.8.1 [with modifications for XeTeX]
	Compiled with zlib version 1.2.3.4; using 1.2.3.4
	Compiled with FreeType2 version 2.4.2; using 2.4.2
	Compiled with fontconfig version 2.8.0; using 2.8.0
	Compiled with libpng version 1.2.44; using 1.2.44
	Compiled with poppler version 0.12.4

### pandoc
	$ pandoc --version
	pandoc 1.5.1.1
	Compiled with syntax highlighting support for:
	Ada, Alert, Asp, Awk, Bash, Bibtex, C, Cmake, Coldfusion, Commonlisp, Cpp, Css,
	D, Djangotemplate, Doxygen, Dtd, Eiffel, Erlang, Fortran, Haskell, Html, Java,
	Javadoc, Javascript, Json, Latex, Lex, LiterateHaskell, Lua, Makefile, Matlab,
	Mediawiki, Modula3, Nasm, Objectivec, Ocaml, Octave, Pascal, Perl, Php,
	Postscript, Prolog, Python, Relaxngcompact, Rhtml, Ruby, Scala, Scheme, Sgml,
	Sql, SqlMysql, SqlPostgresql, Tcl, Texinfo, Xml, Xslt, Yacc
	Copyright (C) 2006-2010 John MacFarlane
	Web:  http://johnmacfarlane.net/pandoc
	This is free software; see the source for copying conditions.  There is no
	warranty, not even for merchantability or fitness for a particular purpose.

## ./makepdfs ja
	! LaTeX Error: File `xkeyval.sty' not found.

## iceweasel
search '! LaTeX Error: File `xkeyval.sty' not found.'
> http://ubuntuforums.org/showpost.php?s=de28f5695d6f36f55a9a40b4bbd43985&p=9712566&postcount=3
> Re: xkeyval.sty not found xelatex
> I solved it like this:
>
> Code:
>
>	$ apt-cache search xkeyval
>	texlive-latex-recommended - TeX Live: LaTeX recommended packages
>	$ sudo apt-get install texlive-latex-recommended

## install texlive-latex-recommended
	$sudo aptitude install texlive-latex-recommended

## ./makepdfs ja
		Running XeTeX:
		Pass 1... failed with:
			! Font \@tempfontb="VL PGothic/ICU" at 10.0pt not loadable: Metric (TFM) fil
## replace font
	$ cd ~/repo/progit/latex
	$ cp config.yml config.yml.org
	vi config.yml
replace 'VL Gothic' to 'IPAGothic'

## ./makepdfs ja
	$./makepdfs ja
	
	Will generate pdf for the following languages:
		 ja
	
	The generation process will start now.
	ja:
		Parsing markdown... done
		Creating main.tex for ja... done
		Running XeTeX:
			Pass 1... done
			Pass 2... done
			Pass 3... done
		Moving output to progit.ja.pdf... done	
	
	real	0m20.469s
	user	0m23.815s
	sys	0m1.060s
	
	
	Done!Linux Microknoppix 3.0.4 #1 SMP PREEMPT Mon Oct 17 07:15:29 UTC 2011 i686 GNU/Linux

## done!
	$ ls *.pdf
	progit.ja.pdf
You can see it like this:
> $ xpdf progit.ja.pdf

## progit
### last commit
	commit 92feb6631b83bd9ec52b4f9d81d6f4ff528c4e0b
	Merge: c81c8d5 789a20c
	Author: Scott Chacon <schacon@gmail.com>
	Date:   Sat May 12 09:14:40 2012 -0700
	
	    Merge pull request #201 from PinGwynn/feature
	    
	    Added russian titles in to ebooks maker

## ja
	$ tig
	$ t
drwxr-xr-x TAKAGI Masahiro    2011-11-29 04:13 ja

