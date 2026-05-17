# Ride-hailing-framework-collection

本项目是一个面向网约车与拼车系统研究的框架集合，整理了多类车辆调度、订单匹配、路径规划和强化学习实验代码，可用于网约车系统建模、算法复现、实验对比和课程/科研演示。

This project is a framework collection for ride-hailing and ride-sharing research, including experimental code for vehicle dispatching, order matching, path planning, and reinforcement-learning-based decision making.

该项目被多人关注，已为多篇论文实验的实施提供基础。项目采用模块化组织方式，研究人员可以基于现有代码快速搭建实验环境，复现实验流程，或进一步扩展新的调度策略、匹配算法和学习模型。

---

## 目录 Table of Contents

- [项目目录 Project Directory](#项目目录-project-directory)
- [使用方法 Getting Started](#使用方法-getting-started)
- [项目内容 Project Content](#项目内容-project-content)
- [模块说明 Module Description](#模块说明-module-description)
- [项目声明 Project Statement](#项目声明-project-statement)
- [注意事项 Notes](#注意事项-notes)

---

## 项目目录 Project Directory

```text
Ride-hailing-framework-collection/
│
├── newridehailing/          # 新版网约车实验框架
│   ├── env/                 # 实验环境相关代码
│   └── re/                  # 实验结果或相关模块
│
├── oldridehailing/          # 旧版网约车实验框架
│   ├── old_rl.py            # 强化学习实验代码
│   ├── original_environment.py
│   ├── TJ.csv               # 实验数据
│   ├── dy.csv               # 实验数据
│   ├── 拾取概率.csv          # 实验数据
│   └── 调理数据4.csv         # 实验数据
│
├── ridesharing/             # 拼车/网约车核心算法框架
│   ├── Action.py            # 动作定义
│   ├── CentralAgent.py      # 中央调度智能体
│   ├── Environment.py       # 系统环境
│   ├── Experience.py        # 经验样本
│   ├── LearningAgent.py     # 学习智能体
│   ├── NeurADPplus.py       # 神经近似动态规划模型
│   ├── NeurAdpVanillaVF.py  # 基础价值函数模型
│   ├── Oracle.py            # 可行动作/调度求解模块
│   ├── Path.py              # 路径表示
│   ├── ReplayBuffer.py      # 经验回放池
│   ├── Request.py           # 订单请求定义
│   ├── main_plus.py         # 改进模型运行入口
│   ├── main_scoring.py      # 评分实验入口
│   ├── main_vanilla.py      # 基础模型运行入口
│   └── segment_tree.py      # 优先经验回放辅助结构
│
└── README.md
```

---

## 使用方法 Getting Started

### 1. 克隆项目 Clone the repository

```bash
git clone https://github.com/asdasdasd964/Ride-hailing-framework-collection.git
cd Ride-hailing-framework-collection
```

### 2. 安装依赖 Install dependencies

建议使用 Python 3.7 及以上版本，并根据实际运行模块安装依赖：

```bash
pip install numpy pandas scikit-learn tensorflow torch
```

如果只运行部分模块，可根据报错信息补充对应依赖。

### 3. 运行示例 Run examples

进入对应模块目录后运行实验入口文件，例如：

```bash
cd ridesharing
python main_vanilla.py
```

或运行改进模型：

```bash
python main_plus.py
```

旧版实验代码可在 `oldridehailing/` 目录下运行：

```bash
cd oldridehailing
python old_rl.py
```

---

## 项目内容 Project Content

本项目可用于网约车和拼车系统的算法实验，支持车辆调度、订单匹配、路径规划、价值函数学习和强化学习决策等任务。项目包含旧版与新版实验框架，并保留了较完整的核心模块，便于研究人员进行对比实验、算法复现和二次开发。

项目结合了当前主流的机器学习、深度学习和优化方法，能够支持常规实验训练、模型评估、订单请求模拟、车辆状态更新和实验日志记录等功能。用户只需根据实验目标调用对应模块，即可完成基础仿真与模型验证。

该项目自发布以来已受到相关研究人员和开发者的关注，已为多篇论文实验的实施提供基础。其模块化结构降低了网约车实验系统的搭建成本，使研究者可以将更多精力集中在算法设计、参数调整和实验分析上，而不必从零开始构建完整的调度环境。

---

## 模块说明 Module Description

### 1. 订单请求 Request

`Request.py` 用于描述乘客订单请求，包括上车点、下车点、时间约束、订单价值等信息，是调度和路径规划模块的基础输入。

### 2. 路径规划 Path

`Path.py` 用于表示车辆的行驶路径和服务顺序，可用于计算车辆完成订单后的状态变化、行程延迟和服务可行性。

### 3. 调度决策 Central Agent

`CentralAgent.py` 负责根据当前车辆状态、订单请求和动作评分结果进行统一调度，选择较优的车辆-订单匹配方案。

### 4. 环境模拟 Environment

`Environment.py` 和 `original_environment.py` 用于构建网约车运行环境，模拟车辆移动、订单生成、时间推进和状态更新过程。

### 5. 强化学习与价值函数 Learning Model

`LearningAgent.py`、`NeurADPplus.py`、`NeurAdpVanillaVF.py` 等文件提供了基于学习的价值函数估计与策略优化框架，可用于研究网约车系统中的长期收益优化问题。

### 6. 经验回放 Replay Buffer

`ReplayBuffer.py` 和 `segment_tree.py` 用于存储和采样历史经验数据，支持模型训练过程中的经验回放和优先采样。

---

## 项目声明 Project Statement

本项目的作者及单位：  
The author and affiliation of this project:

```text
项目名称（Project Name）：Ride-hailing-framework-collection
项目地址（Repository）：https://github.com/asdasdasd964/Ride-hailing-framework-collection
作者/维护者（Author / Maintainer）：asdasdasd964
作者单位（Affiliation）：暨南大学网络空间安全学院
```

本项目主要用于科研实验、算法复现和学习交流。若本项目对你的研究或论文实验有所帮助，建议在论文、报告或项目文档中注明本仓库来源。

---

## 注意事项 Notes

- 本项目为网约车与拼车系统相关实验代码集合，部分模块可能需要根据本地数据路径进行调整。
- 运行前请确认数据文件、日志目录和模型保存目录是否存在。
- 不同实验入口文件的参数设置可能不同，建议先阅读对应 `.py` 文件中的参数配置。
- 若用于论文实验，请记录实验环境、依赖版本、随机种子和参数设置，以保证实验结果可复现。

---

## Citation

如果本项目对你的研究有帮助，可按如下格式引用：

```bibtex
@misc{ride_hailing_framework_collection,
  title  = {Ride-hailing-framework-collection},
  author = {asdasdasd964},
  year   = {2026},
  note   = {A framework collection for ride-hailing and ride-sharing experiments},
  url    = {https://github.com/asdasdasd964/Ride-hailing-framework-collection}
}
```
