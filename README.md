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

