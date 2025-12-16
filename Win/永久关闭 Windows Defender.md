### 准备
首先关闭`篡改保护`（防止后续修改不成功）：`Windows 安全中心` -> `病毒和威胁保护` -> 管理设置


### 修改注册表
1. 打开注册表：Win + R 输入 `regedit` 并回车
2. 进入目录：`计算机\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender`，在这个目录下
3. 先新建几个`DWORD(32位)值`，并将值修改为 1
   - `DisableAntiSpyware`
   - `DisableRealtimeMonitoring`
   - `DisableAntiVirus`
   - `DisableSpecialRunningModes`
   - `DisableRoutinelyTakingAction`
   - `ServiceKeepAlive`
  
4. 然后新建项：`Real-Time Protection`，然后再设置几个值，值为 1
   - `DisableBehaviorMonitoring`
   - `DisableOnAccessProtection`
   - `DisableRealtimeMonitoring`
   - `DisableScanOnRealtimeEnable`
  
5. 再新建项：`Signature Updates`
   - `ForceUpdateFromMU`，值为 1
  
6. 最后一个项：`Spynet`
   - `DisableBlockAtFirstSeen`，值为 1
  
7. 重启电脑，使设置生效

### 恢复
恢复就比较简单了，增加了什么改回去就可以了
  
