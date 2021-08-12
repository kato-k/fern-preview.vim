# fern-preview.vim

Add a file preview window to [fern.vim](https://github.com/lambdalisue/fern.vim).

## Features

- File preview in popup window or floating window
- Toggle auto preview mode
- Scroll preview window

## Demo

![fern-preview](https://user-images.githubusercontent.com/5423775/120148266-ec0ec680-c222-11eb-9a3f-42ff148708ec.gif "fern-preview")


## Requirements

- [fern.vim](https://github.com/lambdalisue/fern.vim)

## Installation

### vim-plug

```vim
Plug 'lambdalisue/fern.vim'
Plug 'yuki-yano/fern-preview.vim'
```

### dein

```vim
call dein#add('lambdalisue/fern.vim')
call dein#add('yuki-yano/fern-preview.vim')
```

## Usage

### Mapping

```vim
function! s:fern_settings() abort
  nmap <silent> <buffer> p     <Plug>(fern-action-preview:toggle)
  nmap <silent> <buffer> <C-p> <Plug>(fern-action-preview:auto:toggle)
  nmap <silent><expr> <buffer> <C-d> fern_preview#is_win_visible()?"<Plug>(fern-action-preview:scroll:down:half)":"<C-d>"
  nmap <silent><expr> <buffer> <C-u> fern_preview#is_win_visible()?"<Plug>(fern-action-preview:scroll:up:half)":"<C-u>"
endfunction


augroup fern-settings
  autocmd!
  autocmd FileType fern call s:fern_settings()
augroup END
```

### Use smart_preview function example

```vim
function! s:fern_settings() abort
  nmap <silent> <buffer> <expr> <Plug>(fern-quit-or-close-preview) fern_preview#smart_preview("\<Plug>(fern-action-preview:close)", ":q\<CR>")
  nmap <silent> <buffer> q <Plug>(fern-quit-or-close-preview)
endfunction
```
