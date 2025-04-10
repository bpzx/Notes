命令：`alias ls='ls --color=auto'`

修改 `~/.bashrc`，然后 `source ~/.bashrc` 使生效即可

Debian 12 已有配置，取消注释后 `source` 下
```
export LS_OPTIONS='--color=auto'
eval "$(dircolors)"
alias ls='ls $LS_OPTIONS'
alias ll='ls $LS_OPTIONS -l'
```
