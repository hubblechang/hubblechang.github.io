---
title: Spring
categories: 
- Spring
---
# Spring和SpringBoot
> Spring引入了依赖注入和面向切面编程，虽然组件代码是轻量级的，但是配置是重量级的（需要大量的XML配置）。在开启某些Spring特性时，比如事务管理和Spring MVC还是需要使用XML或者Java进行显示配置。大量XML的配置使得开发不便，同时，相关库的依赖没有集中管理，使得版本冲突经常出现。

> SpringBoot为了简化Spring开发而生，减少了配置文件。
Spring的主要优点包括：
1. 简化基于Spring应用程序的开发。
2. 无需编写大量样板代码、XML配置和注释
3. 可以很容易与Spring生态集成，如Spring JDBC、Spring Data
4. SpringBoot遵循固执己见的默认配置，减少开发工作
5. SpringBoot提供嵌入式HTTP服务器，包含Tomcat和Jetty
6. SpringBoot提供命令行接口，可用于开发和测试

# @SpringBootApplication 注解

`@SpringBootApplication`看作是 `@Configuration`、`@EnableAutoConfiguration`、`@ComponentScan`

+ `@EnableAutoConfiguration`：启用 SpringBoot 的<b>自动配置</b>机制。

> 通过分析类路径中的依赖和配置文件中的属性，自动为应用程序配置各种组件和设置，减少手动配置的工作量。

+ `@ComponentScan`： <b>组件扫描</b>，扫描被@Component (@Service,@Controller)注解的 bean，注解默认会扫描该类所在的包下所有的类。

>允许Spring自动发现和注册应用程序中的组件，简化Bean的注册和管理过程。

+ `@Configuration`：允许在上下文中注册额外的 bean 或导入其他配置类

# 使用 SpringBoot 实现全局异常处理
SpringBoot 应用程序可以借助 `@RestControllerAdvice` 和 `@ExceptionHandler` 实现全局统一异常处理。

