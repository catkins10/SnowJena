# :gift_heart:SnowJena

<img src="https://img.shields.io/badge/Language-Java8-green.svg" referrerPolicy="no-referrer"/><img src="https://img.shields.io/badge/Maven-3-green.svg" referrerPolicy="no-referrer"/><img src="https://img.shields.io/badge/License-Apache2.0-green.svg" referrerPolicy="no-referrer"/>

## What

基于令牌桶算法实现的分布式无锁限流框架，支持熔断降级，支持动态配置规则，支持可视化监控，开箱即用。

## Document

使用文档：[中文](./CN_README.md)|[English](./EN_README.md)

## 功能概要

| 限流   | 熔断   | 降级   | 监控   | 注解   |
| ------ | ------ | ------ | ------ | ------ |
| 黑名单 | 白名单 | 控制台 | 分布式 | 高可用 |

## 设计模式

| 单例模式 | 观察者模式 | 工厂模式   | 建造者模式 | MVC模式 |
| -------- | ---------- | ---------- | ---------- | ------- |
| 全局配置 | 动态规则   | 生产限流器 | 限流规则   | 控制台  |


# Quick Start

## Maven

```xml
<dependency>
  <groupId>cn.yueshutong</groupId>
  <artifactId>snowjena-core</artifactId>
  <version>3.0.0.RELEASE</version>
</dependency>
```

## 本地限流

```java
public class AppTest {
    Logger logger = LoggerFactory.getLogger(getClass());

    /**
     * 本地限流
     */
    @Test
    public void test1() {
        // 1.配置规则
        RateLimiterRule rateLimiterRule = new RateLimiterRuleBuilder()
                .setLimit(1)
                .setPeriod(1)
                .setUnit(TimeUnit.SECONDS) //每秒令牌数为1
                .build();
        // 2.工厂模式生产限流器
        RateLimiter limiter = RateLimiterFactory.of(rateLimiterRule);
        // 3.使用
        while (true) {
            if (limiter.tryAcquire()) {
                logger.info("ok");
            }
        }
    }

}
```


# About

Blog：<https://yueshutong.cnblogs.com/>

Email：[yster@foxmail.com](mailto:yster@foxmail.com)

Github：<https://github.com/yueshutong/SnowJena>

Gitee：<https://gitee.com/zyzpp/SnowJena>

交流QQ群：781927207

如果帮助到你了，请不吝赞赏！谢谢！

<img src="https://user-images.githubusercontent.com/31175877/67548917-af6d1600-f735-11e9-9807-351e6a2db269.png" width="300px" referrerpolicy="no-referrer">

<img src="https://user-images.githubusercontent.com/31175877/67549023-e17e7800-f735-11e9-89d4-5ca7dac0486d.png" width="300px" referrerpolicy="no-referrer">
