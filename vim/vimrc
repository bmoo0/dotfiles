"======================================================
"-----------------Ben's neo vimrc----------------------
"======================================================


"======================================================
"-----------------Table of Contents--------------------
"======================================================
" 1) functions                                        -
" 2) general settings                                 -
" 3) vundle plugins                                   -
" 4) individual plugin configurations                 -
" 5) commands                                         -
" 6) key remappings                                   -
" 7) abbreviations                                    -
"======================================================




"======================================================
" 1) functions ----------------------------------------
"======================================================


function! ToggleCompileErrors()
				:if g:syntastic_is_open 
								:call SyntasticReset()
								let g:syntastic_is_open = 0
				:else
								:call SyntasticCheck()
								let g:syntastic_is_open = 1
				:endif
endfunction

" Check operatint system for OS dependant code
function! CheckOperatingSystem()
				let g:OS = 'linux'
				let os = substitute(system('uname'), '\n', '', '')
				:if os == 'Darwin' || os == 'Mac'
								let g:OS = 'osx'
				:endif
endfunction


"======================================================


"======================================================
" 2) general settings ---------------------------------
"======================================================

set nocompatible
syntax on " aw my first change <-
set number

"" Tabs
set tabstop=4
set softtabstop=4
set shiftwidth=4
set expandtab
set cursorline 		" horizontal line
set showmatch 		" show matching brackets
set novisualbell  " no blinking
set noerrorbells  " no noise
set wrapmargin=0  " turns off automatic newlines

" Vim Panes settings
set splitbelow
set splitright

" Spaces and indents
set encoding=utf-8
set smarttab

" Set leader key
let mapleader = "\<Space>"

let g:syntastic_is_open = 0 " for toggle compiler errors func 

" Allow vim to find coloscheme 
set rtp+=~/.vim/bundle/vim-colorscheme-primary

" Link clipboard to mac clipboard
set clipboard=unnamed

filetype plugin indent on

" > Setup backup/swap/undo
" ========================
if !isdirectory($HOME . '/.vim/.backup')
    silent !mkdir -p ~/.vim/.backup >/dev/null 2>&1
endif
set backupdir-=.
set backupdir+=.
set backupdir-=~/
set backupdir^=~/.vim/.backup/
set backupdir^=./.vim-backup/
set backup

if !isdirectory($HOME . '/.vim/.swap')
    silent !mkdir -p ~/.vim/.swap >/dev/null 2>&1
endif
set directory=./.vim-swap//
set directory+=~/.vim/.swap//
set directory+=~/.tmp//
set directory+=.

if exists('+undofile')
    if !isdirectory($HOME . '/.vim/.undo')
        silent !mkdir -p ~/.vim/.undo >/dev/null 2>&1
    endif
    set undodir=./.vim-undo//
    set undodir+=~/.vim/.undo//
    set undofile
endif

" startup function calls
:call CheckOperatingSystem()

"======================================================


"======================================================
" 3) vundle plugins -----------------------------------
"======================================================


" Beginning of vundle plugins
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()

" let Vundle manage Vundle, required
Plugin 'VundleVim/Vundle.vim'

" Airline tag plugin
Plugin 'vim-airline/vim-airline'
Plugin 'vim-airline/vim-airline-themes'

Plugin 'vimwiki/vimwiki'

" Syntasitc (syntax checker)
Plugin 'scrooloose/syntastic'

Plugin 'tpope/vim-surround'
Plugin 'tpope/vim-fugitive'
Plugin 'ctrlpvim/ctrlp.vim'

" End of vundle plugins
call vundle#end()

"======================================================


"======================================================
" 4) individual plugin configurations -----------------
"======================================================


" > Airline settings 
" ==================
if !exists('g:airline_symbols')
				let g:airline_symbols = {}
endif

let g:airline_powerline_fonts = 1
let g:airline_theme='papercolor' " previously was bubblegum
let g:airline_skip_empty_sections=0
let g:airline#extensions#branch#enabled=1
set statusline=%=&P\ %f\ %m
set fillchars=vert:\ ,stl:\ ,stlnc:\
set laststatus=2
set noshowmode

" airline tabline setup
let g:airline#extensions#tabline#enabled = 1
let g:airline#extensions#tabline#show_tabs = 1
let g:airline#extensions#tabline#show_splits = 0
let g:airline#extensions#tabline#tab_min_count = 1
let g:airline#extensions#tabline#tab_nr_type = 1
let g:airline#extensions#tabline#show_tab_nr= 0
let g:airline#extensions#tabline#formatter = 'default'
let g:airline#extensions#tabline#fnamemod = ':t'

" rename label for buffers (default: 'buffers')  >
let g:airline#extensions#tabline#buffers_label = 'buffers'

" rename label for tabs (default: 'tabs')  >
let g:airline#extensions#tabline#tabs_label = 'tabs'

" change the symbol for skipped tabs/buffers (default '...') >
let g:airline#extensions#tabline#overflow_marker = '…'

let g:airline#extensions#tabline#buffer_idx_mode = 1

let g:airline#extensions#ale#error_symbol=''
let g:airline#extensions#ale#warning_symbol=''
let g:airline#extensions#ale#show_line_numbers=0

" unicode symbols for airline
let g:airline_left_sep = '»'
let g:airline_left_sep = '▶'
let g:airline_right_sep = '«'
let g:airline_right_sep = '◀'
let g:airline_symbols.crypt = '🔒'
let g:airline_symbols.linenr = '☰'
let g:airline_symbols.linenr = '␊'
let g:airline_symbols.linenr = '␤'
let g:airline_symbols.linenr = '¶'
let g:airline_symbols.maxlinenr = ''
let g:airline_symbols.maxlinenr = '㏑'
let g:airline_symbols.branch = '⎇'
let g:airline_symbols.paste = 'ρ'
let g:airline_symbols.paste = 'Þ'
let g:airline_symbols.paste = '∥'
let g:airline_symbols.spell = 'Ꞩ'
let g:airline_symbols.notexists = 'Ɇ'
let g:airline_symbols.whitespace = 'Ξ'

" powerline symbols for airline
let g:airline_left_sep = ''
let g:airline_left_alt_sep = ''
let g:airline_right_sep = ''
let g:airline_right_alt_sep = ''
let g:airline_symbols.branch = ''
let g:airline_symbols.readonly = ''
let g:airline_symbols.linenr = '☰'
let g:airline_symbols.maxlinenr = ''

" fugitive integration
let g:airline#extensions#fugitiveline#enabled = 1

" airline branch
let g:airline#extensions#branch#enabled = 1
let g:airline#extensions#branch#empty_message = ''
let g:airline#extensions#branch#sha1_len = 10
let g:airline#extensions#branch#format = 2

" > Syntactic settings
" ====================
set statusline+=%#warningmsg#
set statusline+=%{SyntasticStatuslineFlag()}
set statusline+=%*
let g:syntastic_always_populate_loc_list = 1
let g:airline#extensions#syntastic#enabled = 1
let g:syntastic_auto_loc_list = 1
let g:syntastic_check_on_open = 0
let g:syntastic_check_on_wq = 0


" > Pandoc settings
" =================
augroup pandoc_syntax
		au! BufNewFile,BufFilePRe,BufRead *.md set filetype=markdown.pandoc " Use markdown syntax only on markdonwn files

" > CtrlP settings
" =================
let g:airline#extensions#ctrlp#color_template = 'insert' 
let g:airline#extensions#ctrlp#color_template = 'normal'
let g:airline#extensions#ctrlp#color_template = 'visual'
let g:airline#extensions#ctrlp#color_template = 'replace'

"======================================================


"======================================================
" 5) commands -----------------------------------------
"======================================================


command ToggleCompileErrors :call ToggleCompileErrors()
command VerticalTerm vsplit <bar> terminal
command HorizontalTerm split <bar> terminal

"======================================================


"======================================================
" 6) key remappings -----------------------------------
"======================================================


" Map space to nothing since it is my leader key
nnoremap <SPACE> <Nop>

" Easier mapping for panes navigation
nnoremap <C-J> <C-W><C-J>
nnoremap <C-K> <C-W><C-K>
nnoremap <C-L> <C-W><C-L>
nnoremap <C-H> <C-W><C-H>

" Resize panes
nnoremap <silent> <C-w>h 5<C-w><
nnoremap <silent> <C-w>j 5<C-w>-
nnoremap <silent> <C-w>k 5<C-w>+
nnoremap <silent> <C-w>l 5<C-w>>

" Split panes
nnoremap <silent> <Leader>v :vsp <Space>
nnoremap <silent> <Leader>h :sp <Space>

" Change relative number mode
nnoremap <silent> <C-N> :set relativenumber! <cr>

" Keymaps for buffer navigation
nnoremap <silent> <Leader>l :ls<CR>
nnoremap <silent> <Leader>p :bp<CR>
nnoremap <silent> <Leader>n :bn<CR>
nnoremap <silent> <Leader>g :e#<CR>
nnoremap <silent> <Leader>1 :1b<CR>
nnoremap <silent> <Leader>2 :2b<CR>
nnoremap <silent> <Leader>3 :3b<CR>
nnoremap <silent> <Leader>4 :4b<CR>
nnoremap <silent> <Leader>5 :5b<CR>
nnoremap <silent> <Leader>6 :6b<CR>
nnoremap <silent> <Leader>7 :7b<CR>
nnoremap <silent> <Leader>8 :8b<CR>
nnoremap <silent> <Leader>9 :9b<CR>
nnoremap <silent> <Leader>0 :10b<CR>

nnoremap <silent> <Leader>e :edit <Space>

" tab control key mappings
nnoremap <C-1> <Plug>AirlineSelectTab1
nnoremap <C-2> <Plug>AirlineSelectTab2
nnoremap <C-3> <Plug>AirlineSelectTab3
nnoremap <C-4> <Plug>AirlineSelectTab4
nnoremap <C-5> <Plug>AirlineSelectTab5
nnoremap <C-6> <Plug>AirlineSelectTab6
nnoremap <C-7> <Plug>AirlineSelectTab7
nnoremap <C-8> <Plug>AirlineSelectTab8
nnoremap <C-9> <Plug>AirlineSelectTab9
nnoremap <Leader>q <Plug>AirlineSelectPrevTab
nnoremap <Leader>e <Plug>AirlineSelectNextTab

" new tab
nnoremap <silent> <Leader>t :tabnew <Space>

" Toggle syntastic window
nnoremap <silent> <Leader>b :ToggleCompileErrors<CR>


"======================================================

"======================================================
" 7) abbreviations ------------------------------------
"======================================================


ab #i  #include <
ab iio #include <stdio.h>
ab _int main(int argc, char **argv)
ab #d #define

"------------------------------------------------------
