# 什么是`NotepadFree`的`WinGUp`？

该项目fork自 [WinGUp](https://github.com/gup4win/wingup).
WinGUp被用于Notepad++，该项目是NotepadFree项目的WinGUp程序。WinGUp 是为 Notepad++ 的需要而构建的，但保持其功能通用，以便能够在任何 Windows 应用程序上使用。使用 Notepad++ 中新的内置插件管理器，需要更具体的 Notepad++ 更新程序。因此，这个来自原始 WinGUp 的分支。

# 什么是`WinGUp`？

WinGup 是一个在 Windows 环境下运行的通用更新程序。WinGup 的目的是提供一个即用型和可配置的更新程序，它下载更新包然后安装它。通过使用 cURL 库和 TinyXml 模块，WinGup 能够处理 http 协议和处理 XML 数据。


# 为什么使用WinGUp？

最初 WinGup 是为了 Notepad++（MS Windows 下的通用源代码编辑器）的需要而制作的。在它的构思过程中，我的脑海中出现了一个想法：如果它可以适合 Notepad++，那么它可以适合任何 Windows 程序。因此，有了 LGPL 许可，在任何项目中的集成都没有（几乎没有）限制。


# 它如何工作？

WinGup 可以由您的程序或手动启动。它从 xml 配置文件中读取以获取程序的当前版本和 WinGup 获取更新信息的 url，检查 url（具有给定的当前版本）以获取更新包位置，下载更新包，然后运行更新包（它应该是有问题的 msi 或 exe）。

# 谁需要他？

作为 LGPLed，WinGup 可以集成到商业（或封闭源代码）和开源项目中。因此，如果您在 MS Windows 下运行商业或开源项目并定期发布程序，那么您可能需要 WinGup 来通知您的用户新的更新。

# 使用它需要什么？

一个用于向您的 WinGup 提供更新信息的 url 和一个用于存储更新包的另一个 url 位置，就是这样！

# 它有多简单？

您所要做的就是将 WinGup 指向您的 url 更新页面（通过修改 gup.xml），然后在您指定的 url 更新页面上工作（请参阅 `getDownLoadUrl.php` 随发行版提供）以确保它以正确的方式响应您的 WinGup xml 数据。

# 如何构建它

 * 第一步: You have to build cURL before building WinGup:

    1. 打开 VS2017 Native Tool Command for 32/64 bits. 如果想构建arm版本, 打开 cmd, 然后运行：<br/>
    `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvarsamd64_arm64.bat`
    2. 到curl的构建目录：<br/>
       `cd <your wingup source path>\curl\winbuild`
    3. 构建curl，通过以下命令：<br/>
       - x64 release: `nmake /f Makefile.vc mode=dll vc=15 RTLIBCFG=static MACHINE=x64`
       - x64 debug: `nmake /f Makefile.vc mode=dll vc=15 RTLIBCFG=static DEBUG=yes MACHINE=x64`
       - x86 release: `nmake /f Makefile.vc mode=dll vc=15 RTLIBCFG=static MACHINE=x86`
       - x86 debug: `nmake /f Makefile.vc mode=dll vc=15 RTLIBCFG=static DEBUG=yes MACHINE=x86`
       - ARM64 release: `nmake /f Makefile.vc mode=dll vc=15 RTLIBCFG=static MACHINE=ARM64`

 * 第二部: 在 VS2017 中打开[`vcproj\GUP.sln`](https://github.com/gup4win/wingup/blob/master/vcproj/GUP.sln).
 
 * 第三部: 像一个普通Visual Studio项目一样构建它。
