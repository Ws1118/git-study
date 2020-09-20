# Java Web开发

## 八步掌握Java Web开发技术

![image-20200920153519392](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920153519392.png)

### 1.选题，需求分析，架构设计

- 使用“经典的”三层架构开发Web应用：<img src="C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920153735491.png" alt="image-20200920153735491" style="zoom: 67%;" />

- 理解“层”与“组件”之间的关系：

<img src="C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920153910114.png" alt="image-20200920153910114" style="zoom: 67%;" />

- Web应用的开发流程：①需求分析→②架构设计→③开发测试→④上线部署→反馈与迭代（返回①）

  - 需求分析阶段要完成的主要工作
    - 确定能使用网站的用户类型及相关的权限
    - 确定系统应该实现哪些功能，涉及哪些数据，这
      些数据又是如何被加工和处理的
    - 确定系统中应该有哪些领域对象，这些对象相互
      协作完成特定的系统功能（需求分析阶段，不要考虑具体技术，分析得到的对象，称为“（业务）领域对象（Domain Object）”，不是Java对象。它们是诸如“订单”、“用户”等真实世界中的事物。）

  - 架构设计阶段要完成的任务（当前Web应用最常用的架构是组件化的分层架构。）
    - 从业务功能上进行划分，确定整个系统可以划分为
      多少个子系统，每个子系统可以再用分层架构实现
    - 每个子系统的每一层中，有几个包（package），
      每个包中放哪些类，每个类承担职责是什么？
    - 网站需要依赖于哪些第三方组件（即外部jar包），
      自己生成哪些jar包，如何部署？

  - 开发测试![image-20200920160346197](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920160346197.png)
  - 使用Spring全家桶开发移动互联应用![image-20200920160542677](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920160542677.png)

### 2.扫清学习障碍![image-20200920160822365](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920160822365.png)

![image-20200920160932836](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920160932836.png)

![image-20200920161358968](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920161358968.png)

![image-20200920161422217](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920161422217.png)

![image-20200920161447468](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920161447468.png)

![image-20200920161505708](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920161505708.png)

![image-20200920161520705](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920161520705.png)

- Docker的HelloWorld流程与学习资源

  用Spring Boot写一个Web项目——→创建一个Docker镜像，集成Web项目所需的所有外部依赖，比如数据库、第三方组件等——→将Docker镜像部署到一台Linux服务器上，并启动一个容器，验证其工作正常，外部可以访问到这个网站

[GitBook]https://www.gitbook.com/book/yeasy/docker_practice/details

### 3.学习与掌握Spring Framework

（Spring Framework是Spring技术大厦的基石）

- ![image-20200920162306796](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920162306796.png)

  Spring Framework的主要学习内容：①Spring Beans与依赖注入（学习的重点）②Spring测试（最初学习技术时可跳过，开发个人项目时要补上）③面向切面编程（AOP）（初学可跳过，日后需要
  时再补上）![image-20200920162603259](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920162603259.png)

  ![image-20200920162628152](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920162628152.png)

### 4.Spring数据存取技术的学习

- 了解Spring数据存取技术：Spring Data是一个“伞型项目（umbrella project）”，“罩着”下面N个子项目
- 选择数据存储技术的基本原则（在不同的场景、不同类型的数据，应该采用不同的数据存储方式）<img src="C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920163025376.png" alt="image-20200920163025376" style="zoom:80%;" />

- 初学阶段的学习路线![image-20200920163059590](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920163059590.png)

- 实战：对Web应用进行数据分析
  - 每个Web应用都需要存储和处理相应的数据，将这些数据识别出来，并抽象为数据实体类，通常是开发一个网站一开始就要干的几件事情之一。![image-20200920163429122](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920163429122.png)
  - 实战：一对多关联的实现![image-20200920163502306](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920163502306.png)
  - 学习：Repository编程套路（Repository的数据可以来自数据库文件或内存中的对象集合，它的功能通常以接口形式表达。）![image-20200920163552990](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920163552990.png)
  - 实战：使用Repository访问数据![image-20200920163623959](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920163623959.png)
  - 学习：Repository如何存取数据![image-20200920163642971](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920163642971.png)
  - Spring Web网站业务逻辑层的编程套路![image-20200920163725532](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920163725532.png)
  - 实战：使用Spring的IoC容器完成对象的自动装配![image-20200920163801659](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920163801659.png)

### 5.Spring Boot Web开发框架

（Spring MVC是构建表示层的最常用技术)

- Spring MVC中各组件之间的协作关系：

  - 用户发来一个HTTP请求,Spring MVC框架会实例化一个控制器，并调用它的相应方法来响应这个请求。
  - 控制器对象调用业务逻辑层提供的Service组件去完成相应的数据处理工作，将结果封装为Model对象。

  - Spring MVC从Model对象中提取数据，以View为模板生成HTML代码，然后发回给客户端。<img src="C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920164318599.png" alt="image-20200920164318599" style="zoom:50%;" />

- 现实中“前后端分离”的移动互联应用（使用Spring MVC）![image-20200920164357134](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920164357134.png)
- Spring MVC学习注意事项
  - 以学习开发RESTful Service为重点
  - 掌握RESTful Service的通用编程模式
  - 没必要学习MVC的异步处理特性
  - 注意掌握实现数据校验的方法

- 实战：Spring MVC中实现服务端数据校验的编程套路

  当数据校验失败时，普通的MVC控制器（@Controller），通常会显示出错信息给用户，Web API控制器（@RestController）通常会返回诸如400之类的响应码，附加上相应的出错信息给客户端。![image-20200920164534481](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920164534481.png)

### 6.使用Spring Security构建安全的系统

（安全是绕不开的话题）

![image-20200920164648981](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920164648981.png)

- Spring Security学习建议：
  - 了解清楚其默认处理机制是学习的起点
  - 学习摊子不要铺得太开
  - 一定要啃官方文档

### 7.组合现有技术，构建个人项目

（软件开发，就是一个组合与装配的过程）![image-20200920164918209](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920164918209.png)

集成到个人项目中的代码，应该代表了你目前能达到的最高水平。要把你的个人项目当作一个艺术品那样打磨。

### 8、重构、打磨、演化

（传统Web应用→Reactive改造→微服务）![image-20200920165135327](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920165135327.png)

- 个人项目的“Reactive”式重构
  - 非阻塞的（non-blocking）
  - 异步的（asynchronous）
  - 事件驱动的（event driven）![image-20200920165239789](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920165239789.png)

- Spring Boot 2.0中两个技术栈的适用场景
  - Servlet Stack：开发传统移动互联应用：①MVC应用；②单页面应用（SPA）
  - Reactive Stack：开发“现代风格”的移动互联应用：①高并发的高性能Web应用；②（单个）微服务

- Reactive Stack学习指南![qq_pic_merged_1600592233774](C:\Users\dell\Documents\Tencent Files\2865094521\FileRecv\MobileFile\qq_pic_merged_1600592233774.jpg)

- Spring Boot Reactive Web开发技术主要学习内容
  - Reactor框架（Mono和Flux）
  - Spring Boot WebFlux
  - Spring Reactive Database（MongoDB, Redis）

- 最后一步：个人项目的“微服务”改造![image-20200920165841851](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200920165841851.png)

  