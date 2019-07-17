## springboot快速入门



### springboot特点

- 为基于spring的开发提供更快速的入门体验
- 开箱即用，没有代码生成，也无需xml配置，同时也可以修改默认值来满足特定的需求
- 提供了一一些大型项目中常见的非功能性特征，如嵌入式服务器、安全、指标，健康检测、外部配置
- springboot不是对spring功能上的曾强，而是提供了一种快速使用spring的方式



### springboot的核心功能

- 起步依赖
  起步依赖本质上是一个maven项目对象模型（project object model）POM，定义了对其他库的传递依赖，这些东西加载一起即支持某项功能
  简单的说，起步依赖就是将某种功能的坐标打包到一起，并提供一些默认的功能。
- 自动配置
  springboot的自动配置是一个运行时，更准确地说，是应用程序启动时的过程，考虑了众多因素，才决定spring配置应该用哪个，不用那个。该过程是spring自动完成的





### spirngboot环境的搭建

#### 1.1 创建maven工程

#### 1.2添加springboot的起步依赖

springboot要求，项目要继承springboot的起步依赖spring-boot-starter-parent

```xml
<parent>    
    <groupId>org.springframework.boot</groupId>    
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>2.0.1.RELEASE</version>
</parent>
```

springboot要继承springmvc进行controller的开发，所以项目要导入web的启动依赖（这是一个整合的坐标，底层其实是打包spring 和 springmvc 的坐标）

```xml
<dependencies>
    <!--web功能的起步依赖-->        
    <dependency>            
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
</dependencies>
```

#### 1.3添加引导类（一般都是这样写的，但是把注解写到别的类上面也是可以的，run里面就要是那个类的字节码）

```java
//加注解把当前类定义为引导类
@SpringBootApplication
public class MySpringBootApplication {    
    public static void main(String[] args) {
        SpringApplication.run(MySpringBootApplication.class);    
     }
}
```

#### 1.4编写controller

```java
@Controllerpublic 
class QuickController {
    
    @RequestMapping("/quick")    
    @ResponseBody    
    public String quick(){        
        return "Hello SpringBoot";
    }
}
```



### springboot的热部署

```xml
<!--    热部署配置-->
    <dependency>
        <groupId>org.springframework.boot</groupId>    
        <artifactId>spring-boot-devtools</artifactId>
    </dependency>
```

idea本身不支持自动编译，需要勾选

![1563322671987](C:\Users\camus\AppData\Roaming\Typora\typora-user-images\1563322671987.png)



![1563322705191](C:\Users\camus\AppData\Roaming\Typora\typora-user-images\1563322705191.png)

