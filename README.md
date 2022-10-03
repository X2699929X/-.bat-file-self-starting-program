#创建一个bat文件用于自动杀掉和自动启动进程-

RestatClash.bat是用于自动重启Clash for Windows的一个脚本文件。
若要修改bat的代码，请将后缀bat改成txt，修改完成保存后再更改回bat运行。  没尝试过直接拖进IDE内进行修改

若需要嵌入到代码内，只需用代码相关的编程语言运行该文件，即可自动运行bat内的自动杀死clash.exe进程和重启clash.exe进程的操作
请注意：若路径的文件名中包含空格，则需将包含空格的文件夹使用""包含起来。
并且，在用代码打开该bat文件时，请注意是否有权限打开该文件所在的父级的文件夹，若无权限打开，则会导致文件打开失败。

注意要点应该就以上这几点

接下来对bat的代码进行说明：
1.`@echo off`    //准备关闭抓包程序
2.`echo "killing Clash for Windows...."`    
//在控制台输出:"killing Clash for Windows "  译：正在杀掉Clash for Windows进程
3.`taskkill /f /im "Clash for Windows.exe"`  
// taskkill 关闭执行  要关闭的应用程序(不知道叫什么可去任务管理器查看进程名称)  
// 若程序名中包含空格，则需使用""包含起来
4.`echo "Clash for Winodws Closed"`   //Clash for Winodws已关闭
5.若需要等待5秒进入下一步 代码则为：`@ping 127.0.0.1 -n 5 >nul`  bat程序中删除掉了该行代码...
6.`echo "Starting Clash for Windows..."`  
//控制台输出"Starting Clash for Windows.."  译：正在启动Clash for Windows进程
7.`start G:\"Clash for Windows"\"Clash for Windows.exe"`  
//启动G盘Clash for Winodws文件夹中的Clash for Winodws.exe文件，
//注：若文件夹名有空格 则需用""包含起来，若无，则不用，启动时注意是否有权限打开文件夹
//我是C盘的program文件无权限，所以把Clash拖了一份到G盘才成功运行。
//有无权限是说：运行代码时有无权限打开，而不是说你个人以双击鼠标的形式能不能点击进入文件夹
8.`echo "Plause waiting  5s"`   //控制台输出  Plause waiting  5s
9.`echo "Success!!"`   //控制台输出   成功
10.`exit /b`   //退出命令行，若需停留在命令行则将`exit /b`改为`pause`
注：有时会出现命令行关闭，命令行启动的clash也关闭的情况，不知道为什么会出现。知道解决方法时会更新该文档
