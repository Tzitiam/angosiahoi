# Sphinx 使用
## 1.使用pip install Sphinx 安装sphinx
## 2.创建项目 sphinx-quickstart
> Please enter values for the following settings (just press Enter to
accept a default value, if one is given in brackets).
 ​
 Selected root path: .
 ​
 You have two options for placing the build directory for Sphinx output.
 Either, you use a directory "_build" within the root path, or you separate
 "source" and "build" directories within the root path. </br>
  独立的源文件和构建目录（y/n） [n]: 
- 首先，询问你是否要创建独立的源文件和构建目录。一种是在根路径下创建“_build”目录，另一种是在根路径下创建“source”和“build”两个独立的目录，前者用于存放文档资源，后者用于保存构建生成的各种文件。根据个人喜好选择即可，比如我更倾向于独立目录，因此输入 y。
- 接着，需要输入项目名称、作者等信息。
> The project name will occur in several places in the built documentation.</br>
 项目名称: diary </br>
 作者名称: Rudy </br>
 项目发行版本 []: v1
 - 然后，可以设置项目的语言，我们这里选择简体中文。
 > For a list of supported codes, see
 https://www.sphinx-doc.org/en/master/usage/configuration.html#confval-language.
 > 项目语种 [en]: zh_CN
 ### ==============创建项目完成===============

 - Makefile：可以看作是一个包含指令的文件，在使用 make 命令时，可以使用这些指令来构建文档输出。
- build：生成的文件的输出目录。
- make.bat：Windows 用命令行。
- _static：静态文件目录，比如图片等。
- _templates：模板目录。
- conf.py：存放 Sphinx 的配置，包括在 - - sphinx-quickstart 时选中的那些值，可以自行定义其他的值。
- index.rst：文档项目起始文件。
## 3.生成静态前端命令 make html
- 查看效果 /build/html/index.html
- 当然，直接访问 html 文件不是很方便，所以我们借助 sphinx-autobuild 工具启动 HTTP 服务，这个工具也需要额外下载：
> pip install sphinx-autobuild

> sphinx-autobuild source build/html
- 默认启动 8000 端口，在浏览器输入 http://127.0.0.1:8000 。
## 4.修改主题
- 一般使用'sphinx_rtd_theme'主题会比较美观，用pip安装'sphinx_rtd_theme'主题
> pip install sphinx_rtd_theme
- 打开 conf.py 文件，找到 html_theme 字段，修改：
> #html_theme = 'alabaster'</br>
 html_theme = 'sphinx_rtd_theme'
 - Sphinx 为我们提供了好多可选的主题，在 https://sphinx-themes.org/ 都可以找到。
 ## 5. index.rst 的文件内容
- 第1-4行由 .. + 空格开头，属于多行评论（类似于**注释**），**不会显示到网页上**。
- 第6-7行是**标题**，reST 的标题需要被双下划线（或单下划线）包裹，**并且符号的长度不能小于文本的长度。**
- 第9-11行是**文档目录**树结构的描述，**.. toctree::** 声明了一个树状结构（toc 即 Table of Content），</br>**:maxdepth: 2** 表示目录的级数（页面最多显示两级），</br>**:caption: Contents:** 用于指定标题文本（可以暂时去掉）。
- 第15-20行是索引标题以及该标题下的三个索引和搜索链接。
## 6.添加模块
- 假设我要添加一个 **关于** 页面，需要修改 index.rst 文件，添加一个 about 页面。
> 我的日记</br>
=================================
> 
> </br>.. toctree::</br>
> &#160;&#160;:maxdepth: 2</br>
   &#160;&#160;:caption: Contents:
>
> </br> &#160;&#160;about
- 并且在 source 目录下新建一个 about.rst 文件，并写下内容：
>  关于</br>
 ========
 ></br> -（这里必须空一行​）
 ></br>这是我的公开日记
### =========可能需要重新 make html ==========