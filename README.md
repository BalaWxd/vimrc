# vimrc
A personal configuration for vim using amix/vimrc and phpactor for php development.

The configuration works on Linux with VIM 8.

## VIM runtime

```
 git clone --depth=1 https://github.com/amix/vimrc.git ~/.vim_runtime
 sh ~/.vim_runtime/install_awesome_vimrc.sh
```

## Phactor - PHP

```
 # Plugins
 git clone https://github.com/ncm2/ncm2.git ~/.vim_runtime/my_plugins/ncm2
 git clone https://github.com/phpactor/ncm2-phpactor.git ~/.vim_runtime/my_plugins/ncm2-phpactor
 git clone https://github.com/phpactor/phpactor.git ~/.vim_runtime/my_plugins/phpactor
 git clone https://github.com/roxma/nvim-yarp.git ~/.vim_runtime/my_plugins/nvim-yarp
 git clone https://github.com/roxma/vim-hug-neovim-rpc.git ~/.vim_runtime/my_plugins/vim-hug-neovim-rpc
 
 cd ~/.vim_runtime/my_plugins/phpactor && composer install
 
 # Install neovim module
 python3 -m pip install neovim && python3 -m pip install pyvim
```

## VIM language syntax check and fixes

```
 # Load syntax, indent, ftplugin, many languages
 git clone https://github.com/sheerun/vim-polyglot.git ~/.vim_runtime/my_plugins/vim-polyglot
```

```
 # Check syntax in Vim asynchronously and fix files, with Language Server Protocol (LSP) support
 git clone https://github.com/dense-analysis/ale.git ~/.vim_runtime/my_plugins/ale
```

## Fuzzy finder

```
 # Install fzf (Fuzzy finder)
 git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
 ~/.fzf/install
``` 

## my_configs.vim

```

 " Phpactor | https://phpactor.github.io/phpactor/vim-plugin.html
 
 " Include use statement
 nmap <Leader>u :call phpactor#UseAdd()<CR>
 
 " Invoke the context menu
 nmap <Leader>mm :call phpactor#ContextMenu()<CR>
 
 " Invoke the navigation menu
 nmap <Leader>nn :call phpactor#Navigate()<CR>
 
 " Goto definition of class or class member under the cursor
 nmap <Leader>oo :call phpactor#GotoDefinition()<CR>
 nmap <Leader>oh :call phpactor#GotoDefinitionHsplit()<CR>
 nmap <Leader>ov :call phpactor#GotoDefinitionVsplit()<CR>
 nmap <Leader>ot :call phpactor#GotoDefinitionTab()<CR>
 
 " Show brief information about the symbol under the cursor
 nmap <Leader>K :call phpactor#Hover()<CR>
 
 " Transform the classes in the current file
 nmap <Leader>tt :call phpactor#Transform()<CR>
 
 " Generate a new class (replacing the current file)
 nmap <Leader>cc :call phpactor#ClassNew()<CR>
 
 " Extract expression (normal mode)
 nmap <silent><Leader>ee :call phpactor#ExtractExpression(v:false)<CR>
 
 " Extract expression from selection
 vmap <silent><Leader>ee :<C-U>call phpactor#ExtractExpression(v:true)<CR>
 
 " Extract method from selection
 vmap <silent><Leader>em :<C-U>call phpactor#ExtractMethod()<CR>
 
 " Neovim completion manager NCM2 | https://github.com/phpactor/ncm2-phpactor
 autocmd BufEnter * call ncm2#enable_for_buffer()
 set completeopt=noinsert,menuone,noselect
 
 " CLI fuzzy finder fzf | https://github.com/junegunn/fzf
 if executable('fzf')
   set rtp+=~/.fzf
 endif
 
 " Custom tweaks

 " Ag search
 if executable('ag')
   let g:ackprg = 'ag --nogroup --nocolor --column'
 endif
 
 " vim-commentary, change PHP code comment string
 au Filetype php setlocal commentstring=//\ %s
 
 " A fix for vue project indents
 " As vim_runtime already includes othree/html5.vim, where defines html indents.
 au BufRead,BufNewFile *.vue set filetype=html ts=2 sw=2 sts=2

```
