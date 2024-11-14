<div align="center">
<img src="https://github.com/user-attachments/assets/18a4286e-2a15-425c-bb7f-eb238d8fcdaf" alt="XRSOFT_LOGO_ROUND_1024" width="20%" />

# 软件狗狗 Scoop Dooge

[![GitHub Actions CI Status](https://img.shields.io/github/actions/workflow/status/xrgzs/sdoog/ci.yml?style=flat-square&logo=github&label=Tests)](https://github.com/xrgzs/sdoog/actions/workflows/ci.yml)
[![License](https://img.shields.io/github/license/xrgzs/sdoog.svg?style=flat-square)](https://github.com/xrgzs/sdoog/blob/master/LICENSE)
[![Target Windows 10](https://img.shields.io/badge/Target-Windows%2010-0067B8.svg?style=flat-square)](https://www.microsoft.com/en-us/windows)
[![Repo size](https://img.shields.io/github/repo-size/xrgzs/sdoog.svg?style=flat-square)](https://github.com/WuwuZiQWQ/March7th)

对现有仓库的补充，不求数量，只图好用

</div>

## 使用说明

### 添加本仓库：

```powershell
scoop bucket add sdoog https://github.com/xrgzs/sdoog.git
```

或者

```powershell
scoop bucket add sdoog https://gh.xrgzs.top/https://github.com/xrgzs/sdoog.git
```

### 还没安装 Scoop？

配套 Scoop 特供优化版（[仓库](https://github.com/xrgzs/scoop)），优化包括但不限于：

1. 添加 hook，自动判断并替换下载链接为国内源，无需仓库支持；基于 ISP 检测，加速策略更为精准
2. 执行 `scoop search` 时避免大量报错
3. 执行 `scoop update` 时不使用 `git pull` 拉取仓库，无需手动解决 commit 冲突
4. 安装脚本自动配置好 7zip、git、aria2 环境，并做好相关优化
5. 安装脚本支持管理员权限安装，自动修复 Scoop 文件 ACL 到当前用户

#### 默认安装

```powershell
irm c.xrgzs.top/c/scoop | iex
```

#### 增加指定软件

多个可用空格分隔

```powershell
iex "& { $(irm c.xrgzs.top/c/scoop) } -Append xrok"
```

#### 精简安装

仅安装主程序、git、aria2，添加 main 和 sdoog

```powershell
iex "& { $(irm c.xrgzs.top/c/scoop) } -Slim"
```

#### 设置安装路径

安装到 D 盘

```powershell
iex "& { $(irm c.xrgzs.top/c/scoop) } -ScoopDir 'D:\Scoop' -ScoopGlobalDir 'D:\ScoopGlobal'"
```

#### 切换到此版本

如果已经安装 Scoop，可以切换到此专用版本

```powershell
# scoop config scoop_repo "https://gh.xrgzs.top/https://gitee.com/xrgzs/scoop"
scoop config scoop_repo 'https://gitee.com/xrgzs/scoop'

scoop update
```

## 提交贡献

以下是几点提交贡献的小提示：

1. 不要重复添加以下仓库已有的配置文件，除非配置文件内容不同或有特殊优化：

    此仓库为潇然系统优化版 scoop（可通过上面的命令安装）打造，默认安装会添加以下仓库：

    | Name            | Source                                             |
    | --------------- | -------------------------------------------------- |
    | main            | https://github.com/ScoopInstaller/Main             |
    | extras          | https://github.com/ScoopInstaller/Extras           |
    | versions        | https://github.com/ScoopInstaller/Versions         |
    | nirsoft         | https://github.com/ScoopInstaller/Nirsoft          |
    | sysinternals    | https://github.com/niheaven/scoop-sysinternals     |
    | php             | https://github.com/ScoopInstaller/PHP              |
    | nerd-fonts      | https://github.com/matthewjberger/scoop-nerd-fonts |
    | nonportable     | https://github.com/ScoopInstaller/Nonportable      |
    | java            | https://github.com/ScoopInstaller/Java             |
    | games           | https://github.com/Calinou/scoop-games             |
    | **abgo_bucket** | https://github.com/abgox/abgo_bucket.git           |
    | **aki**         | https://github.com/akirco/aki-apps.git             |
    | **dorado**      | https://github.com/chawyehsu/dorado.git            |
    | **DoveBoy**     | https://github.com/DoveBoy/Apps.git                |
    | **scoop-zapps** | https://github.com/kkzzhizhou/scoop-zapps.git      |

2. 无需担心 GitHub 无法下载问题，优化版 Scoop 自带的 `Url Proxy` 功能能够自动处理

3. 尽量使用便携版软件，并 `persist` 程序数据，尽量纳入 scoop 原生管理

4. 不要使用绝对路径，请使用 scoop 提供的变量或 `$env:系统变量`

5. 安装时创建的文件，卸载的时候要删除

6. 如果有自动更新程序，最好干掉，如果是后台自动更新无法关闭那种，不要安装到 `scoop\apps` 目录下

7. 如果能加入优化配置文件，尽量加入，别人不做的我们做

8. 受限于 scoop 的机制，不适合用 scoop 安装的软件，可以 ~~祸害~~ 提交到其它仓库（甩锅+手动狗头.jpg）

9. 遵循 [Scoop Contributing Guide](https://github.com/ScoopInstaller/.github/blob/main/.github/CONTRIBUTING.md#for-scoop-buckets) 的规范提交 Pull Request，懒得看的话，需要注意以下几点：

    - 不要用 Master 分支提交 Pull Request
    - 一个 Manifest 一个 Branch 一个 Pull Request
    - 本仓库对 Pull Request、Commit 和 Branch 命名没有强制性要求，但要能看得出来改了什么

10. 提交 PR 前，请开一台电脑或虚拟机，要求**开启 UAC**，测试以下内容：

    - 能够正常安装

        ```powershell
        scoop install .\bucket\<name>.json
        ```

    - 能够正常使用

    - 能够正常持久化配置文件

    - 能够正常卸载

    - 能够正常执行 Autoupdate

        - 可以先破坏要更新的内容（尤其是 `version` 字段），然后本地执行检测操作，确保配置文件能用且为最新版本

        - 两种测试方法：

            1. VS Code 在 JSON 配置文件下按 <kbd>F5</kbd>

                - Only sdoog can do.

            2. 在项目根目录执行：

                ```powershell
                 .\bin\checkver.ps1 -App 软件名称 -Update
                ```

11. 提交 PR 时，清空默认的提交内容，加入你认为有用的信息（提交上一步测试的截图/输出）

12. 提交 PR 后，如果有更改，在 GitHub PR 页面发送评论 `/verify`，让机器人再次检测

希望此规范能够帮助到参与第三方 scoop 仓库的贡献者，提供一个轻松、高效的软件提交流程，如果不会搞的话可以发 issue。

## 编写技巧

本仓库一些关于编写配置的规范和技巧（不看会后悔）

### 配置定义

你想知道关于配置文件的定义项，这里都有，在编写配置文件时建议同时打开：

-   [App Manifests](https://github.com/ScoopInstaller/Scoop/wiki/App-Manifests)
    -   [Creating an App Manifest](https://github.com/ScoopInstaller/Scoop/wiki/Creating-an-app-manifest)
    -   [Autoupdate](https://github.com/ScoopInstaller/Scoop/wiki/App-Manifest-Autoupdate)
    -   [Persistent data](https://github.com/ScoopInstaller/Scoop/wiki/Persistent-data)
    -   [Pre and Post install and uninstall Scripts](<https://github.com/ScoopInstaller/Scoop/wiki/Pre-Post-(un)install-scripts>)

### 读取脚本

读取现有配置中的脚本块，避免人脑反转义

从配置文件中读取：

```powershell
PS D:\sdoog> (Get-Content .\bucket\qqnt.json | ConvertFrom-Json).installer.script

# Output:
$configpath = "$env:PUBLIC\Documents\Tencent\QQ"
if (!(Test-Path -Path "$configpath")) {
    New-Item -Path "$configpath" -Type Directory -Force -ErrorAction SilentlyContinue | Out-Null
}
if (!(Test-Path -Path "$configpath\UserDataInfo.ini" -PathType leaf)) {
    Set-Content -NoNewline -Path "$configpath\UserDataInfo.ini" -Value "[UserDataSet]`nUserDataSavePathType=2`nUserDataSavePath=`"$persist_dir\Tencent Files`""
}
```

从 `scoop cat` 中读取：

```powershell
PS D:\sdoog> (scoop cat python | ConvertFrom-Json).installer.script

# Output:
Expand-DarkArchive "$dir\setup.exe" "$dir\_tmp"
@('path.msi', 'pip.msi') | ForEach-Object {
    Remove-Item "$dir\_tmp\AttachedContainer\$_"
}
(Get-ChildItem "$dir\_tmp\AttachedContainer\*.msi").FullName | ForEach-Object {
    # appendpath.msi does not contain any file, which causes 'msiexec /a' to fail
    if($((Get-Item $_).Basename) -eq 'appendpath') { return }
    Expand-MsiArchive $_ "$dir"
}
Remove-Item "$dir\_tmp", "$dir\setup.exe" -Force -Recurse
if ($global) {
    $pathext = (Get-EnvVar -Name PATHEXT -Global) -replace ';.PYW?', ''
    Set-EnvVar -Name PATHEXT -Value "$pathext;.PY;.PYW" -Global
}
```

### 嵌入脚本

还在吐槽爬虫难写、人工转义费劲？

将 PowerShell 脚本块转换成 JSON Array 以便嵌入到配置中，自动转义相关符号，避免人工转义

所以你可以放心往脚本里面多写点东西，使此仓库具有独特性

```powershell
PS D:\sdoog> Get-Content .\Untitled-1.ps1

# Output:
if ($global) {
    $pathext = (Get-EnvVar -Name PATHEXT -Global) -replace ';.PYW?', ''
    Set-EnvVar -Name PATHEXT -Value "$pathext;.PY;.PYW" -Global
}

PS D:\sdoog> Get-Content .\Untitled-1.ps1 | ConvertTo-Json

# Output:
[
  "if ($global) {",
  "    $pathext = (Get-EnvVar -Name PATHEXT -Global) -replace ';.PYW?', ''",
  "    Set-EnvVar -Name PATHEXT -Value \"$pathext;.PY;.PYW\" -Global",
  "}"
]
```

### 蓝奏文件夹分享自动更新

参考 [pecmd-beta](bucket/pecmd-beta.json)

### WinGet 自动更新

我们提供了 WinGet PowerShell 模块，只需导入即可使用

manifestUrl 会在 DEBUG 中输出，建议开启 DUBUG，以便查看具体 YAML 配置

如果只要版本号，可以：

```json
"checkver": {
    "script": [
        "Import-Module \"$pwd\\bin\\WinGet.psm1\"",
        "$Manifest = Get-WinGetInfo -Id '<WinGetPackageID>'",
        "$Manifest.latest_version"
    ]
},
"autoupdate": {
    "url": "https://www.example.com/download/$version/$version"
}
```

如果要同时将版本号和 URL 同时匹配出来，可以：

```json
"checkver": {
    "script": [
        "Import-Module \"$pwd\\bin\\WinGet.psm1\"",
        "$Manifest = Get-WinGetManifest -Id '<WinGetPackageID>'",
        "$version  = $Manifest.PackageVersion",
        "$url      = $Manifest.Installers.InstallerUrl",
        "return \"$version=====$url\""
    ],
    "regex": "(.*)=====(?<url>.*)"
},
"autoupdate": {
    "url": "$matchUrl"
}
```

### 匹配转链

`Get-RedirectedUrl1st`：匹配 301 / 302 等带有 Location 头的转链

### 创建桌面快捷方式

啥？还要用外置脚本？直接从开始菜单复制一个不就行，卸载的时候记得删除

注意安装时机为 `post_install` ，`installer.script` 的时候还没创建开始菜单快捷方式

参考 [xrok](bucket/xrok.json)

### 持久化数据

官方文档仅适用于便携版软件（数据存程序同一目录），比较简单，这边需要进一步补充

https://github.com/ScoopInstaller/Scoop/wiki/Persistent-data

如果要持久化的数据非文件夹，如配置文件，需要在 `pre_install` 中创建对应需要持久化的文件，像这样：

```json
"persist":[
    "Settings.json"
],
"pre_install":[
    "if (!(Test-Path \"$dir\\Settings.json\") -or !(Get-Item \"$dir\\Settings.json\").Length) {",
    "    New-Item \"$dir\\Settings.json\" -ItemType File -Force -ErrorAction SilentlyContinue | Out-Null",
    "    Set-Content -Path \"$dir\\Settings.json\" -Value '{\"UpdateMode\":0}'",
    "}"
]
```

如果要持久化的数据与程序不在同一目录，如 `$env:APPDATA` / `$env:LOCALAPPDATA` 等，这种情况 scoop 不支持处理，我们需要设定一个标准手动解决

笔记：

> 正常 `persist` 定义的持久化数据在执行 `scoop uninstall <name>` 时不会删除，需要使用 `scoop uninstall <name> -p` 命令
>
> 目前 `scoop uninstall <name> -p` 可以删除手动创建的持久化数据
>
> 某仓库会在 `uninstall` 字段删除持久化数据，这边我们遵循 scoop 的设计规范，不学那样搞，因为 scoop 没有 `reinstall` 命令，你只能卸了重装
>
> PowerShell 的 `Remove-Item` cmdlet 无法删除 junction，需要使用 .NET [`System.IO.Directory` 的 `Delete` 方法](https://learn.microsoft.com/zh-cn/dotnet/api/system.io.directory.delete)

在 `installer.script` 中添加迁移配置和创建 Junction 的代码

```powershell
. "$bucketsdir\$bucket\bin\utils.ps1"
New-PersistDirectory "$env:APPDATA\Seewo\EasiNote5" "$persist_dir\Data" -Migrate
```

```mermaid
flowchart TD
    A[开始] --> B{数据目录存在？}
    B -->|否| E[结束]
    B -->|是| C{数据目录是符号链接？}
    C -->|是| D[删除旧符号链接]
    C -->|否| F[迁移数据]
    F --> G[删除原数据目录]
    D --> H[创建新符号链接]
    G --> H[创建新符号链接]
    H --> E[结束]
```

在 `uninstaller.script` 中添加删除 Junction 的代码，不处理 `$persist_dir`

```powershell
$bucket = $install.bucket
. "$bucketsdir\$bucket\bin\utils.ps1"
Remove-Junction "$env:APPDATA\Seewo\EasiNote5"
```

参考 [easinote](bucket/easinote.json)

这些命令需要外置脚本，所有请务必在仓库内测试

### 关闭目录下的所有程序

`Stop-App`：关闭安装目录下所有正在运行的程序，可加第一个参数传入需要关闭的其它目录，使用此函数无需指定程序名称

建议在 `pre_uninstall`、`uninstaller.script` （无法避免 scoop 检测正在运行）中调用

```powershell
$bucket = $install.bucket
. "$bucketsdir\$bucket\bin\utils.ps1"
Stop-App
```

目前暂不支持提权关闭

### 安装 UWP 应用

开启开发者模式，然后使用 `Add-AppxPackage -Register <AppxManifestPath>` 即可

无需担心 MS Store 会自动升级

可能不支持 persist，需要自行测试

参考 [snap.hutao](bucket/snap.hutao.json)

_未完待续……_


## 免责声明

访问本仓库或传播、查看、使用本仓库资源即视为同意且遵守本仓库的免责声明。

本仓库仅提供软件下载链接，并不提供任何软件及安装包。相关软件搜集自互联网，用户在使用前请自行评估风险，后果自担，我们不承担任何责任。

本仓库为非盈利性开源仓库，所有资源都来自互联网，所发布的一切资源及软件分析文章教程仅限用于学习、交流和研究目的，所有资源不代表本站立场。

本仓库并不贩卖软件，且不修改软件，不存在任何商业目的及用途，如果您访问和下载此仓库内的软件，表示您同意只将此文件或者技术教程用于参考、学习而非其他用途，请使用者和传播者遵循相关法律法规。

本仓库所有资源不得用于任何商业用途和非法用途。版权归原公司所有！如果您希望长期使用，请向作者购买正版版权，假如因用户未购买正版版权而导致版权纠纷，本站概不负责。如果无意侵犯了您的版权，请联系我们及时标明版权或是删除（提供相关版权证明）。

本仓库对任何资源不提供任何技术支持，遇到问题请自行研究或购买正版。

本仓库仅提供一个展示、交流的平台，不对其内容的准确性、真实性、正当性、合法性负责，也不承担任何法律责任。

任何人因使用本仓库而可能遭致的意外及其造成的损失（包括通过使用本站的资源而感染电脑病毒或查看本站技术文章并操作造成的经济损失），我们对此概不负责，亦不承担任何法律责任。

本仓库对发布的资源不能完全保证其完整性和安全性，请在下载后自行检查。在使用过程中出现的任何问题均与本仓库无关，请自行处理！部分资源有时效性，不保证发布的资源在任何时间绝对可用。

本仓库遵守国家法律法规，禁止制作、复制、发布、传播等具有反动、色情、暴力、淫秽，政治等内容的信息，一经发现，立即删除。

本仓库的传播者、使用者的一切意向、言行、用途和由此造成的任何结果，由该传播者和使用者自行负责，我们对此不承担任何法律责任。

本仓库在法律允许最大范围内对本声明拥有解释权与修改权。

如果本仓库有敏感资源或不合适的内容将积极配合有关执法部门检查及整改。

对免责声明的解释、修改及更新权均属于 @xrgzs 所有。
