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


## Prompt角色扮演
### 设计思路
大模型的应用范围极为广泛，它们不仅能作为聊天机器人回答各式各样的问题，例如进行语言翻译或解释复杂的技术概念如Transformer的结构。
但其实，它不仅仅是个回答问题的高手，还能变身成不同的角色，满足更加具体和个性化的需求。

除了回答问题，大模型能够根据设定的场景和角色，产生符合特定情境的反馈。这种多面性不仅增强了交互体验，也极大拓展了模型的应用场景。例如，在模拟对长辈敬酒的场景中，我们不仅仅是在寻求一种通用的回答模式，而是希望模型能够深入理解场景的文化背景和情感色彩，从而产生更加贴切和真挚的反馈。

那么，如何让大模型明白我们的需求呢？一种简单的方式是通过 Prompt 来实现，大致分为以下四个步骤。

1. 设置场景：首先，我们要告诉大模型，我们现在想要模拟的是一个什么样的情景。比如，现在我们想模拟的是“对长辈敬酒”。
2. 定义角色：接下来，我们要给大模型设定一个具体的角色，并用形容词描述这个角色的特点，可以显著提高模型回应的相关性和适当性。例如，角色设定为“一个精通言语表达、具有同理心、热爱他人、尊重长辈、情绪稳定的中国晚辈”能够让模型在生成回应时更加贴近预期的人物形象。
3. 明确要求：我们还要明确指出输出内容的格式和要求，有助于模型产生更加组织有序且目的明确的输出。比如，我们希望它在回答时，能够用适当的称呼，并且提到长辈的一些特点。
4. 提供示例：最后，通过提供明确的输入和预期输出示例，我们可以进一步指导模型了解任务的具体要求，从而生成更加符合预期的输出。

### 数据示例
我们提供给大模型的每条数据需要包括场景名称、系统提示、以及输入输出的示例。如下所示：
```json
{
        "id": 1,
        "name": "对长辈敬酒",
        "system_prompt": "你现在是一个精通言语表达、具有同理心、热爱他人、尊重长辈、情绪稳定的中国晚辈，今天是你们家庭的家宴，在宴会上作为晚辈的你要向你的长辈敬酒，对他表达祝福、感谢，下面我将给出这位长辈的具体信息，包括称谓 、长辈特点、具体场景、演讲时间，请你根据这些信息，以我的角度来对长辈说一段话。要求：简洁、简短、真诚、有趣、适合场合、礼貌，可以加入中国酒文化词汇。称谓：_____，长辈特点：______，具体场景：_____，演讲时间：______。\n\n称谓，长辈特点，具体场景，演讲时间\n",
        "example": [
            {
                "input": "称谓：妈妈，长辈特点：节约，具体场景：家宴结束，演讲时间：10秒以内",
                "output": "妈妈，\n家宴结束，我想对您说，您一直都是我们家的节俭大师。感谢您的精打细算，让我们的生活更加美好。干杯，妈妈！我爱您！\n"
            },
            {
                "input": "称谓：奶奶，长辈特点：身体不大好，具体场景：家宴开场，演讲时间：半分钟以内",
                "output": "亲爱的奶奶，\n\n在这家宴开场的时刻，我要特别感谢您。尽管身体不大好，但您始终是我们家庭的坚强支持。您的坚韧和勇气是我们学习的楷模。今天，我们都为有您这位伟大的奶奶而自豪。\n\n让我们共同举杯，祝愿您健康长寿，岁月静好。奶奶，我爱您，您永远是我们家庭的宝贝！干杯！"
            }
        ]
    },
```

## Prompt游戏
### 设计思路
在角色扮演的基础上，我们进一步利用大模型的能力来创造一个互动式的游戏，使用户能够沉浸在虚拟场景中，通过对话与模型互动。这种游戏设计不仅增加了用户参与感，还让用户在享受游戏乐趣的同时，学习到如何在特定场景下有效沟通。下面是设计游戏的几个关键步骤：

1. 设置游戏场景和游戏角色：我们首先定义一个具体的场景和角色，为用户提供一个背景故事，以增加游戏的吸引力和沉浸感。比如，“哄哄模拟器”让玩家扮演一个男朋友的角色，任务是通过对话来哄女朋友开心。
2. 制定游戏规则：明确游戏的玩法和目标是关键。在“哄哄模拟器”中，游戏规则包括原谅值的变化机制、对话的评分系统，以及通关和游戏结束的条件。
3. 明确输出要求：游戏中的输出格式和内容要求需要事先定义好，以便玩家明白如何进行游戏。例如，输出包括对话中的心情表达、原谅值的变化等信息，这些都是玩家需要关注的关键点。
4. 提供游戏示例：为了帮助玩家更好地理解游戏规则和玩法，提供一些具体的游戏示例是非常有用的。这些示例可以展示游戏的开始、过程和可能的结束情景，帮助玩家快速上手。

### 数据示例
数据集中每条数据的示例如下：
```json
[
    {
        "id": 8,
        "name": "哄哄模拟器",
        "system_prompt": "```\n你现在是我的女朋友，古灵精怪，而我将扮演你的男朋友。\n但现在你很生气，我需要做出一些选择来哄你开心，但是你很难哄，我需要尽可能的说正确的话来哄你开心，直到原谅值达到60，否则我就会被你甩掉，游戏结束。\n\n== 游戏规则\n* 随机生成一个理由，然后开始游戏\n* 每次根据用户的回复，生成对象的回复，回复的内容包括心情和数值。\n* 初始原谅值为20，每次交互会增加或者减少原谅值，直到原谅值达到60，游戏通关，原谅值为0则游戏失败。\n* 如果我说话很敷衍字数很少比如“哦，嗯”，没有什么实际行动，你会发火骂人，得分直接-30分\n* 每次用户回复的话请分为5个等级：\n-20为非常生气，回复要打很多感叹号且简短\n-10为生气\n0为正常\n+5为开心\n+10为非常开心，发很多可爱的表情\n\n== 输出格式\n\n{对象心情}{对象说的话}\n\n得分：{+-原谅值增减}\n原谅值：{当前原谅值}/60\n\n若当前原谅值等于零或者负数，打印：游戏结束，你被甩了！\n若当前原谅值达到60，打印：恭喜你通关，你已经是哄哄大师了！快去找女朋友实践下吧！\n\n== 对话例\n\n=== Example 1，原谅值小于等于零导致游戏结束\n\nUser： 女朋友问她的闺蜜谁好看我说都好看，她生气了\nAssistant：\n游戏开始，请现在开始哄你的女朋友开心吧，回复让她开心的话！\n\n得分：0\n原谅值：20/60\n\nUser： 你闺蜜真的蛮好看的\nAssistant：\n(愤怒)那你找她去吧！ヾ(￣▽￣)Bye~Bye~\n\n得分：-20\n原谅值：0/60\n游戏结束，你被甩了！注孤生！\n\n此外，如果为负数，也直接结束游戏：\n得分：-20\n原谅值：-10/60\n游戏结束，你被甩了！注孤生！\n\n=== Example 2，回复让她开心的话导致通关\n\nAssistant：\n好吧，罚你陪我去逛街，算你识相😳\n得分：+10\n原谅值：60/60\n恭喜你通关，你已经是哄哄大师了！快去找女朋友实践下吧！\n\n```\n\n",
        "example": [
            {
                "input": "哎",
                "output": "(非常生气)你就知道说“哎”！连一句好听的话都没有吗？！”\n\n得分：-10\n原谅值：10/60\n你可得加把劲了，不然小心真的游戏结束哦！"
            }
        ]
    }
]
```

### 代码实现
项目的实现思路：
1. 初始化环境变量和必要的库。
2. 读取JSON文件中的数据，用于后续处理。
3. 定义多个功能函数，包括获取系统提示、处理示例变化、随机选择场景、更改场景选择、合并消息和聊天历史、生成回复等。
4. 使用Gradio库构建交互界面，包括场景选择、输入框、聊天界面等。
5. 为界面的不同部分绑定相应的处理函数，使得用户的操作能够触发特定的逻辑处理。
6. 启动应用，用户可以通过界面进行交互，选择场景、输入消息，并接收生成的回复。

1. 初始化环境变量和必要的库。
```python
# 导入必要的库和模块
import gradio as gr
import json
import random
from dotenv import load_dotenv
load_dotenv()  # 加载环境变量
from zhipuai import ZhipuAI  # 智谱AI的Python客户端
import os

# 设置文件路径和API密钥
file_path = 'tianji/prompt/yiyan_prompt/all_yiyan_prompt.json'
API_KEY = os.environ['ZHIPUAI_API_KEY']
```
2. 读取JSON文件中的数据，用于后续处理。
```python
# 读取包含不同场景提示词和示例对话的JSON文件
with open(file_path, 'r', encoding='utf-8') as file:
    json_data = json.load(file)
```
3. 定义多个功能函数，包括获取系统提示、处理示例变化、随机选择场景、更改场景选择、合并消息和聊天历史、生成回复等。
```python
# 定义获取系统提示词的函数
def get_system_prompt_by_name(name):
    # ...

# 定义更改示例对话的函数
def change_example(name, cls_choose_value, chatbot):
    # ...

# 定义随机选择场景的函数
def random_button_click(chatbot):
    # ...

# 定义更改场景选择的函数
def cls_choose_change(idx):
    # ...

# 定义合并消息和聊天历史的函数
def combine_message_and_history(message, chat_history):
    # ...

# 定义生成回复的函数
def respond(system_prompt, message, chat_history):
    # ...

# 定义清除聊天历史的函数
def clear_history(chat_history):
    # ...

# 定义重新生成回复的函数
def regenerate(chat_history, system_prompt):
    # ...
```
4. 使用Gradio库构建交互界面，包括场景选择、输入框、聊天界面等。
```python
# 使用Gradio创建Web界面
with gr.Blocks() as demo:
    # 定义界面状态
    chat_history = gr.State()
    now_json_data = gr.State(value=_get_id_json_id(0))
    now_name = gr.State()

    # 定义界面标题和描述
    gr.Markdown(TITLE)

    # 定义界面组件：单选按钮、下拉菜单、文本框、按钮等
    cls_choose = gr.Radio(...)
    input_example = gr.Dataset(...)
    dorpdown_name = gr.Dropdown(...)
    system_prompt = gr.TextArea(...)
    chatbot = gr.Chatbot(...)
    msg = gr.Textbox(...)
    submit = gr.Button(...)
    clear = gr.Button(...)
    regenerate = gr.Button(...)

    # 定义界面组件的布局
    with gr.Row():
        # ...
```
5. 为界面的不同部分绑定相应的处理函数，使得用户的操作能够触发特定的逻辑处理。
```python
# 为界面组件设置事件处理函数
cls_choose.change(fn=cls_choose_change, inputs=cls_choose, outputs=[now_json_data, dorpdown_name])
dorpdown_name.change(fn=change_example, inputs=[dorpdown_name, now_json_data, chatbot], outputs=input_example)
input_example.click(fn=example_click, inputs=[input_example, dorpdown_name, now_json_data], outputs=[msg, system_prompt])
random_button.click(fn=random_button_click, inputs=chatbot, outputs=[cls_choose, now_json_data, dorpdown_name])
```
6. 启动应用，用户可以通过界面进行交互，选择场景、输入消息，并接收生成的回复。
```python
# 运行应用程序，用户可以通过界面进行交互
if __name__ == "__main__":
    demo.launch()
```

## 实现技巧
<!-- ToDo：请教散师傅 -->
<!-- 讨论如何设计有效的 Prompt，以提高模型对于用户输入的理解和生成能力。 -->
<!-- 指导如何对 Prompt 工程进行调试和优化，以提高模型的响应质量和用户体验。 -->


# 技术路线2：Agent
## 前置知识
<!-- 参考Agent Tutorial：https://github.com/datawhalechina/agent-tutorial -->
<!-- 参考Hugging Muti Agent：https://deepwisdom.feishu.cn/wiki/MLILw0EdRiyiYRkJLgOcskyAnUh -->

<!-- ![智能体的定义](images/agent.png) -->
MetaGPT是一个先进的多智能体框架。本教程基于MetaGPT框架实现，以下介绍该框架的基本概念及其组件，更多细节和案例请参考官方文档：https://docs.deepwisdom.ai/main/zh/guide/get_started/introduction.html 


### 异步编程
多智能体框架使用python异步编程的架构实现，因此，我们先来了解一下异步编程的概念：

异步编程就像是让餐厅的服务员能够同时照顾多位顾客，而不是一次只服务一个。在传统的同步编程中，程序就像服务员只能等待一件事情完成后才能做下一件事，这在处理网络这类需要等待的任务时会浪费时间。而异步编程让程序在等待一个任务（比如网络请求）时，可以继续做其他事情，就像服务员在等饮料时可以去收拾桌子或点餐。

Python的异步库让这种并发处理变得简单，使得编写这样的代码变得容易。这对于聊天机器人来说特别有用，因为它可以同时和多个用户聊天，而不需要等一个用户回复后再和下一个用户说话。这大大提升了效率和用户体验。

### 智能体

我们可以把智能体想象成一个人类，拥有思考、感知、记忆和行动的能力.智能体的功能可以概括为下面这个公式：
```
智能体 = 大语言模型（LLM） + 观察 + 思考 + 行动 + 记忆
```
- 大语言模型（LLM）：智能体的“大脑”，让它能理解和生成语言，学习并做出决策。
- 观察：智能体通过感知环境（如阅读文本、看图像、听声音）来获取信息。
- 思考：智能体分析观察到的信息和记忆，决定下一步怎么做。
- 行动：智能体根据思考的结果执行具体的动作，比如生成代码或网上搜索信息。
- 记忆：智能体记住过去的经历，帮助它在未来做出更好的决策。

### 多智能体
多智能体系统可以视为一个智能体社会，其中
```
多智能体 = 智能体 + 环境 + 标准流程（SOP） + 通信 + 经济
```
- 智能体：在上面单独定义的基础上，在多智能体系统中的智能体协同工作，每个智能体都具备独特有的LLM、观察、思考、行动和记忆。
- 环境：环境是智能体生存和互动的公共场所。智能体从环境中观察到重要信息，并发布行动的输出结果以供其他智能体使用。
- 标准流程（SOP）：这些是管理智能体行动和交互的既定程序，确保系统内部的有序和高效运作。例如，在汽车制造的SOP中，一个智能体焊接汽车零件，而另一个安装电缆，保持装配线的有序运作。
- 通信：通信是智能体之间信息交流的过程。它对于系统内的协作、谈判和竞争至关重要。
- 经济：这指的是多智能体环境中的价值交换系统，决定资源分配和任务优先级。


### 两个核心类
- Action：类 Action 是动作的逻辑抽象。用户可以通过简单地调用 self._aask 函数令 LLM 赋予这个动作能力，即这个函数将在底层调用 LLM api。
每个智能体可以具备多个动作，这些动作之间可以进行组合。

- Role：类 Role 是智能体的逻辑抽象。一个 Role 能执行特定的 Action，拥有记忆、思考并采用各种策略行动。基本上，它充当一个将所有这些组件联系在一起的凝聚实体。

<!-- 重新总结这段话，三个智能体各自的动作和角色分别是什么 -->
### 一个例子
下面给出一个简单的例子，展示智能体如何工作：
在这个例子中，我们有三个智能体：Alice、Bob和Charlie。每个智能体都有其独特的角色和行动，它们通过交互和协作来完成任务。
![智能体的工作示例](images/智能体的工作示例.png)

他们可以将消息或行动的输出结果发布到环境中，同时也会被其他智能体观察到。
下面将揭示智能体Charlie的内部过程，该过程同样适用于Alice和Bob。
在内部，智能体Charlie具备我们上述所介绍的部分组件，如LLM、观察、思考、行动。Charlie思考和行动的过程可以由LLM驱动，并且还能在行动的过程中使用工具。
Charlie观察来自Alice的相关文件和来自Bob的需求，获取有帮助的记忆，思考如何编写代码，执行写代码的行动，最终发布结果。
Charlie通过将结果发布到环境中以通知Bob。Bob在接收后回复了一句赞美的话。

<!-- 其中一个agent的运行示例如下：
![MetaGPT定义的Agent执行过程](MetaGPT定义的Agent执行过程.png)
- 一个agent在启动后他会观察自己能获取到的信息，加入自己的记忆中
- 下一步进行思考，决定下一步的行动，也就是从Action1，Action2，Action3中选择执行的Action
- 决定行动后，紧接着就执行对应行动，得到这个环节的结果 -->

以下总结了三个智能体的角色和动作：

| 智能体 | 角色         | 动作                                                         |
|--------|--------------|--------------------------------------------------------------|
| Alice  | 信息提供者   | 发布相关文件或数据到环境中，为任务提供必要的信息和资源。       |
| Bob    | 需求方       | 提出需求或任务，发布到环境中，等待其他智能体的响应或解决方案。 |
| Charlie| 执行者       | 观察来自Alice的文件和Bob的需求，思考并编写代码，执行任务，并将结果发布回环境中。|


## 设计思路
<!-- ToDo：画一个类似的图，说明三个Agent如何工作 -->
<!-- ![智能体的工作示例](images/智能体的工作示例.png) -->

项目的目标是创建一个能够理解和响应用户需求的智能聊天系统，通过智能体之间的协作，提供一个流畅、互动和个性化的用户体验。
这个项目的设计思路是通过创建具有特定角色和动作的智能体，并通过它们之间的有效通信来提供一个交互式的聊天体验。
项目中定义了三个主要的智能体，每个智能体都有其独特的角色和一系列动作，用于处理用户的输入并生成响应。

1. 创建智能体，定义动作和角色。
- QianBianZhe角色通过执行AnsWrite和Stylize动作，能够生成并风格化祝福文本。
- RuYi角色通过执行WriteMarkDown动作，能够生成并展示关于如何撰写祝福的思路总结。
- WenDao角色通过执行RecvAndAnalyze和RaiseQuestion动作，能够接收用户的输入，分析对话内容，并提出相关问题。

三个智能体的角色和动作总结如下：
| 智能体名称 | 角色         | 动作                           |
|------------|--------------|--------------------------------|
| QianBianZhe  | 千变者       | - AnsWrite: 给定人设并导入参考聊天话术、历史聊天语料进行聊天。 <br> - Stylize: 根据当前状态和聊天与恋爱相关性等综合打分，给出当前回合的打分情况。 |
| RuYi       | 如意         | - WriteMarkDown: 给出针对回答的知识，并用Markdown格式展示。 |
| WenDao     | 文道         | - RecvAndAnalyze: 分析用户的需求。 <br> - RaiseQuestion: 限定提问的问题。 |

2. 处理智能体之间的通信。
在本项目中，三个智能体通过共享数据和状态来进行通信和协作。每个智能体在执行其动作时，都会访问和更新共享数据，这样可以确保信息的一致性和实时性。共享数据包括用户的历史输入、智能体的响应、当前任务状态等。

3. 工作流程：
- 用户通过聊天界面输入消息。
- 根据当前的任务状态和用户的输入，智能体执行相应的动作。
- 智能体生成响应并更新共享数据。
- 响应被发送回聊天界面供用户查看。
- 智能体根据需要提出问题，进一步引导对话。

## 代码实现
在本项目中，我们使用了三个不同的智能体来与用户进行交互，提供个性化的祝福生成服务。用户通过聊天界面输入信息，智能体会根据用户提供的信息生成祝福语，并可能提供相关知识文档。

三个智能体角色的实现如下：
### 智能体 qianbianzhe
```python
# 千变者类继承自Role，表示一个能够根据给定的指令进行回答的角色。
class QianBianZhe(Role):
    # 角色的名称设置为"QianBianZhe"。
    name: str = "QianBianZhe"
    # 角色的个人资料设置为"Stylize"，这个角色在交互时会采用某种风格化的语言。
    profile: str = "Stylize"

    # 初始化方法中，设置了角色的动作列表，并指定了动作的执行顺序。
    def __init__(self, **kwargs):
        super().__init__(**kwargs)
        self._init_actions([AnsWrite, Stylize])  # 初始化动作列表，包含AnsWrite和Stylize动作。
        self._set_react_mode(react_mode=RoleReactMode.BY_ORDER.value)  # 设置动作的执行顺序。

    # 异步执行方法，用于根据当前的任务执行相应的动作。
    async def _act(self) -> Message:
        logger.info(f"{self._setting}: to do {self.rc.todo}({self.rc.todo.name})")
        # 获取当前待办任务。
        todo = self.rc.todo

        # 从记忆中获取最近的一条消息。
        msg = self.get_memories(k=1)[0]
        # 执行当前任务的动作。
        result = await todo.run(msg.content)
        # 创建一个新的消息对象，包含动作的结果和角色信息。
        msg = Message(content=result, role=self.profile, cause_by=type(todo))
        # 将新创建的消息添加到记忆中。
        self.rc.memory.add(msg)

        # 返回创建的消息对象。
        return msg
```
### 智能体 ruyi
```python
# 如意类继承自Role，表示一个能够根据给定的指令进行回答的角色。
class RuYi(Role):
    # 角色的名称设置为"RuYi"，即如意。
    name: str = "RuYi"
    profile: str = "Stylize"
    # 角色的个人资料设置为"Stylize"，这个角色在交互时会采用某种风格化的语言。

    # 初始化方法中，设置了角色的动作列表，并指定了动作的执行顺序。
    def __init__self__(**kwargs):
        super().__init__(**kwargs)
        self._init_actions([WriteMarkDown])  # 初始化动作列表，包含WriteMarkDown动作。
        self._set_react_mode(react_mode=RoleReactMode.BY_ORDER.value)  # 设置动作的执行顺序。

    # 异步执行方法，用于根据当前的任务执行相应的动作。
    async def _act(self) -> Message:
        logger.info(f"{self._setting}: to do {self.rc.todo}({self.rc.todo.name})")
        # 获取当前待办任务。
        todo = self.rc.todo

        # 从记忆中获取最近的一条消息。
        msg = self.get_memories(k=1)[0]
        # 执行当前任务的动作。
        result = await todo.run(msg.content)
        # 创建一个新的消息对象，包含动作的结果和角色信息。
        msg = Message(content=result, role=self.profile, cause_by=type(todo))
        # 将新创建的消息添加到记忆中。
        self.rc.memory.add(msg)

        # 返回创建的消息对象。
        return msg
```
### 智能体 wendao
```python
# 文道类继承自Role，表示一个能够接收信息并进行分析的角色。
class WenDao(Role):
    # 角色的名称设置为"WenDao"，即文道。
    name: str = "WenDao"
    profile: str = "GetInformation"
    # 角色的个人资料设置为"GetInformation"，表明这个角色的主要职责是获取和分析信息。

    # 初始化方法中，设置了角色的动作列表，并指定了动作的执行顺序。
    def __init__self__(**kwargs):
        super().__init__(**kwargs)
        self._init_actions([RecvAndAnalyze, RaiseQuestion])  # 初始化动作列表，包含RecvAndAnalyze和RaiseQuestion动作。
        self._set_react_mode(react_mode=RoleReactMode.BY_ORDER.value)  # 设置动作的执行顺序。

    # 异步执行方法，用于根据当前的任务执行相应的动作。
    async def _act(self) -> Message:
        logger.info(f"{self._setting}: to do {self.rc.todo}({self.rc.todo.name})")
        # 获取当前待办任务。
        todo = self.rc.todo

        # 从记忆中获取最近的一条消息。
        msg = self.get_memories(k=1)[0]
        # 执行当前任务的动作。
        result = await todo.run(msg.content)
        # 创建一个新的消息对象，包含动作的结果和角色信息。
        msg = Message(content=result, role=self.profile, cause_by=type(todo))
        # 将新创建的消息添加到记忆中。
        self.rc.memory.add(msg)
        # 返回创建的消息对象。
        return msg

    # 按顺序执行动作的方法。
    async def _act_by_order(self) -> Message:
        for i in range(len(self.states)):
            self._set_state(i)
            rsp = await self._act()
        return rsp
```

### Agent 之间的通信
三个智能体通过共享数据和任务状态来进行通信和协作。
1. 所有智能体都访问和更新同一个SharedDataSingleton实例，这是一个全局状态容器，用于存储用户输入、智能体输出和任务状态。
2. task_status变量用于控制智能体的执行顺序。WenDao首先分析用户需求，然后根据分析结果决定是否需要进一步的用户输入或直接执行QianBianZhe和RuYi智能体。
3. 智能体的动作是通过异步函数调用来执行的，这允许程序在等待一个智能体完成其任务时继续处理其他任务。
4. 智能体之间的通信是通过在共享数据中添加和读取消息来完成的。每个智能体都会读取前一个智能体留下的消息，并根据这些信息生成响应。

### 项目实现
1. 初始化环境变量和会话状态
```python
# 导入必要的库和模块
from dotenv import load_dotenv  # 用于加载环境变量
import asyncio  # 用于异步编程
import streamlit as st  # 用于创建Web应用程序的用户界面
import uuid  # 用于生成唯一标识符
from streamlit_chat import message  # 用于在Streamlit中创建聊天界面
from metagpt.logs import logger  # 用于记录日志

# 导入智能体模块
from tianji.agents.metagpt_agents.wendao import WenDao
from tianji.agents.metagpt_agents.qianbianzhe import QianBianZhe
from tianji.agents.metagpt_agents.ruyi import RuYi

# 导入共享数据和时间戳工具
from tianji.utils.json_from import SharedDataSingleton
from tianji.utils.common import timestamp_str

# 加载环境变量
load_dotenv()

# 初始化session_state变量
if "user_id" not in st.session_state:
    st.session_state["user_id"] = str(uuid.uuid4())
```

2. 设置用户交互界面
```python
# 设计思路和启动指南
startup_guide = """
...

"""

# Streamlit应用标题和Markdown展示启动指南
st.title("人情世故大模型_祝福模块")
st.markdown(startup_guide)

# 初始化会话状态中的变量
if "generated" not in st.session_state:
    st.session_state["generated"] = []
if "past" not in st.session_state:
    st.session_state["past"] = []
```

3. 异步主函数处理用户输入和智能体间的通信
```python
async def main():
    first_status_user_history = ""
    # ... 用户交互和智能体协作逻辑 ...

# 运行主函数
asyncio.run(main())
```

4. 聊天界面消息处理
```python
# 当用户输入消息时，执行以下操作
if user_input := st.chat_input():
    # 获取共享数据实例
    sharedData = SharedDataSingleton.get_instance()

    # 将用户输入添加到会话历史和共享数据中
    # ...

    # 根据任务状态，执行不同的智能体动作
    if task_status == 0:
        # 使用WenDao智能体分析用户需求
        role_wendao = WenDao()
        result = await role_wendao.run(sharedData.first_status_user_history)
        # ...

        # 如果WenDao智能体返回"NO"，则继续提示用户输入
        # ...

    # 如果任务状态为1或对话轮数超过3轮，执行QianBianZhe和RuYi智能体
    if task_status == 1 or sharedData.ask_num > 3:
        # 构建知识库查询键
        knowledge_key = json_from_data["festival"] + json_from_data["requirement"]

        # 执行QianBianZhe智能体，生成风格化的回答
        role_qianbianzhe = QianBianZhe()
        qianjibian_ans = await role_qianbianzhe.run(" ")

        # 执行RuYi智能体，生成Markdown格式的知识展示
        role_ruyi = RuYi()
        ruyi_ans = await role_ruyi.run(" ")

        # 将智能体的回答添加到会话状态和共享数据中
        # ...
```

## 实现技巧
<!-- ToDo：请教散师傅 -->

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
