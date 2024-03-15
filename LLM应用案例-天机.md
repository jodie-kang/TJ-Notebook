# LLM应用案例：人情世故大模型系统-天机
[TOC]

# 引言
<!-- ToDo：用现实生活场景，引出天机具备的功能 -->
你是否苦恼于餐桌敬酒？
别急别急，您的人情世故小助手已上线~

## 项目背景介绍
天机是 SocialAI（来事儿AI）制作的一款免费使用、非商业用途的人工智能系统。您可以利用它进行涉及传统人情世故的任务，如：如何敬酒、如何说好话、如何会来事儿等，以提升您的情商和"核心竞争能力"。
来事儿AI（Tianji）构建并开源了常见的大模型应用范例，涉及prompt、Agent、知识库、模型训练等多种技术。


## 目标与意义
<!-- ToDo：扩充并润色 -->
目标：探索大模型与人情世故法则结合的多种技术路线，构建AI服务于生活的智能应用。
意义：通用人工智能
我们坚信，只有人情世故才是未来AI的核心技术，只有会来事儿的AI才有机会走向AGI，让我们携手见证通用人工智能的来临。 —— "天机不可泄漏。"


## 主要功能
<!-- ToDo：本周更新知识库代码后，补充相应功能 -->
天机项目覆盖了常见人际交往中的七大领域：敬酒礼仪文化，请客礼仪文化，送礼礼仪文化，送祝福，如何说对话，化解"尴尬"场合，矛盾&冲突应对
1. Prompt：敬酒词，请客，送礼物，送祝福，日常沟通，化解尴尬，应对冲突矛盾
2. AIGame：哄哄模拟器，忠心模拟器，。。。
3. 知识库：大模型幻觉

# 技术实现
结合这些领域，Tianji涉及到的技术路线共有四种：
- 纯prompt（包括AI游戏）：内置 system prompt 基于大模型自身能力对话。
- Agent（MetaGPT等）：利用 Agent 架构的得到更丰富、更定制化详细的回答。
- 知识库：直接检索人情世故法则（比如餐桌上一般怎么喝酒）。
- 模型训练：基于不同优秀的模型基座，在积累大量数据的情况下进行Lora微调或全量微调。

## 环境要求

### 计算资源要求
<!-- 说明应用所需的计算资源，如 CPU、GPU、内存等，以及推荐的硬件配置。 -->
<!-- ToDo：写一个表格 -->
Tianji涉及到的技术路线共有四种：Prompt、Agent，知识库，模型训练。
其中，Prompt和Agent只需要配置大模型秘钥，不需要显卡，使用常规笔记本电脑即可运行。
<!-- ToDo：根据选择的基座大模型，配置所需计算资源， -->


### 开发环境要求
<!-- 指明搭建应用开发环境所需的软件和工具，如操作系统、IDE 等，以及相关配置要求。 -->
操作系统：Windows，Linux，Mac
IDE：PyCharm，VSCode
<!-- ToDo：其他相关配置要求 -->


### 环境配置方法
``` shell
克隆仓库：git clone https://github.com/SocialAI-tianji/Tianji.git
创建虚拟环境：conda create -n TJ python=3.11
激活环境：conda activate TJ
安装环境依赖：pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
```

在项目内创建.env文件，填写你的大模型秘钥
``` env
OPENAI_API_KEY=
OPENAI_API_BASE=
ZHIPUAI_API_KEY=
BAIDU_API_KEY=
OPENAI_API_MODEL=
HF_HOME='./cache/'
HF_ENDPOINT = 'https://hf-mirror.com'
HF_TOKEN=
```

## 开发流程简述
### 当前的项目版本及未来规划
<!-- ToDo：和作者沟通确定 -->


### 核心 Idea
<!-- 简洁明了地阐述应用的核心理念和创新点，引导读者深入理解应用的设计初衷。 -->
<!-- ToDo：扩充并润色 -->
核心理念：利用大模型工具，提高个人情商
创新点：大模型+人情世故法则

### 使用的技术栈
<!-- ToDo：画一个表格，四种技术路线涉及的前置知识和推荐阅读材料 -->
前置知识：Prompt，推荐阅读材料：LLM Universe
前置知识：知识库，推荐阅读材料：LLM Universe
前置知识：Agent，推荐阅读材料：DW【Agent】专区
前置知识：模型训练，推荐阅读材料：xxx

## 应用架构
<!-- 展示应用的整体架构，包括各个模块之间的关系和交互方式，帮助读者理解应用的组织结构和工作原理。注：在书写时，需要从 RAG 的一般框架出发，使读者能够理解该应用与教程内容的关联。 -->
<!-- ToDo：画一个项目架构图-->

## 数据预处理
<!-- 介绍如何对原始数据进行预处理，包括多类型数据清洗、标准化、向量化等，以满足 RAG 模型的输入要求。 -->
<!-- ToDo: 数据预处理代码写在 tools/，理解代码，写出数据处理思路 -->

# 技术路线1：Prompt
<!-- ToDo：本教程的核心，整理Prompt相关资料，理解代码 tianji\prompt 和 test\prompt-->
## 前置知识
<!-- 参考第一版 Prompt设计: https://datawhalechina.github.io/llm-universe/#/C5/ -->

## 设计思路

## step1：

## step2：

## 实现技巧
<!-- 讨论如何设计有效的 Prompt，以提高模型对于用户输入的理解和生成能力。 -->
<!-- 指导如何对 Prompt 工程进行调试和优化，以提高模型的响应质量和用户体验。 -->


# 技术路线2：Agent
<!-- ToDo：本教程的核心，整理Agent相关资料，理解代码 tianji\agent 和 test\agent-->
## 前置知识
<!-- 参考Agent Tutorial：https://github.com/datawhalechina/agent-tutorial -->
<!-- 参考Hugging Muti Agent：https://deepwisdom.feishu.cn/wiki/MLILw0EdRiyiYRkJLgOcskyAnUh -->

## 设计思路
给定人设并导入参考聊天话术、历史聊天语料进行聊天。
根据当前状态和聊天与恋爱相关性等综合打分。给出当前回合的打分情况
## step1：

## step2：

## 实现技巧

# 技术路线3：知识库
<!-- ToDo：本教程的核心，整理知识库相关资料，理解代码 tianji\knowledge 和 test\knowledge-->
## 前置知识
<!-- 参考第一版CH3：https://datawhalechina.github.io/llm-universe/#/C3/3.%20%E9%A1%B9%E7%9B%AE%E6%9E%B6%E6%9E%84%E7%AE%80%E6%9E%90?id=_1-%e6%95%b4%e4%bd%93%e6%9e%b6%e6%9e%84 -->

## 设计思路

## step1：

## step2：

## 实现技巧


# 总结与展望

## 每个实例的关键点总结

## 未来研究方向展望
