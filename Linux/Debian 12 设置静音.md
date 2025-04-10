在 Debian 12 中，您可以通过以下方法关闭在使用 Tab 键进行命令补全时产生的提示音：

1. **修改 `/etc/inputrc` 文件**：

   使用文本编辑器（如 `nano` 或 `vim`）打开 `/etc/inputrc` 文件：

   ```bash
   sudo nano /etc/inputrc
   ```


   找到以下行（可能带有注释符号 `#`）：

   ```
   # set bell-style none
   ```


   去掉行首的 `#`，将其修改为：

   ```
   set bell-style none
   ```


   保存并关闭文件。

2. **使更改生效**：

   重新启动系统，或注销并重新登录，以应用上述更改。

完成上述步骤后，使用 Tab 键进行命令补全时，终端将不再发出提示音。
