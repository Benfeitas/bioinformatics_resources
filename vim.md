# Cheatsheet

## Movement
- shift + G # jump to end
- gg # jump to start

## Folding
" This is a fold {{{1
some text and `code`
" }}}1


- z + o # opens a fold at the cursor.
- z + Shift + o # opens all folds at the cursor.
- z + c  # closes a fold at the cursor.
- z + m  # increases the `foldlevel` by one.
- z + Shift + m # closes all open folds.
- z + r # decreases the `foldlevel` by one.
- z + Shift + r # decreases the `foldlevel` to zero -- all folds will be open.

## Working with Rmd
To launch terminal:
- <localleader> t  #launch terminal
- <localleader> q #quit terminal
- <localleader> c #run chunk





- <localleader>l <Plug>SlimeLineSend #send line
- <localleader>p <Plug>SlimeParagraphSend #send paragraph
- <localleader>s <Plug>SlimeRegionSend #send highlighted region
- <localleader>c <Plug>SlimeSendCell #send cell
- <localleader>w viw<Plug>SlimeRegionSend #send word
- <localleader>a ggVG<Plug>SlimeRegionSend #send whole file
- <localleader>t :call OpenTerminal()<CR>
- <localleader>q :call CloseTerminal()<CR>
- <localleader>h :call PrintHead()<CR>
- <localleader>C :SlimeSend0 "\x03"<CR>
- <localleader>f :call FindFunction()<CR><Plug>SlimeRegionSend<CR>


