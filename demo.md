>一些实操记录
>生效 ~/.vimrc  配置文件
>vim   ==> :source ~/.vimrc

 ```bash
#配置快捷键
, + w  ===> 实现  wq!
let mapleader = ","
nmap <leader>w :wq!<CR>
```

>使用F5 键触发运行当前文件
>注意 vimrc 脚本中 使用 "  单行注释   找资料说是无法 块注释  只能 类似 多行  " 实现多行注释
>然后简单介绍下面的脚本，触发F5 ，保存文件，然后将判断文件类型，然后编译，当前文件编译生成同文件名（没有后缀），然后计算运行了多长时间
```bash
"C,C++ 按F5编译运行
map <F5> :call CompileRunGcc()<CR>
func! CompileRunGcc()
    exec "w"
    if &filetype == 'c'
        exec "!g++ % -o %<"
        exec "!time ./%<"
    elseif &filetype == 'cpp'
        exec "!g++ % -o %<"
        exec "!time ./%<"
    endif    
endfunc
```

>再来一个简单的gdb 调试 的脚本
>
```bash
"C,C++的调试
map <F8> :call Rungdb()<CR>
func! Rungdb()
exec "w"
exec "!g++ % -g -o %<"
exec "!gdb ./%<"
endfunc
```


