# 实现分库分表

## 配置信息

```yaml
# 多数据源路由配置
ray-db-router:
  jdbc:
    datasource:
      dbCount: 2
      tbCount: 4
      default: db00
      routerKey: uId
      list: db01,db02
      db00:
        driver-class-name: com.mysql.cj.jdbc.Driver
        url: jdbc:mysql://127.0.0.1:3306/lottery?useUnicode=true&serverTimezone=Asia/Shanghai
        username: root
        password: 123456
      db01:
        driver-class-name: com.mysql.cj.jdbc.Driver
        url: jdbc:mysql://127.0.0.1:3306/lottery_01?useUnicode=true&serverTimezone=Asia/Shanghai
        username: root
        password: 123456
      db02:
        driver-class-name: com.mysql.cj.jdbc.Driver
        url: jdbc:mysql://127.0.0.1:3306/lottery_02?useUnicode=true&serverTimezone=Asia/Shanghai
        username: root
        password: 123456
```

## 组件结构

![数据库路由组件.drawio](images/数据库路由组件.drawio.png)