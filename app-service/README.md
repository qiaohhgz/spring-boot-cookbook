Service 层：相对具体的业务逻辑服务层。

一个Service涉及到复杂算法时，如果通过DAO层导致逻辑不清晰  
可通过manager层来解耦    
相关算法内聚在manager层   


异常处理策略及日志规约：  
在 Service 层出现异常时，必须记录出错日志到磁盘，尽可能带上参数信息，相当于保护案发现场。
