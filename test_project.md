# 测试项目
PS：由于测试项目内部导入（包括显式导入隐式导入，相对导入绝对导入__init__命名空间等等），理论上要包括所有导入方式

PS：作为检测手段，每个py不实际运行程序，而是检测是否导入成功，和导入的值是否为true,若两者都成立则返回值true,否则输出false，该值可以在作为模块被导入其他py文件是否判断导入的值是否为true.

PS:运行程序后输出所有返回false的文件位置

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
