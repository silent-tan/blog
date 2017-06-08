### 安装
[spf13-vim](https://github.com/spf13/spf13-vim)

### 使用

#### 一.多文件编辑：缓冲区管理

**1.打开**

```bash
# 打开文件到缓存区
vim filename1 filename2
```

**2.切换缓冲区**

- 显示缓冲区列表: `ls`
- 切换到下一个缓冲区: `:bn` 或者 `Ctrl` `^`
- 切换到上一个缓冲区: `:bp`
- 切换到第一个缓冲区: `:bf`
- 切换到最后一个缓冲区: `:bl`
- 切换到索引或者表达式目标缓冲区: `:b {index, expression}`

**3.关闭缓冲区**

- 关闭: `bd`
- 强制关闭: `bd!`

#### 二. 分屏管理

**1.分屏启动**

```bash
# O 为大写字母,大小写表示分屏方向;
# n 为数字,表示分为几个屏
# 垂直分屏
vim -On file1,file2...
# 水平分屏
vim -on file1,file2...
```

**2.关闭分屏**

关闭当前: `Ctrl+W` `c` 或者 `:clo`

关闭当前,如果只剩下一个窗口则关闭vim: `Ctrl+W` `q`

**3.启动后分屏**

上下分割当前文件: `Ctrl+W` `s`

上下分割并打开新文件: `:sp filename`

左右分割当前文件: `Ctrl+W` `v`

左右分割并打开新文件: `:vsp filename`

水平分屏并打开buffer: `sb {number}`

垂直分屏并打开buffer: `verticle sb {number}`

**4.切换分屏**

左下上右切换分屏: `Ctrl+W` `h/j/k/l`

切换下一个分屏: `Ctrl+W` `w`

**5.移动分屏**

左下上右移动分屏: `Ctrl+W` `H/J/K/L`

**6.调整分屏尺寸**

所有分屏大小一样: `Ctrl+W` `=`

增加高度: `Ctrl+W` `+`

减小高度: `Ctrl+W` `-`

#### 三.键位映射Map

**1.映射种类**

- 用于普通模式: 输入命令时
- 用于可视模式: 可视区域高亮并输入命令
- 用于操作等待模式: 操作符等待中，如d,y,c
- 用于插入模式: 也用于替换模式
- 用于命令行模式: 输入: 或者 /

| Command<br/>命令|Normal<br/>常规模式|Visual<br/>可视模式|Operator Pending<br/>运算符模式|Insert Only<br/>插入模式|Command Line<br/>命令行模式|
|:---------:|:---------:|:--------:|:---------:|:-----------:|:---------:|
|:map|y|y|y|||
|:nmap|y|||||
|:vmap|||y|||
|:omap||||y||
|:map!||||y|y|
|:imap||||y||
|:cmap|||||y|


### 参考
- [酷壳](http://coolshell.cn/)
- [vim map自定义快捷键](http://blog.jasonding.top/2015/04/29/Developer%20Kits/%E3%80%90Vim%E3%80%91%E4%BD%BF%E7%94%A8map%E8%87%AA%E5%AE%9A%E4%B9%89%E5%BF%AB%E6%8D%B7%E9%94%AE/)
