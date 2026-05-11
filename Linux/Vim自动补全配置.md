# Vim自动补全配置

1. 安装插件管理器（Vim-plug）：
   curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
   
2. 创建Vim配置文件：
   vim ~/.vimrc

3. 配置文件内容：
    ```.vimrc
    " 启用插件
    call plug#begin('~/.vim/plugged')
    
    " 自动补全插件
    Plug 'jiangmiao/auto-pairs'
    Plug 'ervandew/supertab'
    
    call plug#end()
    
    " 基本设置
    syntax on           " 语法高亮
    " set number          " 显示行号
    set autoindent      " 自动缩进
    set smartindent     " 智能缩进
    
    " 空格缩进设置
    set expandtab       " 按Tab键时插入空格
    set tabstop=4       " Tab显示为4空格宽度
    set shiftwidth=4    " 自动缩进使用4空格
    set softtabstop=4   " 退格键一次删除4空格
    
    " 自动补全设置
    inoremap ( ()<Left>
    inoremap [ []<Left>
    inoremap { {}<Left>
    inoremap ' ''<Left>
    inoremap " ""<Left>
    
    " 使用Tab键进行补全
    let g:SuperTabDefaultCompletionType = "<c-n>"
    ```
    
4. 安装插件：

    在vim中执行  **:PlugInstall** 启动插件

    :PlugStatus    # 查看插件状态
    :PlugInstall   # 重新安装插件
