## SUNFLOWER论文

### 文件内容

**SUNFLOWER.tex**	- 使用Latex编写的文件；

**SUNFLOWER.bib**	- 引用文献的内容；

**ieeeconf.cls**		- IEEE模板；

**其他**			- 编译的中间文件；

### 配置Sublime Text 3使用Latex（参考）

#### 准备工作

下载并安装MikTeX：<https://miktex.org/download>

下载并安装SumatraPDF：<https://www.sumatrapdfreader.org/downloadafter.html>

*[NOTE] SumatraPDF建议下载32-bit。*

Sublime Text 3 安装好Package Install（自行百度），安装好后搜索LaTeXTools并安装。

#### 修改LaTeXTools配置文件

修改配置文件LaTeXTools.sublime-settings。

*[NOTE] 建议使用Everything搜索文件位置，我的位置在`C:\Users\Keith Lin\AppData\Roaming\Sublime Text 3\Packages\User\LaTeXTools.sublime-settings`。*

*[NOTE] 该配置文件有两个，除了上述位置外，还有可能在`C:\Users\Keith Lin\AppData\Roaming\Sublime Text 3\Packages\LaTeXTools\LaTeXTools.sublime-settings`，不知道两个文件的差别，建议两个都进行修改。*

搜索`"texpath"`,找到`"windows"`下的设置，如下：

```sett
"windows": {
	// ...
	"texpath" : "",
	// TeX distro: "miktex" or "texlive"
	"distro" : "miktex",
	// Command to invoke Sumatra. If blank, "SumatraPDF.exe" is used (it has to be on your PATH)
	"sumatra": "",
	// ...
```
*[NOTE]不要设置成`"osx"`下的`"texpath"`*。

修改第5行代码`"texpath" : "",`成miktex的安装地址下`mitex\bin\x64`文件夹加上`$PATH`，比如`"texpath" : "D:\\Software\\miktex\\miktex\\miktex\\bin\\x64;$PATH",`

修改后代码如下：

```
"windows": {
		// ...
		"texpath" : "D:\\Software\\miktex\\miktex\\miktex\\bin\\x64;$PATH",
		// TeX distro: "miktex" or "texlive"
		"distro" : "miktex",
		// Command to invoke Sumatra. If blank, "SumatraPDF.exe" is used (it has to be on your PATH)
		"sumatra": "",
		// ...
```

#### 修改环境变量

在用户环境变量中添加SumatraPDF的安装地址。

#### 配置逆向搜索

*[NOTE] 配置了这一部分才能在生成的pdf中反向搜索源代码的位置。*

在命令行中运行：`SumatraPDF.exe -inverse-search "\"C:\Program Files\Sublime Text 3\sublime_text.exe\" \"%f:%l\""`

其中的目录是sublime_text.exe的位置，可以使用everything查找，其位于sublime的安装位置。

#### 检验是否配置成功

使用Sublime打开SUNFLOWER.tex，按`Ctrl+B`，出现框框选择，选择`PdfLaTeX`（第一次会出现，后面不出现）。

如果配置成功，会跳出SumatraPDF，界面正常显示，且双击pdf内容会跳到Sublime源代码处。

*[NOTE] 在`Ctrl+B`前，确认`Tools -> Build System`选择的是`LaTeX`。*