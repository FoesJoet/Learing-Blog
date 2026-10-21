# 重拾Java开发之路（1）

## Java是什么

Java之父是SUN公司的高司令，其主要是分为SE、EE以及ME。

当前主要讨论的是JavaEE这一块，也就是国内互联网公司主要使用的后端技术。

###互联网主力军？还是49年入国军？

当前AI的快速冲击让笔者不知所措，AI时代，抽干了互联网的潮水，让无数人裸泳。笔者不想追问 学习Java的意义，我只是不想让我这一年的努力化为泡影，因此写下下面的东西。

### 每一个Javaer必备的IDEA

只要用Java就不可能没听过IDEA，作为目前编程抑或是调试最好用的IDE，所有Java使用者都应该学习他的用法。由于本专栏不面向小白，而是对进行一个快速的回顾，所以希望大家自行学习。

### Maven

Java的包管理器和构建器。

Java不像Python，不编译只要解释器，也不像C，编译好了就可以直接运行，Java编译的字节码文件必须借助JVM才能运行。

导入的依赖必须管里，不然早晚混乱不堪。

文件也需要分门别类否则难以管理。

为了提效和便于管理-->标准化-->Maven、

Maven提供了一套标准的项目结构，构建流程，依赖管理机制，保证不同项目之间的标准化流程一致且易于管理。

####项目结构

![image-20261021140135105](C:\Users\Foes\AppData\Roaming\Typora\typora-user-images\image-20261021140135105.png)

其中pom.xml是Mvn配置文件，记载了各类依赖组件的配置信息，主要的内容存放在main/java，相应的Java文件用到的资源文件放在resources下，例如静态页面，和一些对应配置，对项目进行编译构建之后得到的内容就存放在target中。

这是单模块情况下，如果引入多模块

![image-20261021142959235](C:\Users\Foes\AppData\Roaming\Typora\typora-user-images\image-20261021142959235.png)

会将模块共有依赖抽取出来，形成parent模块的xml文件。

#### 依赖管理

Java开发如果只用JDK提供的包，失去了Java的所有魅力，因为Java最好的点就在于其超级的社区底蕴与标准化。但是如果要依赖第三方的包，自行管理会有很多问题，比如前置依赖缺失、以及繁琐的依赖查找过程。
但是如果使用Maven就没有这样的问题，Maven可以自行进行前置依赖的补全。

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
    <version>1.4.2.RELEASE</version>
</dependency>
```

引入这样的复杂依赖，如果手工引入，不知道要引入多少前置或者相关依赖。

![image-20261021141900664](C:\Users\Foes\AppData\Roaming\Typora\typora-user-images\image-20261021141900664.png)

上图为依赖的生命周期，了解即可。

#### 项目构建

Mvn将Java项目的构建整理成生命周期，有很多不同的phase，但是对于大部分phase都无需了解，只需知道

```
package(打包)\clean（清理）\compile（编译）\test（测试）
```

主要使用方法是以下几个命令
```bash
mvn clean
mvn clean package
mvn clean complie
mvm clean test
```

该命令的主要作用会让Mvn的生命周期执行从default到当前命令这一步，其他时候如果需要用到MVN命令，我只能说善用AI。

##### 写在最后

如果导入项目到IDEA之后，发现其没法进行使用mvn，将Pom.xml选中后右键添加Maven即可。
