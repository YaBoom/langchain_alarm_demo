# LangChain Alarm Demo

[![Python](https://img.shields.io/badge/Python-3.8+-3776AB?logo=python)](https://www.python.org/)
[![LangChain](https://img.shields.io/badge/LangChain-0.1.0-blue?logo=langchain)](https://python.langchain.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

基于LangChain的大语言模型(LLM)应用开发示例，展示如何构建复杂LLM应用，结合多种组件（Prompt、LLM、OutputParser、Tool、Agent等）来创建智能系统。

## 🚀 项目介绍

本项目演示了LangChain框架的强大功能，通过构建一个智能提醒系统，展示了如何：
- 集成大语言模型（使用通义千问）
- 构建基础chain处理自然语言查询
- 整合系统工具（bash命令）扩展LLM能力
- 创建API链来调用外部服务

## 🛠️ 技术栈

- **LangChain**: LLM应用开发框架
- **Tongyi**: 通义千问大语言模型
- **Python**: 3.8+
- **APIChain**: 用于调用外部API
- **LLMBashChain**: 用于执行bash命令

## 📋 项目结构

```
langchain_alarm_demo/
├── alarm_langchain.py    # 核心实现代码
├── README.md            # 项目说明
└── requirements.txt     # 依赖列表
```

## 🔧 安装依赖

```bash
pip install langchain langchain-community langchain-experimental
pip install openai  # 如果使用OpenAI模型
pip install tongyi  # 如果使用通义千问
```

## 🚀 快速开始

### 1. 环境配置

首先，安装所需的Python包：

```bash
pip install -r requirements.txt
```

### 2. 配置API密钥

根据您使用的LLM提供商，设置相应的环境变量：

```bash
# 通义千问
export QWEN_API_KEY="your_qwen_api_key"

# 或者 OpenAI
export OPENAI_API_KEY="your_openai_api_key"
```

### 3. 运行示例

```bash
python alarm_langchain.py
```

## 🏗️ 核心组件

### 1. Bash Chain

基础chain实现，使用bash工具处理系统命令：

```python
from langchain_experimental.llm_bash.base import LLMBashChain
from langchain_community.llms.tongyi import Tongyi

model = Tongyi(model_name="qwen-max", model_kwargs={'temperature': 0.0001})
bash_chain = LLMBashChain.from_llm(model, verbose=True)
```

### 2. Alarm Chain

整合bash chain和alarm tool的复合链：

```python
alarm_chain = {
    "context": lambda x: bash_chain.invoke(query)['answer']
} | prompt | model
```

### 3. API Chain

通过HTTP API调用外部服务的链：

- **API文档**: HTTPBin服务作为示例API
- **URL**: `http://httpbin.org/get`
- **方法**: `GET`
- **参数**: `alarm` - 提醒信息

## 🧪 使用示例

以下是如何使用本项目的示例：

```python
# 执行bash命令查询
query = "列出当前目录的文件"
result = bash_chain.invoke(query)

# 使用alarm chain
alarm_chain.invoke({})

# 调用API chain
api_chain.invoke({})
```

## 📚 学习要点

1. **Chain组合**: 如何将不同的组件链接在一起
2. **工具集成**: 如何将外部工具（bash、API）与LLM集成
3. **提示工程**: 如何设计有效的提示来指导LLM行为
4. **错误处理**: 在LLM应用中处理异常情况

## 🤝 贡献

欢迎提交Issue和Pull Request来改进此项目！

### 开发流程

1. Fork此仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送分支 (`git push origin feature/AmazingFeature`)
5. 创建Pull Request

## 📄 许可证

本项目采用 [MIT License](LICENSE) 许可证。

## 📞 支持

如果您有任何问题，请通过以下方式联系：

- 提交 [GitHub Issue](https://github.com/YaBoom/langchain_alarm_demo/issues)
- 发送邮件至: [your-email@example.com]

## 🙏 致谢

- 感谢 [LangChain](https://python.langchain.com/) 提供的优秀框架
- 感谢 [通义千问](https://www.aliyun.com/product/dashscope) 提供的LLM能力
- 感谢 [HTTPBin](https://httpbin.org/) 提供的API测试服务

---

⭐ 如果这个项目对你有帮助，请给一个Star！