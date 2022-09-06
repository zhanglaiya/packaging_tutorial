# packaging_tutorial
PyPi 制作包tutorial

## 创建包文件夹
创建一个文件夹packaging_tutorial，结构如下
```
packaging_tutorial/
├── LICENSE
├── pyproject.toml
├── README.md
├── src/
│   └── example_package_YOUR_USERNAME_HERE/
│       ├── __init__.py
│       └── example.py
└── tests/
```
### pyproject.toml
```
[build-system]
requires = ["hatchling"]
build-backend = "hatchling.build"
```
包基本信息
```
[project]
name = "example_package_YOUR_USERNAME_HERE"
version = "0.0.1"
authors = [
  { name="Example Author", email="author@example.com" },
]
description = "A small example package"
readme = "README.md"
license = { file="LICENSE" }
requires-python = ">=3.7"
classifiers = [
    "Programming Language :: Python :: 3",
    "License :: OSI Approved :: MIT License",
    "Operating System :: OS Independent",
]

[project.urls]
"Homepage" = "https://github.com/pypa/sampleproject"
"Bug Tracker" = "https://github.com/pypa/sampleproject/issues"
```
构建
```
py -m pip install --upgrade build
py -m build
```
这一步做完生产 dist文件夹  
上传到[https://test.pypi.org](https://test.pypi.org)
```
py -m pip install --upgrade twine
py -m twine upload --repository testpypi dist/*
```

安装
```
py -m pip install --index-url https://test.pypi.org/simple/ --no-deps example-package-YOUR-USERNAME-HERE
```

使用
```
>>> from example_package_YOUR_USERNAME_HERE import example
>>> example.add_one(2)
3
```
