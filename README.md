# python-flatten
目的：做一个python项目扁平化的工具。将整个项目的py文件合并到main.py中

用途：1.多个项目的合并前的预处理 2.对项目语言翻译前的预处理(比如把python翻译为语言)

功能实现：合并py文件，处理依赖项路径

流程：遍历检索py→（复制重命名py→修改py外部导入地址→删除原py）

----------------------------------------------
## 一、遍历检索py
遍历得到项目结构树，滤除非py文件的信息，得到tree.txt

PS:检测到tree.txt文件后进入二三四流程的循环（每一次循环只操作一个py文件，按tree记录的顺序操作最新的py文件，在四流程完成后会生成或者更新complish_tree.txt，记录操作完成的py文件的原地址。随后进入下个循环，通过tree和complish_tree的差异得出最新py开始流程循环，直到差异中没有任何py文件或者手动停止）(根目录的py文件跳过2，4流程，只需进行3修改外部导入然后更新complish_tree文件)
## 二、复制重命名py(以translator/config/api.py为例)
根据tree.txt文件

1.复制py到根目录：得到translator/api.py

2.按照相对路径重命名:translator/api.py → translator/config.api.py

## 三、修改py外部导入地址
对象：重名后的py
PS:由于只更改了项目内部的py位置，没有动导入的标准库和项目的其他文件，所以只修改tree.txt记录的内部py模块的导入路径

PS：该怎么处理显式导入和隐式导入还有__init__.py文件，我还没想好

PS：怎么处理相对导入和绝对导入我也没想好

三流程完成后，给py文件顶端加入"#外部导入地址已全部修改！+修改时间"的注释
## 四、删除原py（以translator/config.api.py为例)
1.删除原py文件：~translator/config/api.py~

2.更新complish_tree.txt，写入已处理完成的py文件原路径
