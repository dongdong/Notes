# Redis开发与运维

### 1. 初识Redis

##### Redis特性

- 数据结构
    * 基础：字符串，哈希，列表，集合，有序集合
    * 扩展：位图（Bitmaps），HyperLogLog
    * 新增：地理位置信息GEO
    

- 功能
  * 键过期功能，实现缓存
  * 发布订阅功能，实现消息系统
  * lua脚本，创造新命令
  * 简单的事务功能
  * pipeline流水线功能，将一批命令一次性传到Redis
  

- 高可用和分布式
  * 持久化：RDB，AOF
  * 主从复制
  * Redis Sentinel，故障发现，故障转移 
  * Redis cluster
  

##### Redis使用

- 使用场景
  * 缓存
  * 排行榜系统
  * 计数器
  

- Reids命令
  ```
  $ redis-server #启动redis，默认配置
  $ redis-server --port 6380 #启动redis，参数配置
  $ redis-server redis.conf #启动redis，配置文件
  $ redis-cli -h 127.0.0.1 -p 6379 #启动客户端
  $ redis-cli -h 127.0.0.1 -p 6379 get hello #命令
  $ redis-cli shutdown [save|nosave] #停止服务
  ```

### 2. API的理解和使用

- 全局命令
  ```
  keys #查看所有键
  dbsize #键总数
  exists key #键是否存在
  del key [key ...] #删除键，返回成功删除个数
  expire key seconds #键过期
  ttl key #查看键的剩余过期时间，-1：没设置，-2：不存在
  type key #键的数据结构类型，string，hash，list，set，zset
  ```
  * dbsize时间复杂度O(1)，keys时间复杂度O(n)


- 数据结构和内部编码

  
  
