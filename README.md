# minidump_parser
## 环境配置
> [旧版WSL的手动安装步骤](https://docs.microsoft.com/zh-cn/windows/wsl/install-manual)
1. 首先在PowerShell(管理员权限下) 开启Linux子系统
``` shell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
shutdown /r /t 0

```
> 重启生效


2. 安装 Linux 内核更新包
[Linux内核更新包](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)


3. 设置 WSL 版本(可选)
``` shell
wsl --set-default-version 2

```

## 安装 Docker
点击下面的链接下载，按照步骤安装后重启即可。
[Docker Desktop](https://desktop.docker.com/win/main/amd64/Docker%20Desktop%20Installer.exe?utm_source=docker&utm_medium=webreferral&utm_campaign=dd-smartbutton&utm_location=header)

## 使用
1. 在 `C:` 盘创建 `dumpdir` 目录
3. 将包含minidump的 `zip` 压缩包、对应版本的`apk`文件 全部放到 `C:\dumpdir`
4. 打开管理员权限的 `PowerShell`，执行下面的命令

```shell
cd C:\dumpdir
Invoke-RestMethod -Uri "https://github.com/tqcq/minidump_parser/archive/refs/heads/master.zip" -OutFile minidump_parser-master.zip
Expand-Archive -Path minidump_parser-master.zip -DestinationPath C:\dumpdir
Del minidump_parser-master.zip
cd C:\dumpdir\minidump_parser-master
docker-compose.exe up
ls

```
