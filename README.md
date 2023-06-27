# tju_MasterDr_Latex_template

 Tianjin University thesis latex template for personal use. Based on 2021 revised version.

环境：

* Windows
* VSCode

* Latex Workshop Extension
* texlive 2022

编译工具：xelatex + bibtex

将以下设置补充添加到Latex-Workshop的recipes设置中

![1687837001540](image/README/1687837001540.png)

```
"latex-workshop.latex.recipes":
[
    {
        "name": "xelatex ➞ bibtex",
        "tools": [
            "xelatexmk",
            "bibtex"
        ]
    }
]
```
