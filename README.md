<body>
    <div align="left">
        <h1 align="left">onetab</h1>
        <p>
            <a>
                <img
                    src="https://ci.appveyor.com/api/projects/status/3k5hn9361lyf5r6a?svg=true"
                />
            </a>
        </p>
    </div>
    <p></p>
    <div>
        <p>
            一个用于 Windows 最佳命令行软件管理器<a
                href="https://github.com/lukesampson/scoop"
                >Scoop</a
            >的脚本仓库：持续助力科研
        </p>
        <p align="left">
            <a href="README_CN.md">简体中文</a>
        </p>
    </div>
</body>

对于熟悉 Scoop 的用户：

```powershell
scoop bucket add onetab https://github.com/wholegale39/onetab
```

# :running: 开始

## :bike: 安装 Scoop

### :computer: 步骤 1：在 PowerShell 中打开远程权限

```powershell
Set-ExecutionPolicy RemoteSigned -scope CurrentUser
```

### :gear: 步骤 2：自定义 Scoop 安装目录

```powershell
$env:SCOOP='Your_Scoop_Path'
[Environment]::SetEnvironmentVariable('SCOOP', $env:SCOOP, 'User')
```

> 如果跳过该步骤， Scoop 将默认把所有用户安装的 App 和 Scoop 本身置于`c:/users/user_name/scoop`

### :hammer: 步骤 3：下载并安装 Scoop

```powershell
Invoke-Expression (New-Object System.Net.WebClient).DownloadString('https://get.scoop.sh')
```

### :book: 步骤 4：通过`scoop help`查看快速上手方法

更多信息，请访问 Scoop 官网 👉 https://scoop.sh/ 👈

## :car: 利用扩展库安装 App

### :train: 步骤 1：安装 Aria2 来加速下载

```powershell
scoop install aria2
```

如果使用 VPN，需要通过如下命令关闭 aria2

```powershell
scoop config aria2-enabled false
```

### :ticket: 步骤 2：安装 Git 来添加新仓库

```powershell
scoop install git
```

### :airplane: 步骤 3：添加本仓库并更新，么么哒~ :kiss:

```powershell
scoop bucket add onetab https://github.com/wholegale39/onetab
scoop update
```

### :rocket: 步骤 4：安装 App

- 使用 `scoop search` 命令搜索 App 的具体名称

```powershell
scoop search <app_name>
```

- 利用插件`scoop-completion`协助安装

```powershell
scoop install scoop-completion
scoop install <app_name>
```

> 使用`scoop-completion`：键入 App 名称的前几个字母后敲击`tab`键进行补全

### :100: 步骤 5：查看官方推荐仓库

```powershell
scoop bucket known

main [默认]
extras [墙裂推荐]
versions
nightlies
nirsoft
php
nerd-fonts
nonportable
java
games
jetbrains
```

## :m: 其他

### Aria2 的参数自定义

```powershell
# aria2 在 Scoop 中默认开启
scoop config aria2-enabled true
# 关于以下参数的作用，详见aria2的相关资料
scoop config aria2-retry-wait 4
scoop config aria2-split 16
scoop config aria2-max-connection-per-server 16
scoop config aria2-min-split-size 4M
```

## :star: 总结

### 科研工具

|          App          | 自动更新 | 原创                                                             |
| :-------------------: | :------: | ---------------------------------------------------------------- |
|    CopyTranslator     |    √     | √                                                                |
|   GeoGebra-Portable   |    √     | √                                                                |
|         Gephi         |    √     | √                                                                |
|       Julia-cn        |    √     | √                                                                |
|       KingDraw        |    √     | √                                                                |
|        LogSeq         |    √     | √ 已迁移至 [Extras](https://github.com/lukesampson/scoop-extras) |
|        LyX-cn         |    √     | √                                                                |
| Mathpix Snipping Tool |    √     | √                                                                |
|   Mendeley Desktop    |    √     | √                                                                |
|     Miniconda-cn      |    √     | √                                                                |
|        NetLogo        |    √     | √                                                                |
|      SageMath-cn      |    √     | √                                                                |
|        TeXLive        |    √     | 拷贝自 [dorado](https://github.com/chawyehsu/dorado)             |
|       思源笔记        |    √     | 拷贝自 [dorado](https://github.com/chawyehsu/dorado)             |
|         语雀          |    √     | 拷贝自 [dorado](https://github.com/chawyehsu/dorado)             |

### 开发辅助

|          App           | 自动更新 | 原创                                                                |
| :--------------------: | :------: | ------------------------------------------------------------------- |
|       Cyberduck        |    √     | √ 已迁移至 [Extras](https://github.com/lukesampson/scoop-extras)    |
|    scoop-completion    |    √     | 拷贝自 [Moeologist](https://github.com/Moeologist/scoop-completion) |
|         uTools         |    √     | 拷贝自 [dorado](https://github.com/chawyehsu/dorado)                |
| VirtualBox [含扩展包]  |    √     | 拷贝自 [Ash258](https://github.com/Ash258/Scoop-Ash258)             |
| VMware Workstation Pro |    √     | 拷贝自 [Ash258](https://github.com/Ash258/Scoop-Ash258)             |
|         WinGet         |    √     | 拷贝自 [Ash258](https://github.com/Ash258/Scoop-Ash258)             |
|      傲梅分区助手      |    √     | √                                                                   |

### 日常办公

|       App        | 自动更新 | 原创                                                 |
| :--------------: | :------: | ---------------------------------------------------- |
|  File Converter  |    √     | √                                                    |
|  OBS Studio-cn   |    √     | √                                                    |
| Office Tool Plus |    √     | √                                                    |
|     RustDesk     |    √     | √                                                    |
|   小狼毫输入法   |    √     | √                                                    |
|  Wise Care 365   |    √     | √                                                    |
|    WPSOffice     |    ×     | 拷贝自 [dorado](https://github.com/chawyehsu/dorado) |
|     百度网盘     |    √     | √                                                    |
|     腾讯会议     |    ×     | 拷贝自 [sushi](https://github.com/kidonng/sushi/)    |

### 社交休闲

|     App      | 自动更新 | 原创                                                 |
| :----------: | :------: | ---------------------------------------------------- |
|     钉钉     |    √     | √                                                    |
| 洛雪音乐助手 |    √     | √                                                    |
|  网易云音乐  |    √     | 拷贝自 [dorado](https://github.com/chawyehsu/dorado) |
|     微信     |    √     | 拷贝自 [dorado](https://github.com/chawyehsu/dorado) |
|   magnetW    |    √     | √                                                    |
|   You-Get    |    √     | √                                                    |
