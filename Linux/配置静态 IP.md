1. **确定网络接口名称**：首先，使用以下命令查看当前的网络接口名称：

   ```bash
   ip link show
   ```
   在输出结果中，找到类似 `ens33` 或 `eth0` 的接口名称。

2. **编辑网络接口配置文件**：使用文本编辑器（如 `nano` 或 `vi`）打开 `/etc/network/interfaces` 文件：

   ```bash
   sudo nano /etc/network/interfaces
   ```

3. **添加或修改接口配置**：在文件中，为您的网络接口添加或修改以下配置（请根据实际情况编辑）：

   ```ini
   # 配置静态 IP 的网络接口
   auto ens33
   iface ens33 inet static
       address 192.168.1.100
       netmask 255.255.255.0
       gateway 192.168.1.1
       dns-nameservers 8.8.8.8 8.8.4.4
   ```

   在上述配置中：

   - `auto ens33`：确保系统在启动时自动启用该接口。
   - `iface ens33 inet static`：指定接口使用静态 IPv4 配置。
   - `address`：设置静态 IP 地址。
   - `netmask`：设置子网掩码。
   - `gateway`：设置默认网关。
   - `dns-nameservers`：设置 DNS 服务器地址。

   请将 `ens33` 替换为您实际的网络接口名称，并根据实际网络设置调整 IP 地址、网关和 DNS 信息。

4. **保存并关闭文件**：编辑完成后，保存更改并退出编辑器。

5. **重启网络服务**：使更改生效，运行以下命令重启网络服务：

   ```bash
   sudo systemctl restart networking
   ```

6. **验证配置**：使用以下命令检查网络接口的 IP 地址，确认配置已生效：

   ```bash
   ip addr show ens33
   ```
   请将 `ens33` 替换为您的实际网络接口名称。

