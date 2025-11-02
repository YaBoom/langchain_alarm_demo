# langchain_base_demo

#### 介绍
针对langchain框架集成通义大模型实现聊天机器人的demo实例以及Langchain的LCEL表达式执行chain等应用功能

#### 功能说明
1 通过bash_chain实现查询操作系统的所有磁盘使用情况
2 通过alarm_chain 结合bash_chain查询到的磁盘使用情况判断是否需要告警
3 通过alarm_api_chain 结合alarm_chain的是否告警的结果来判断，如果需要告警,通过HTTP API发送告警。

