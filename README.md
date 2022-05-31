# minidump_parser
## 环境配置
> [旧版WSL的手动安装步骤](https://docs.microsoft.com/zh-cn/windows/wsl/install-manual)
1. 首先在PowerShell(管理员权限下) 开启Linux子系统

``` shell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```
2. 安装 Linux 内核更新包
[Linux内核更新包](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)

3. 设置 WSL 版本
``` shell
wsl --set-default-version 2
```
## 安装 Docker

