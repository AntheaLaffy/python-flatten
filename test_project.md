# 测试项目
这是一个检测自身项目的导入是否正确的项目，用于测试扁平化后是否正确修改了导入路径。测试方式：处理前运行一次，看看是否有返回false值的文件名理论上应该为0；扁平化处理后再运行一次，输出的返回值为false文件的导入就是没有被正确扁平化处理的。

PS：由于测试项目内部导入（包括显式导入隐式导入，相对导入绝对导入__init__命名空间等等），理论上要包括所有导入方式

PS：作为检测手段，每个py不运行实际翻译api的程序，而是作为导入的载体，分别检测导入语句是否导入成功，和导入的值是否为true,若两者都成立则返回值true,否则输出false，该值可以在作为模块被导入其他py文件是否判断导入的值是否为true.（如果没有导入语句，报告没有导入语句即可。不需检测是否导入成功，也不需要返回值）

PS:运行main.py后汇总所有py的报告，输出没有导入语句的文件和返回值为false的文件的位置

```tree
test_project/
├── main.py
├── utils/
│   ├── __init__.py
│   ├── helper.py
│   └── validation.py
├── translator/
│   ├── __init__.py
│   ├── config.py
│   ├── api.py
│   └── processors/
│       ├── __init__.py
│       └── text_processor.py
└── models/
    ├── __init__.py
    ├── user.py
    └── payment.py
```
