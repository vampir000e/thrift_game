## Linux learning——thrift

<br>使用thrift实现游戏匹配机制，该应用的不同微服务分配到不同服务器上，各端使用不同语言实现

<br>thrift/多线程/消息队列/微服务/生产者-消费者模型/cpp/python

### 图示

![image](https://user-images.githubusercontent.com/49400104/160067216-43f7e998-4aed-45d8-9b88-89cb23338406.png)


###  文件结构

![image](https://user-images.githubusercontent.com/49400104/160064729-3a5398ea-7107-4d15-9e84-ef867f40f0ca.png)

1. thrift
   <br>match.thrift 定义匹配接口
   <br>save.thrift 定义数据存储接口
2. game
  <br>游戏端，也是匹配客户端match_client
  <br>client.py业务逻辑
3. match_system
  <br>匹配系统，是匹配服务端match_server，同时也是数据存储客户端save_client
  <br>main.cpp业务逻辑
  
 ### 版本更新
 对匹配机制逐步完善
 <br> match-server: 无实际操作，只打印
 <br> match-server2.0: 每次match匹配池中的前两个人
 <br> match-server3.0: 考虑匹配的合理性，将分值差50以内的玩家匹配在一起，每1秒检测一次
 <br> match-server4.0: 改为多线程，每次匹配新开一线程
 <br> match-server5.0: 随着玩家等待时间的增加，可匹配玩家的范围应该拓宽。如果匹配池中有2个以上玩家但分数差>50，而已经等待已久，这种情况应当匹配。
 
