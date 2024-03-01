# IDM 激活脚本

用于激活和重置 Internet Download Manager 试用版的开源工具 [Internet Download Manager](https://www.internetdownloadmanager.com/)

## Features

-   IDM 冻结试用和使用注册表项锁定方法激活
-   即使在安装 IDM 更新后，激活和试用仍然存在
-   IDM 试用重置
-   完全开源
-   基于透明批处理脚本

## IAS 最新版本

Last Release - v1.2 (12-Feb-2024)\
[GitHub](https://github.com/WindowsAddict/IDM-Activation-Script) - [BitBucket](https://bitbucket.org/WindowsAddict/idm-activation-script/)

## Download / 如何使用它？

-   首先全新安装 Internet 下载管理器。确保删除/卸载以前的裂缝/补丁（如果有）。
-   之后，请按照以下步骤激活它。

## 注意

-   📌 📌 激活选项当前在脚本中不起作用，请使用“冻结试用”选项锁定 30 天的试用期。

### 方法 1 - PowerShell


-  （推荐）

-  右键单击 Windows“开始”菜单，然后选择“PowerShell”或“终端（非 CMD）”。
-  复制粘贴以下代码并按回车键
-  irm https://massgrave.dev/ias | iex
-  您将看到激活选项，请按照屏幕上的说明进行操作。
-  就这样。

### 方法 2 - 传统

-   Download the file from [GitHub](https://github.com/WindowsAddict/IDM-Activation-Script/archive/refs/heads/main.zip) 或 [Bitbucket](https://bitbucket.org/WindowsAddict/idm-activation-script/get/main.zip)
-   右键单击下载的 zip 文件并解压
-   在提取的文件夹中，运行名为IAS.cmd
-   您将看到激活选项，并按照屏幕上的说明进行操作。
-   就这样。

## 信息

#### 冻结试用

-   IDM provides a 30-day trial period, you can use this option in the script to lock this trial period for the lifetime so that you won't have to reset the trial again and your trial won't expire.
-   This method requires the Internet at the time of applying this option.
-   IDM updates can be installed directly without having to freeze it again.

#### Activation

(\*Currently not working)

-   This script applies the registry lock method to activate the Internet download manager (IDM).
-   This method requires the Internet at the time of activation.
-   IDM updates can be installed directly without having to activate it again.
-   After the activation, if in some cases, IDM starts to show an activation nag screen, then just run the activation option again without using the reset option.

#### Reset IDM Activation / Trial

-   Internet download manager provides a 30-day trial period, you can use this script to reset this Activation / Trial period whenever you want.
-   This option also can be used to restore status if in case IDM reports a fake serial key and other similar errors.

#### OS requirement

-   The project is supported for Windows 7/8/8.1/10/11 and their Server equivalent.
-   The PowerShell method to run IAS is supported on Windows 8 and higher.

#### Advanced Info

-   To activate in unattended mode, run the script with the `/act` parameter.
-   To freeze the trial in unattended mode, run the script with the `/frz` parameter.
-   To reset in unattended mode, run the script with the `/res` parameter.

## How does it work?

-   IDM stores the data related to trial and activation across various registry keys. Some of these keys are locked to protect them from tampering and data is stored in a pattern to track the fake serial issue and the remaining trial days. To activate it, the script here simply generates those registry keys by triggering a few downloads in IDM, identifies those registry keys, and locks them so IDM can't edit and view them. That way IDM cannot show the warning that it's activated with a fake serial key.

## Troubleshoot

-   Browser Integration Fix: [Chrome](https://www.internetdownloadmanager.com/register/new_faq/bi9.html) - [Firefox](https://www.internetdownloadmanager.com/register/new_faq/bi4.html)
-   Raise the issue on [Github](https://github.com/WindowsAddict/IDM-Activation-Script) with screenshots.

## Changelog

#### v1.2

-   Added back activation option with a randomized name, email, and key in registration details along with a warning that it's not working for some users, the recommended option is to use Freeze trial.

#### v1.1

-   IDM update 6.42b3 has started showing fake serial popups with IAS activation, due to this we have removed the activation option and replaced it with the Freeze trial option to lock the 30-day trial period for the lifetime.
-   Now the script will disable quick-edit in CMD windows using Powershell instead of editing registry, thanks to @abbodi1406 for the code and @awuctl for the idea.
-   Code to relaunch script with conhost.exe to avoid terminal app is now merged in quick-edit disable code, thanks to @abbodi1406.

#### v1.0

-   Added the code to relaunch the script with conhost.exe if the script is running from the terminal app.
-   Fixed an issue in getting the current user account SID.

#### v0.9

-   Fixed an issue where the script can not activate and reset IDM in non-admin user accounts.
-   Fixed an issue where the script incorrectly shows that IDM is activated.
-   Fixed an issue where a fake serial pop-up may appear. The script will also show the info to run the activation option again without using the reset option.
-   Fixed an issue where Powershell code to launch IAS may not work due to GitHub block in some regions. It will use the new [BitBucket](https://bitbucket.org/WindowsAddict/idm-activation-script/) repo as a fallback link.
-   IDM registry scanning and locking code is now written in Powershell.
-   The script update checker code is added to the script.
-   The script will now disable quick edit mode temporarily because users often click inside the script window and it pauses the script.
-   The script will back up the CLSISD registry keys before performing operations on them.
-   Many error checks are added to better identify the issues.

#### v0.8

-   Move the project to [Github](https://github.com/WindowsAddict/IDM-Activation-Script) and [massgrave.dev](https://massgrave.dev/idm-activation-script.html)
-   Minor bug fixes
-   Add info to inform users that empty registry keys are being deleted when the script deletes a lot of them

## Screenshots

![](https://massgrave.dev/images/IAS.png?raw=true)

![](https://massgrave.dev/images/IAS_Freeze_Trial.png?raw=true)

## Credits

|                                             |                                                                                                                                                                                                                                        |
|-------------------|-----------------------------------------------------|
| Dukun Cabul                                 | Original researcher of this IDM trial reset and activation logic, made an Autoit tool for these methods, [IDM-AIO_2020_Final](https://nsaneforums.com/topic/371047-discussion-internet-download-manager-fixes/page/8/#comment-1632062) |
| AveYo aka BAU                               | [reg_own lean and mean snippet](https://pastebin.com/XTPt0JSC)                                                                                                                                                                         |
| [abbodi1406](https://github.com/abbodi1406) | Help in coding                                                                                                                                                                                                                         |
| WindowsAddict                               | IAS Author                                                                                                                                                                                                                             |

And thanks to the IAS users for their interest, feedback, and assistance.

------------------------------------------------------------------------

Made with Love ❤️
