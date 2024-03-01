IDM 激活脚本
用于激活和重置 Internet Download Manager 试用版的开源工具

特征
IDM 冻结试用和使用注册表项锁定方法激活
即使在安装 IDM 更新后，激活和试用仍然存在
IDM 试用重置
完全开源
基于透明批处理脚本
IAS 最新版本
最新版本 - v1.2（2024 年 2 月 12 日）
GitHub - BitBucket

下载 / 如何使用它？
首先全新安装 Internet 下载管理器。确保删除/卸载以前的裂缝/补丁（如果有）。
之后，请按照以下步骤激活它。
注意
📌 激活选项当前在脚本中不起作用，请使用“冻结试用”选项锁定 30 天的试用期。
方法 1 - PowerShell
（推荐）

右键单击 Windows“开始”菜单，然后选择“PowerShell”或“终端（非 CMD）”。
复制粘贴以下代码并按回车键
irm https://massgrave.dev/ias | iex
您将看到激活选项，请按照屏幕上的说明进行操作。
就这样。
方法 2 - 传统
从 GitHub 或 Bitbucket 下载文件
右键单击下载的 zip 文件并解压
在提取的文件夹中，运行名为IAS.cmd
您将看到激活选项，并按照屏幕上的说明进行操作。
就这样。
信息
冻结试用
IDM 提供 30 天的试用期，您可以在脚本中使用此选项将此试用期锁定到终身，这样您就不必再次重置试用版，并且您的试用版不会过期。
此方法在应用此选项时需要 Internet。
IDM 更新可以直接安装，而无需再次冻结。
激活
（*目前不工作）

此脚本应用注册表锁定方法来激活 Internet 下载管理器 （IDM）。
此方法在激活时需要 Internet。
IDM 更新可以直接安装，而无需再次激活。
激活后，如果在某些情况下，IDM 开始显示激活唠叨屏幕，则只需再次运行激活选项而不使用重置选项。
重置 IDM 激活/试用
Internet 下载管理器提供 30 天的试用期，您可以随时使用此脚本重置此激活/试用期。
如果 IDM 报告伪造的序列号和其他类似错误，此选项也可用于恢复状态。
操作系统要求
Windows 7/8/8.1/10/11 及其服务器等效版本支持该项目。
Windows 8 及更高版本支持用于运行 IAS 的 PowerShell 方法。
高级信息
若要在无人参与模式下激活，请使用参数运行脚本。/act
若要在无人参与模式下冻结试用版，请使用参数运行脚本。/frz
若要在无人参与模式下重置，请使用参数运行脚本。/res
它是如何工作的？
IDM 跨各种注册表项存储与试用和激活相关的数据。其中一些密钥被锁定以保护它们不被篡改，并且数据以模式存储，以跟踪伪造的序列号问题和剩余的试用天数。若要激活它，此处的脚本只需通过在 IDM 中触发一些下载来生成这些注册表项，识别这些注册表项，并锁定它们，以便 IDM 无法编辑和查看它们。这样，IDM 就无法显示使用假序列号激活的警告。
Troubleshoot
Browser Integration Fix: Chrome - Firefox
Raise the issue on Github with screenshots.
Changelog
v1.2
Added back activation option with a randomized name, email, and key in registration details along with a warning that it's not working for some users, the recommended option is to use Freeze trial.
v1.1
IDM update 6.42b3 has started showing fake serial popups with IAS activation, due to this we have removed the activation option and replaced it with the Freeze trial option to lock the 30-day trial period for the lifetime.
Now the script will disable quick-edit in CMD windows using Powershell instead of editing registry, thanks to @abbodi1406 for the code and @awuctl for the idea.
Code to relaunch script with conhost.exe to avoid terminal app is now merged in quick-edit disable code, thanks to @abbodi1406.
v1.0
Added the code to relaunch the script with conhost.exe if the script is running from the terminal app.
Fixed an issue in getting the current user account SID.
v0.9
Fixed an issue where the script can not activate and reset IDM in non-admin user accounts.
Fixed an issue where the script incorrectly shows that IDM is activated.
Fixed an issue where a fake serial pop-up may appear. The script will also show the info to run the activation option again without using the reset option.
Fixed an issue where Powershell code to launch IAS may not work due to GitHub block in some regions. It will use the new BitBucket repo as a fallback link.
IDM registry scanning and locking code is now written in Powershell.
The script update checker code is added to the script.
The script will now disable quick edit mode temporarily because users often click inside the script window and it pauses the script.
The script will back up the CLSISD registry keys before performing operations on them.
Many error checks are added to better identify the issues.
0.8 版
将项目移动到 Github 并 massgrave.dev
小错误修复
添加信息以通知用户，当脚本删除大量空注册表项时，将删除空注册表项
截图
