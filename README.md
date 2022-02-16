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
            >的脚本仓库：测试工程师专属软件桶
        </p>
        <p align="left">
            <a href="README.md">简体中文</a>
        </p>
    </div>
</body>

对于熟悉 Scoop 的用户：

```powershell
scoop bucket add onetab https://github.com/wholegale39/onetab
```



## 安装 Scoop

> 1、Windows 7 SP1+ / Windows Server 2008+
>
> 2、确保安装Powershell 3(或更高版本)
>
> 3、.NET Framework 4.5+(或更高版本)
>
> 4、必须为您的用户帐户启用PowerShell，并将执行策略设置为远程签名




- 打开PowerShell执行以下命令确认Powershell版本

```powershell
PS C:\Users\wch> $psversiontable.psversion.major
5

PS C:\Users\wch> $host


Name             : ConsoleHost
Version          : 5.1.19041.1320
InstanceId       : af599a82-f08b-4a1b-8039-ad57c9edd4f2
UI               : System.Management.Automation.Internal.Host.InternalHostUserInterface
CurrentCulture   : zh-CN
CurrentUICulture : zh-CN
PrivateData      : Microsoft.PowerShell.ConsoleHost+ConsoleColorProxy
DebuggerEnabled  : True
IsRunspacePushed : False
Runspace         : System.Management.Automation.Runspaces.LocalRunspace
```

> 安装Powershell新版本
>
> https://docs.microsoft.com/zh-cn/powershell/scripting/windows-powershell/install/installing-windows-powershell?view=powershell-5.1



![Win7升级Powershell 5.1](https://gitee.com/wholegale39/pictures_markdown/raw/master/20211208140312.png)

![下载Powershell 5.1](https://gitee.com/wholegale39/pictures_markdown/raw/master/20211208141211.png)

![下载Powershell 5.1对应版本](https://gitee.com/wholegale39/pictures_markdown/raw/master/20211208141257.png)

![安装Powershell 5.1](https://gitee.com/wholegale39/pictures_markdown/raw/master/20211208141345.png)

- 注意上述Powershell版本安装成功后需要重启计算机

- 打开Powershell执行以下命令确认.NET Framework版本

```powershell
PS C:\Users\wch> (Get-ItemProperty 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Client' -Name Version).Version
4.8.04084
```

> 安装.NET Framework新版本
>
> https://www.microsoft.com/zh-CN/download/details.aspx?id=30653


- PowerShell执行以下命令，选择A，回车确认

```powershell
PS C:\Users\wch> Set-ExecutionPolicy RemoteSigned -scope CurrentUser
```


- PowerShell执行以下命令

```powershell
PS C:\Users\wch> iex (new-object net.webclient).downloadstring('https://get.scoop.sh')
```

> 执行过程中可能会因为网络问题导致失败，可先科学上网


- 等待安装成功，默认为`C:\Users\wch\scoop`目录

![scoop](https://gitee.com/wholegale39/pictures_markdown/raw/master/20211027165521.png)


- 如果下载scoop的过程中断，那么必须先删除`C:\Users\wch\scoop`文件夹，再执行以上命令安装。
- 也可以自定义安装目录`D:\Applications\Scoop`

```powershell
[environment]::setEnvironmentVariable('SCOOP', 'D:\Applications\Scoop', 'User')
$env:SCOOP='D:\Applications\Scoop' # with this we don't need to close and reopen the console
iex (new-object net.webclient).downloadstring('https://get.scoop.sh')
```

- 或者自定义全局安装目录

```powershell
[environment]::setEnvironmentVariable('SCOOP_GLOBAL','F:\GlobalScoopApps','Machine')
$env:SCOOP_GLOBAL='F:\GlobalScoopApps'
```

> 自定义全局安装目录需要管理员权限


- 接下来就可以愉快的安装你想用的各种软件

```powershell
scoop install maven openjdk gradle
```

- 安装软件指定版本

```powershell
scoop install nodejs@13.14.0
```


- 上述软件安装成功后会自动配置环境变量
- 查看状态信息，在此之前未执行过update操作会自动触发update操作，执行完毕后提示待更新版本

```powershell
PS C:\Users\wch> scoop status

PS C:\Users\wch> scoop status
Scoop is up to date.
Updates are available for:
    sublime-text: 4-4113 -> 4-4121
    typora: 0.11.8 -> 0.11.13
Everything is ok!
```


- 也可手动触发更新scoop及本地软件仓库

```powershell
PS C:\Users\wch> scoop update
Updating 'main' bucket...
 * df9e83391 1password-cli: Update to version 1.12.3                     66 minutes ago
 * 6da9a1924 packer: Update to version 1.7.8                             4 hours ago
 * a948e4817 edgedriver: Update to version 97.0.1058.0                   4 hours ago
Scoop was updated successfully!
```

- 更新指定软件

```powershell
PS C:\Users\wch> scoop update maven
```

- 更新所有软件

```powershell
PS C:\Users\wch> scoop update *
```


- 更新版本后会遗留安装包，查询下载缓存

```powershell
PS C:\Users\wch> scoop cache
```

- 删除遗留安装包

```powershell
PS C:\Users\wch> scoop cache rm *
```


- 清除所有软件旧版本

```powershell
PS C:\Users\wch> scoop cleanup *
```


- 卸载软件

```powershell
PS C:\Users\wch> scoop uninstall maven
```


- 一次性卸载多个软件

```powershell
PS C:\Users\wch> scoop uninstall maven gradle ant xxx
```


- 卸载并清理软件数据

```powershell
PS C:\Users\wch> scoop uninstall -p maven
```


- 切换软件版本

```powershell
PS C:\Users\wch> scoop reset python27
Resetting python27 (2.7.18).
Linking ~\scoop\apps\python27\current => ~\scoop\apps\python27\2.7.18
Creating shim for 'python'.
Creating shim for 'pythonw'.
Creating shim for 'python2'.
Creating shim for 'idle'.
WARN  Overwriting shim to idle.bat installed from python
Creating shim for 'idle2'.
PS C:\Users\wch> 
```

- 另外OracleJDK8、openjdk11也可随意切换


- 查看官方维护的软件库

```powershell
PS C:\Users\wch> scoop bucket known
main
extras
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


- 为scoop添加额外bucket，欢迎star

```powershell
scoop bucket add onetab https://github.com/wholegale39/onetab
```

- 查看命令使用方法

```powershell
PS C:\Users\wch> scoop help uninstall
```

## 利用扩展库安装 App

- Aria2是一款开源下载工具，可帮助简化不同设备和服务器之间的下载过程。它支持磁力链接、BT种子、http等类型的文件下载，与迅雷及QQ旋风相比，Aria2有着优秀的性能及较低的资源占用,架构本身非常轻巧，通常只需要4兆字节（HTTP下载）到9兆字节（用于BitTorrent交互）之间。最重要的一点是Aria2完全免费！

```powershell
PS C:\Users\wch> scoop install aria2
WARN  'aria2' (1.36.0-1) is already installed.
Use 'scoop update aria2' to install a new version.
PS C:\Users\wch>  

# 默认为5
PS C:\Users\wch> scoop config aria2-max-connection-per-server 10

# 默认为5
PS C:\Users\wch> scoop config aria2-split 10

# 其他参数均默认
```

You can tweak the following `aria2` settings with the `scoop config` command:

- aria2-enabled (default: true)
- aria2-warning-enabled (default: true)
- [aria2-retry-wait](https://aria2.github.io/manual/en/html/aria2c.html#cmdoption-retry-wait) (default: 2)
- [aria2-split](https://aria2.github.io/manual/en/html/aria2c.html#cmdoption-s) (default: 5)
- [aria2-max-connection-per-server](https://aria2.github.io/manual/en/html/aria2c.html#cmdoption-x) (default: 5)
- [aria2-min-split-size](https://aria2.github.io/manual/en/html/aria2c.html#cmdoption-k) (default: 5M)

```powershell
PS C:\Users\wch> scoop install extras/everything
WARN  Scoop uses 'aria2c' for multi-connection downloads.
WARN  Should it cause issues, run 'scoop config aria2-enabled false' to disable it.
WARN  To disable this warning, run 'scoop config aria2-warning-enabled false'.
Installing 'everything' (1.4.1.1009) [64bit]
Starting download with aria2 ...
```

- 设置代理

```powershell
# 设置代理
PS C:\Users\wch> scoop config proxy 127.0.0.1:19180

# 查看代理
PS C:\Users\wch> scoop config proxy
127.0.0.1:19180

# 删除代理，删除后如果未生效，则打开新的Powershell窗口
PS C:\Users\wch> scoop config rm proxy
'proxy' has been removed
```

