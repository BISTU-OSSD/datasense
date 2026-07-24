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

### 命令行工具

| 命令 | 说明 |
|------|------|
| `summary` | 显示数据基本信息：行数、列名、数据类型、缺失值 |
| `stats` | 计算数值列的描述性统计：均值、标准差、四分位数等 |
| `plot` | 生成散点图或直方图，输出PNG文件 |

### Web 可视化界面（新增）

除了命令行工具，datasense 还提供了 **Web 网页端界面**，由组员 **李鑫硕** 开发。无需打开终端，在浏览器中即可完成数据分析。

**快速启动：**

```bash
cd web
pip install -r requirements.txt
python app.py
```

打开浏览器访问 **http://localhost:5000**，即可看到 Web 界面。

**Web 端功能：**
- 拖拽上传 CSV 文件或一键加载示例数据（鸢尾花数据集）
- 数据概览：显示文件名、行列数、每列数据类型及缺失值统计
- 统计分析：对数值列输出均值、标准差、最小值、四分位数、最大值
- 数据预览：表格形式展示前 10 行数据
- 交互式可视化：选择 X/Y 轴列，实时生成散点图或直方图

> Web 端完整代码在 `web/` 目录下，由李鑫硕独立开发完成。

## 项目结构

```sh
datasense/
├── datasense/
│   ├── __init__.py
│   ├── cli.py          # 命令行接口（曾祥盛）
│   ├── loader.py       # 数据加载模块（马明宇）
│   ├── stats.py        # 统计计算模块（李鑫硕）
│   └── visualize.py    # 可视化模块（朱皓锴）
├── web/                # Web网页端界面（李鑫硕）
│   ├── app.py          # Flask应用
│   ├── templates/      # 前端页面
│   └── README.md       # Web端说明
├── tests/
├── examples/
│   └── iris.csv        # 示例数据集
└── .github/workflows/
    └── ci.yml          # CI自动化
```

## 许可证

MIT License
