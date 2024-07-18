# Rasp-Agent
基于传统RASP的设计思想，自定义实现的java-agent探针，可及时拦截大部分漏洞攻击并返回调用栈信息
## 背景
为了深刻理解RASP以及java agent插桩技术
## 版本
编译运行等都使用 8u65 版本
## 基本使用
可在程序运行前以及程序运行过程中加载rasp-agent探针
### 运行前
将我们的jar包放入指定目录，在VM选项中加入相关配置：-javaagent:target\out\java_agent.jar
运行程序即可成功加载
![图片](https://github.com/user-attachments/assets/143e4da7-0000-46f4-9f83-8169114eca0d)
### 运行中
jps -l 获取程序进程ID

    `public static void main(String[] args) throws IOException, AttachNotSupportedException, AgentLoadException, AgentInitializationException {
        VirtualMachine target = VirtualMachine.attach("29180");
        target.loadAgent("D:\\Study_Project\\agentproject\\target\\agentproject-1.0-SNAPSHOT-jar-with-dependencies.jar");
        target.detach();
    }`

使用如下代码远程加载
![图片](https://github.com/user-attachments/assets/1a527216-047b-4089-bd62-06134d5dd655)
## 部分截图
分享几个攻击失败的截图和一些日志输出的截图
1.sql注入
攻击不成功如下：
![图片](https://github.com/user-attachments/assets/5693ccbd-4dff-468b-87fc-47c96eca1ffc)
后台日志输出如下：
![图片](https://github.com/user-attachments/assets/56b16361-a754-4592-a039-fbb776340144)

2.xxe实体注入
攻击失败如下：
![图片](https://github.com/user-attachments/assets/97293932-cde1-477d-909d-9e8cbaca285f)
后台日志输出如下：
![图片](https://github.com/user-attachments/assets/53ad8cfa-123d-4219-963c-b71c5be0a0ad)

等等。。。

## 不足
编写代码过程中测试项目为开源的java_sec_code，缺少大量的测试数据，以及需要hook的类方法不全，拦截代码对程序的影响等等。

## 最后
该java-agent探针目前只能当作一个小玩具，还需要长时间持续的改进和优化，以后会应用到更多项目中测试效果，也希望师傅们能玩玩这个小玩具，非常感谢能够为我收获一些宝贵的意见。最后也希望师傅们能点一个小小的star~




