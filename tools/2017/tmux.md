# tmux 按照与使用
### 安装tmux
`sudo apt-get install tmux`
安装完后安装`.tmux`: 
```bash
cd
rm -rf .tmux
git clone https://github.com/gpakosz/.tmux.git
ln -s .tmux/.tmux.conf
cp .tmux/.tmux.conf.local .
vim .tmux.conf
# 添加下面设置默认zsh打开tmux
# set-option -g default-shell /bin/zsh
```

### 使用
#### session
- `tmux new -s session_name` 创建一个叫做 session_name 的 tmux session
- `tmux attach -t session_name`重新开启叫做 session_name 的 tmux session
- `tmux switch -t session_name`转换到叫做 session_name 的 tmux session
- `tmux list-sessions`列出现有的所有 session
- `tmux detach (prefix + d)`离开当前开启的 session

#### window
- `tmux new-window (perfix + c)` 创建一个新的 window
- `tmux select-window -t :0-9 (perfix + 0-9)` 根据索引转到该 window
- `tmux rename-window (perfix + ,)` 重命名当前 window

#### panel
- `tmux split-window (perfix + “)` 将 window 垂直划分为两个 pane
- `tmux split-window -h (perfix + %)` 将 window 水平划分为两个 pane
- `tmux swap-pane -[UDLR] (perfix + { or })` 在指定的方向交换 pane
- `tmux select-pane -[UDLR]` 在指定的方向选择下一个 pane
- `tmux select-pane -t :.+` 选择按数字顺序的下一个 pane
