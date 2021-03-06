# Install

## With [Vundle][]:

Add the following to `.vimrc`

    Plugin 'mikea1729/octave.vim'

  [Vundle]: https://github.com/VundleVim/Vundle.vim

## With [pathogen.vim][]:

    cd ~/.vim/bundle
    git clone git://github.com/mikea1729/octave.vim.git

  [pathogen.vim]: https://github.com/tpope/vim-pathogen

# Pedigree

`syntax/octave.vim` is mirrored from: http://www.vim.org/scripts/script.php?script_id=3600

`indent/octave.vim` from https://github.com/louima/octave.vim--

`plugin/octave.vim` Added to automate installation as described below


# Details

Following copied verbatim from http://www.vim.org/scripts/script.php?script_id=3600

```
description
This file provides syntax highlighting for the GNU Octave programming language.

Features
* Highlights entire Octave grammar (endwhile, endfor, etc.), not just Matlab keywords
* Updated to highlight all core Octave functions as of version 4.2.0
* Highlights user functions and anonymous functions [@(...)] from within the .m file being edited
* Use-dependent highlighting of Octave system variables
   When querying system variables, keyword is highlighted as a constant.  For example, var = true, highlights 'true' as a constant.
   When setting variables or otherwise invoking keyword as a function, keyword is highlighted as a function.  For example, var = true (2,4), highlights 'true' as a function.
* Support for multi-line strings with line continuation characters as well as escaped quotes (\" or \') within string.
* Support for multi-line block comments
* Support for highlighting numbers that use hex (0x) or binary (0b) syntax
* Error highlighting for bad number syntax, bad structure variable names, bad block comments, bad line continuations.
* Optional support for highlighting operators (+, -, *, etc.), user variables, or tabs

Errata
* Occasionally anonymous functions are highlighted as a function even though the instance is of the name as a variable.  This is too difficult to correct without writing a full parser.

OMNIFUNC
* The syntax file has a list of every valid function in Octave which makes it useful as an auto-completion dictionary for use with ViM's omnifunc function.  Once installed, type a few letters of the name of a function and then use Ctrl-X Ctrl-O to bring up a list of possible matches.

Addenda

This script owes some debt to the two existing Octave syntax scripts:
http://www.vim.org/scripts/script.php?script_id=1241
http://www.vim.org/scripts/script.php?script_id=1591

However, it has been thoroughly rewritten and expanded considerably.

install details
Syntax file install on a UNIX-like system

1) mkdir -p ~/.vim/syntax
2) cp octave.vim ~/.vim/syntax/
3) Add the following lines to your ~/.vimrc to get ViM to use the file

----- SNIP -----
" Octave syntax
augroup filetypedetect
  au! BufRead,BufNewFile *.m,*.oct set filetype=octave
augroup END
----- SNIP -----

Optional highlighting of operators (+, -, *, etc.), user variables, or tabs can be had by uncommenting the appropriately tagged lines in octave.vim.

OMNIFUNC install on a UNIX-like system

1) Install the syntax file as described above
2) Add the following lines to your ~/.vimrc after the snippet from step 3 above
----- SNIP -----
" Use keywords from Octave syntax language file for autocomplete
if has("autocmd") && exists("+omnifunc")
   autocmd Filetype octave
   \	if &omnifunc == "" |
   \	setlocal omnifunc=syntaxcomplete#Complete |
   \	endif
endif
----- SNIP -----
```

