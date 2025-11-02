# langchain_base_demo

#### 介绍
针对langchain框架的LLMS模型接口,结合Langchain多个模块，快速实现磁盘监控以及监控告警功能的实用工具。 
#### 功能说明
1 通过bash_chain实现查询操作系统的所有磁盘使用情况
2 通过alarm_chain 结合bash_chain查询到的磁盘使用情况判断是否需要告警
3 通过alarm_api_chain 结合alarm_chain的是否告警的结果来判断，如果需要告警,通过HTTP API发送告警。

