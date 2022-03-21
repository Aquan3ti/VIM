set nocompatible
filetype on
filetype indent on
filetype plugin on
filetype plugin indent on
"set mouse=a
set encoding=utf-8
let &t_ut=''
set expandtab
set tabstop=2
set shiftwidth=2
set softtabstop=2
set list
set listchars=tab:▸\ ,trail:▫
set scrolloff=5
set tw=0
set indentexpr=
set backspace=indent,eol,start
set foldmethod=indent
set foldlevel=99
let &t_SI = "\<Esc>]50;CursorShape=1\x7"
let &t_SR = "\<Esc>]50;CursorShape=2\x7"
let &t_EI = "\<Esc>]50;CursorShape=0\x7"
set laststatus=2
set autochdir
au BufReadPost * if line("'\"") > 1 && line("'\"") <= line("$") | exe "normal! g'\"" | endif
set scrolloff=5

" use space instead  : in normal mode
nmap <space> :
" use jk instead Esc in insert mode 
imap jk <Esc>

" 语法高亮
syntax on
" 设置行号
set number
" 设置相对行号
set relativenumber
" 显示下划线
set cursorline
" 字自动换行
set wrap
" 屏幕显示按键
set showcmd
" 命令模式下补全提示
set wildmenu
" 设置搜索结果高亮显示
set hlsearch
" 设置：时去掉高亮，避免打开新文件时还在搜索高亮。
exec "nohlsearch"
" 设置搜索时高亮
set incsearch
" 智能大小写
set smartcase

" 安装插件
call plug#begin('~/.vim/plugged')
Plug 'vim-airline/vim-airline'

Plug 'preservim/nerdtree'
" Error checking
Plug 'dense-analysis/ale'

" Auto Complete
Plug 'Valloric/YouCompleteMe'

Plug 'nathanaelkane/vim-indent-guides'

" Auto pair
Plug 'jiangmiao/auto-pairs'
call plug#end()



" ===
" " === NERDTree
" " ===
map ff :NERDTreeToggle<CR>
let NERDTreeMapOpenExpl = ""
let NERDTreeMapUpdir = ""
let NERDTreeMapUpdirKeepOpen = "l"
let NERDTreeMapOpenSplit = ""
let NERDTreeOpenVSplit = ""
let NERDTreeMapActivateNode = "i"
let NERDTreeMapOpenInTab = "o"
let NERDTreeMapPreview = ""
let NERDTreeMapCloseDir = "n"
let NERDTreeMapChangeRoot = "y"


" ==
" == NERDTree-git
" ==
let g:NERDTreeIndicatorMapCustom = {
  \ "Modified"  : "✹",
  \ "Staged"    : "✚",
  \ "Untracked" : "✭",
  \ "Renamed"   : "➜",
  \ "Unmerged"  : "═",
  \ "Deleted"   : "✖",
  \ "Dirty"     : "✗",
  \ "Clean"     : "✔︎",
  \ "Unknown"   : "?"
  \ }


" ===
" === You Complete ME
" ===
nnoremap gd :YcmCompleter GoToDefinitionElseDeclaration<CR>
nnoremap g/ :YcmCompleter GetDoc<CR>
nnoremap gt :YcmCompleter GetType<CR>
nnoremap gr :YcmCompleter GoToReferences<CR>
let g:ycm_autoclose_preview_window_after_completion=0
let g:ycm_autoclose_preview_window_after_insertion=1
let g:ycm_use_clangd = 0
let g:ycm_python_interpreter_path = "/bin/python3"
let g:ycm_python_binary_path = "/bin/python3"


" ===
" === ale
" ===
"自定义error和warning图标
let g:ale_sign_error = '✗'
let g:ale_sign_warning = '⚡'
""在vim自带的状态栏中整合ale
let g:ale_statusline_format = ['✗ %d', '⚡ %d', '✔ OK']"
let b:ale_linters = ['pylint']
let b:ale_fixers = ['autopep8', 'yapf']


" ===
" === vim-indent-guide
" ===
let g:indent_guides_guide_size = 1
let g:indent_guides_start_level = 2
let g:indent_guides_enable_on_vim_startup = 1
let g:indent_guides_color_change_percent = 1
silent! unmap <LEADER>ig
autocmd WinEnter * silent! unmap <LEADER>ig
