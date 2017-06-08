### 安装
[spf13-vim](https://github.com/spf13/spf13-vim)

### 使用
#### 一. 分割Panel
**1.分屏启动**

```bash
# O 为大写字母,大小写表示分屏方向;
# n 为数字,表示分为几个屏
# 垂直分屏
vim On file1,file2...
# 水平分屏
vim on file1,file2...
```

**2.关闭分屏**

关闭当前: `Ctrl+W` `c`

关闭当前,如果只剩下一个窗口则关闭vim: `Ctrl+W` `q`

**2.启动后分屏**

上下分割当前文件: `Ctrl+W` `s`

上下分割并打开新文件: `:sp filename`

左右分割当前文件: `Ctrl+W` `v`

左右分割并打开新文件: `:vsp filename`

**3.切换分屏**

左下上右切换分屏: `Ctrl+W` `h/j/k/l`

切换下一个分屏: `Ctrl+W` `w`

**4.移动分屏**

左下上右移动分屏: `Ctrl+W` `H/J/K/L`

**5.调整分屏尺寸**

所有分屏大小一样: `Ctrl+W` `=`

增加高度: `Ctrl+W` `+`

减小高度: `Ctrl+W` `-`

### 参考
- [酷壳](http://coolshell.cn/)
