```vim=
" general setting
syntax on 
filetype plugin indent on
set autoindent
set number
set relativenumber
set cursorline
set shiftwidth=4
set tabstop=4
set mouse=a
set incsearch
set wrap
set scrolloff=6
set noeb
set t_Co=256
set foldmethod=manual
set path+=/usr/local/include/

" compile and run shortcut for c, cpp, python 
autocmd filetype python nnoremap <Space>c :w <bar> exec '!python3 '.shellescape('%')<CR>
autocmd filetype c nnoremap <Space>c :w <bar> exec '!gcc '.shellescape('%').' -o '.shellescape('%:r').' && ./'.shellescape('%:r')<CR>
autocmd filetype cpp nnoremap <Space>c :w <bar> exec '!g++ '.shellescape('%').' -o '.shellescape('%:r').' && ./'.shellescape('%:r')<CR>
autocmd filetype python map <Space>d :call flake8#Flake8()<CR>

" html, css and markdown setting
let g:user_emmet_install_global = 0
autocmd filetype html,css EmmetInstall
autocmd filetype html nnoremap <Space>f ihtml:5
autocmd filetype html nnoremap -- :set lazyredraw<cr>mhvato<ESC>i<!-- <ESC>vatA --><ESC>`h:set nolazyredraw<cr>
autocmd filetype html nnoremap == :set lazyredraw<cr>mhvat<ESC>4xvato<ESC>5X`h:set nolazyredraw<cr>
let g:user_emmet_leader_key=','
let g:vim_markdown_no_default_key_mappings = 1
let g:vim_markdown_toc_autofit = 1
let g:vim_markdown_math = 1 " LaTex math
let g:vim_markdown_frontmatter = 1 " YAML Front Matter
let g:bracey_auto_start_browser = 0


call plug#begin()

Plug 'neoclide/coc.nvim'
Plug 'jiangmiao/auto-pairs'
Plug 'gruvbox-community/gruvbox'
Plug 'vim-airline/vim-airline'
Plug 'vim-airline/vim-airline-themes'
Plug 'preservim/nerdtree'
Plug 'dense-analysis/ale'
Plug 'nvie/vim-flake8'
Plug 'godlygeek/tabular'
Plug 'instant-markdown/vim-instant-markdown', {'for': 'markdown', 'do': 'yarn install'}
Plug 'plasticboy/vim-markdown'
Plug 'mattn/emmet-vim'

call plug#end()

" use <tab> to trigger completion and navigate to the next complete item
function! CheckBackspace() abort
  let col = col('.') - 1
  return !col || getline('.')[col - 1]  =~# '\s'
endfunction


inoremap <silent><expr> <Tab>
      \ coc#pum#visible() ? coc#pum#next(1) :
      \ CheckBackspace() ? "\<Tab>" :
      \ coc#refresh()

" general shortcut
nnoremap <Space>v <C-w>v <CR> " split window vertically 
nnoremap <Space>b <C-w>s <CR> " split window horizontally
nnoremap <Space>m <C-w>= <CR> " make split windows equal width & height
nnoremap <Space>q <ESC>:close <CR> " close current split window
nnoremap <Space>h <C-w>h <CR> " move cursor to left window
nnoremap <Space>j <C-w>j <CR> " move cursor to under window
nnoremap <Space>k <C-w>k <CR> " move cursor to above window
nnoremap <Space>l <C-w>l <CR> " move cursor to right window
nnoremap <Space>n <C-f> <CR> " move cursor to next page
nnoremap <Space>p <C-b> <CR> " move cursor to previous page
nnoremap <Space>u <C-r> <CR> " recover undo
inoremap <Space>e <ESC>:NERDTreeToggle<CR>
nnoremap <Space>e <ESC>:NERDTreeToggle<CR>
noremap <Space> <S-n>
nnoremap <CR> n

" editer colorscheme
colorscheme gruvbox
```
