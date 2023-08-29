# tju_MasterDr_Latex_template

Tianjin University thesis latex template for personal use. Based on 2021 revised version.

基于硕博学位模板，基于《天津大学关于博士、硕士学位论文统一规定（2021年修订）》。

使用前请**自行搜索安装 texlive**

如果使用`vscode`作为编辑器，克隆本仓库后打开文件夹工作区即用，编译链已经集成至`.vscode`文件夹内。

![image](https://github.com/nathanatgit/tju_MasterDr_Latex_template/assets/20399271/b246a822-fb78-4ff8-8aee-13fd3a5b5a88)


## 环境：
* Windows
* VSCode
* VSCode 扩展 - Latex Workshop
* texlive 2022

## 编译工具：
`xelatex + bibtex`或 `xelatex + biber + xelatex * 2`（视参考文献及参考文献风格的使用方式而定，一般前者可满足，如果对参考文献风格和引擎做了调整，编译不成功试试第二种）
已经将编译工具链集成至 vscode 工作区设定，保存在`.vscode/settings.json`中。

**改完设置完一定记得编译的时候选对候选编译工具**

## 文档列表

```
📑main.tex  ................. 主文档
 ├─ 📃 packages.tex ......... 文档中使用的包文件
 ├─ 📃 styCtrl.tex .......... 风格化设定，包括章节、图、表、公式、页眉、页脚等的风格定义
 └─ 📂 preface .............. 封面等
  ├─  📃 cover_Ph.D.tex ..... 学术博士封面（按需在 main.tex 中修改 \input{preface/cover_xxx.tex}）
  ├─  📃 cover_proD.tex ..... 专业博士封面
  ├─  📃 cover_acaMa.tex .... 学术硕士封面
  ├─  📃 cover_proMa.tex .... 专业硕士封面
  ├─  📃 abstract_cn.tex .... 中文摘要
  ├─  📃 abstract_en.tex .... 英文摘要
  └─  📃 noveltyDeclar.tex .. 独创性声明和版权页
 └─ 📂 chapters ............. 封面等
  ├─  📃 chpt1.tex .......... 参考 main.tex 按需添加章节
  .......
 ├─ 📂 figures .............. 默认图片文件夹，放入此文件夹内的图片 \includegraphics[参数控制]{文件名} 即可，不需要额外添加路径
 └─ 📂 postface ............. 所取得成果等
  ├─  📃 achievements.tex ... 发表论文和参加科研情况说明
  └─  📃 acknowlegement.tex . 致谢
 └─ 📃 references.bib ....... 参考文献的 bibtex 文档
```

--------------

## 一些问题

### 参考文献格式：

《统一规定》的文档中要求：

**根据GB/T 7714-2005的要求书写参考文献，可采用顺序编码制，也可采用著者-出版年制，但全文必须统一**。

本文档默认**顺序编码制**，如果需要采用著者-出版年制，可以在
```
\usepackage{gbt7714}        % Chinese GBT 7714 style reference list
\bibliographystyle{gbt7714-numerical}
```
修改为将`gbt7714-numerical`改为`gbt7714-author-year`，也可指定2005版本比如`gbt7714-2005-numerical`或`gbt7714-2005-author-year`。
如果发现输出文献格式不符合要求，或者与Google Scholar/CNKI输出的格式不同，建议仔细检查`references.bib`中的有问题条目，是否信息完整。

B.T.W. `GB/T7714`标准文档给出的示例的西文 authors 名字全部是大写（如图），但是 CNKI 等网站输出的是正常大小写，此区别不影响图书馆上传（个人经历），如介意大写问题建议自行 Google 修改。

![image](https://github.com/nathanatgit/tju_MasterDr_Latex_template/assets/20399271/8720a497-13af-4027-bff3-8ba31bfce867)

```
扩展资料：
https://github.com/hushidong/biblatex-gb7714-2015
https://github.com/zepinglee/gbt7714-bibtex-style
```


### 关于页边距：

按文档要求，硕博论文规定**奇偶页固定**、**左右不对等**页边距，在双面打印的时候是一件很迷的事情，保持尊重吧就。

建议上交电子版用固定页边距的版本，打印的时候生成一版奇偶页页边距互换的 pdf（修改`packages.tex`内注释掉的geometry设置，`offbinding=8mm`的版本）。

```
% \usepackage[top= 27.5mm,bottom=25.4mm,left=27.7mm,right=27.7mm,head=15mm,foot=17.5mm,bindingoffset=8mm]{geometry}  % 左右页边距奇偶页互换版本
\usepackage[a4paper,asymmetric,top= 27.5mm,bottom=25.4mm,left=35.7mm,right=27.7mm,head=15mm,foot=17.5mm,bindingoffset=0mm]{geometry}  % 页边距固定版本
```

### 关于页眉页脚

按文档要求，所有章节起始于基数页，奇数页页眉为章节标题，偶数页页眉为`天津大学博士学位论文`或者`天津大学硕士学位论文`，按需在`styCtrl.tex`中修改:
```
%% Define headers and footers
\pagestyle{fancy}               % fancy is to show the header and footer
……
\fancyhead[CO]{\songti \wuhao \leftmark}    % the CO means centering the odd pages' header
\fancyhead[CE]{\songti \wuhao 天津大学博士学位论文} % the CE centering the even pages' header
……
```

### 关于表格/图片：

**格式**：

默认采用三线表。表格标题和图片标题在统一规定中并未体现或者说有歧义（原文仅在 4.3.3 中规定了内容文字格式，即“图、表内容为五号字，中文字体为宋体，英文字体为 Times New Roman”，未规定标题格式，这个统一规定文档中的表格标题是黑体小四）。

本模板按照正文格式处理（宋体小四 20 磅行距）。表格内容文字规定了五号字，设置了`\tabfont`命令方便初始化（参考文档中的示例）。

**扩展资料**：

```
xelatex 支持的图片格式
https://tex.stackexchange.com/questions/1072/which-graphics-formats-can-be-included-in-documents-processed-by-latex-or-pdflat
figure 环境的的常见排版
https://www.overleaf.com/learn/latex/Inserting_Images
```

### 独创性声明：

参考统一要求文档的附录，“天津大学”四个字是`楷体GB_2312`，所以没有这个字体的话就会被被替换成了``微软雅黑``显示（如下图）。

![image](https://github.com/nathanatgit/tju_MasterDr_Latex_template/assets/20399271/7da58e83-c328-4ed4-8b40-b3a470e2b256)

鉴于现在是2023年，`楷体_GB2312`字库可能只会在Windows XP的电脑上默认出现，并且`GB2312`标准早已被`GB18030-2005`所替代，如果不是手动下载安装根本不会用到这个远古字库（`GB2312`和`GB18030`不存在字形区别，仅仅是字库扩充），所以本模板中改为``楷体``（如图）。

![image](https://github.com/nathanatgit/tju_MasterDr_Latex_template/assets/20399271/7f4d7a62-9a99-402f-b868-48a3f877e3db)


### 封面：

模板中的封面有4种，依照统一要求的文档附录，放在了`cover_Ph_D.tex（学术博士）`、`cover_pro_D.tex（专业博士）`、`cover_acaMa.tex（学术硕士）`和`cover_proMa.tex（专业硕士）`中，请对应修改`main.tex`中相应注释
```
\input{preface/cover_Ph.D.tex}          % Ph.D cover page
% \input{preface/cover_pro.D.tex}       % Professional doctor cover page
% \input{preface/cover_acaMa.tex}       % Master with academic degree cover page
% \input{preface/cover_proMa.tex}       % Master with professional degree cover page
```

### 相关仓库：

https://github.com/twtstudio/TJUThesisLatexTemplate

https://github.com/a171232886/TJUThesis_master_2021

https://github.com/jiangqideng/tjuthesis_master_2016

https://github.com/6gbluewind/Tjuthesis_phd_1.2-

感谢前人大佬们
