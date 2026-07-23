# datasense - CSV数据分析命令行工具

[![CI](https://github.com/zxs06205/datasense/actions/workflows/ci.yml/badge.svg)](https://github.com/zxs06205/datasense/actions/workflows/ci.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**datasense** 是一个轻量级命令行工具，用于快速分析和可视化CSV数据文件。无需编写代码，一条命令即可生成数据统计摘要和图表。

## 面向用户

数据分析初学者、学生以及需要快速探索数据集的开发者。不需要启动Jupyter或编写Python脚本，直接在终端中查看数据概况。

## 安装

```bash
git clone https://github.com/zxs06205/datasense.git
cd datasense
pip install .
```

### Windows 用户注意

安装后如果 `datasense` 命令找不到，请尝试以下方法之一：

**方法一：** 将 Python 的 Scripts 目录添加到系统 PATH（重新打开 CMD 生效）：
```
set PATH=%PATH%;%USERPROFILE%\AppData\Local\Programs\Python\Python312\Scripts
```

**方法二：** 使用 `python -m` 运行（不需要额外配置）：
```bash
python -m datasense stats examples/iris.csv
python -m datasense plot examples/iris.csv --x sepal_length --y sepal_width
python -m datasense summary examples/iris.csv
```

## 快速开始

```bash
# 查看基本统计信息
datasense stats examples/iris.csv

# 生成可视化图表
datasense plot examples/iris.csv --x sepal_length --y sepal_width

# 查看数据概览
datasense summary examples/iris.csv
```

## 支持的命令

| 命令 | 说明 |
|------|------|
| `summary` | 显示数据基本信息：行数、列名、数据类型、缺失值 |
| `stats` | 计算数值列的描述性统计：均值、标准差、四分位数等 |
| `plot` | 生成散点图或直方图，输出PNG文件 |

## 项目结构

```
datasense/
├── datasense/
│   ├── __init__.py
│   ├── cli.py          # 命令行接口
│   ├── loader.py       # 数据加载模块
│   ├── stats.py        # 统计计算模块
│   └── visualize.py    # 可视化模块
├── tests/
├── examples/
│   └── iris.csv        # 示例数据集
└── .github/workflows/
    └── ci.yml          # CI自动化
```

## 许可证

MIT License
