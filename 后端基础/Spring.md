# Sfring

## **1、spring是什么：**

  - ### Spring是一个轻量级的**控制反转(*IoC*)**和**面向切面(*AOP*)**的容器（框架）。

       - 控制反转：通过**描述（XML或注解）**并**通过第三方去生产或获取特定对象的方式**。在Spring中实现控制反转的是IoC容器，其实现方法是依赖注入（Dependency Injection,DI）。
       - 面向切边：在**一类业务**里面，横向的增加新功能而**不改变原有代码**。

   - ### spring容器特点：

     - 把**对象交给容器**管理，不需要我们自己去new。
     - 其配置文件可以**集合mybatis的配置**文件，把sqlsession等mybatis对象收入spring容器中。

## 2、spring基本代码：

 1. 构建空的maven项目，dom导入依赖，删除掉src目录，再构建模块。

    ```xml
    <dependencies>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-webmvc</artifactId>
            <version>5.2.0.RELEASE</version>
        </dependency>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
        </dependency>
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <version>1.18.12</version>
        </dependency>
    </dependencies>
    ```

 2. 在resources目录下构造spring配置文件‘ContextApplication.xml’:

     ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <beans xmlns="http://www.springframework.org/schema/beans"
           xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:schemaLocation="http://www.springframework.org/schema/beans
           http://www.springframework.org/schema/beans/spring-beans.xsd">
    </beans>
    ```

	3. bean的配置：

    ```xml
    <!--
       id 是bean的标识符,要唯一,如果没有配置id,name就是默认标识符
       如果配置id,又配置了name,那么name是别名
       name可以设置多个别名,可以用逗号,分号,空格隔开
       如果不配置id和name,可以根据applicationContext.getBean(.class)获取对象;
       class是bean的全限定名=包名+类名,需要用双引号括起来
    -->
    <bean id="hello" name="hello2 h2,h3;h4" class="com.kuang.pojo.Hello">
       <property name="name" value="Spring"/>
    </bean>
    ```

	4. spring配置文件的导入：

    ```java
    <import resource="{path}/beans.xml"/>
    ```

​    5. 调用ioc容器及其中的bean对象：

```xml
//调用spring配置文件new出context
ApplicationContext context = new ClassPathXmlApplicationContext("beans.xml");
User user = context.getBean("user",User.class);
//调用对象的方法 .
user.show();
```

## 3、依赖注入：

 1. 依赖注入是什么：

     	1. 依赖： Bean对象的依赖资源 .
      
2. 注入：由容器来设置和装配 .
	
2. 怎么注入：
   
    	1. set注入：
    
   条件：对象的属性有对应的 set方法,set方法的方法名由set + 属性首字母大写 , 如果属性是boolean类型 , 没有set方法 , 是 is .
   
        ```xml
        <property name="set后面的名字" ref="引用的另外一个bean"/>
        <property name="set后面的名字" value="基本数据值"/>
   ```
    
    	2. 构造器注入：
     
   条件：有对应的有参构造器
     
        ```xml
        <!-- 第一种根据index参数下标设置 -->
        <bean id="userT" class="com.kuang.pojo.UserT">
           <!-- index指构造方法 , 下标从0开始 -->
           <constructor-arg index="0" value="kuangshen2"/>
        </bean>
        <!-- 第二种根据参数名字设置 -->
        <bean id="userT" class="com.kuang.pojo.UserT">
           <!-- name指参数名 -->
           <constructor-arg name="name" value="kuangshen2"/>
        </bean>
        <!-- 第三种根据参数类型设置 -->
        <bean id="userT" class="com.kuang.pojo.UserT">
           <constructor-arg type="java.lang.String" value="kuangshen2"/>
        </bean>
   ```
   
    	3. 属性直接注入：（不通过构造器和set方法）
    	  
    	1. **常量注入**
    	   
    	     ```xml
    	     <property name="普通数据类型" value="值"/>
    	     ```
    	
    	```
    	  
    	2. **Bean注入** 
    	  
    	     ```xml
    	     <bean id="addr" class="com.kuang.pojo.Address">
    	          <property name="address" value="重庆"/>
    	      </bean>
    	      
    	      <bean id="student" class="com.kuang.pojo.Student">
    	          <property name="name" value="小明"/>
    	          <property name="address" ref="addr"/>
    	      </bean>
    	```
    	  
    	3. **数组注入**
    	  
    	     ```xml
    	     <property name="books">
    	          <array>
    	              <value>西游记</value>
    	              <value>红楼梦</value>
    	              <value>水浒传</value>
    	          </array>
    	      </property>
    	```
    	  
    	4. **List注入**
    	  
    	     ```xml
    	     <list>
    	          <value>听歌</value>
    	          <value>看电影</value>
    	          <value>爬山</value>
    	      </list>
    	```
    	  
    	5. **Map注入**
    	  
    	     ```xml
    	     <map>
    	         <entry key="" value=""></entry>
    	     </map>  
    	```
    	  
    	6. **set注入**
    	  
    	     ```xml
    	     <property name="games">
    	          <set>
    	              <value>LOL</value>
    	          </set>
    	      </property>
    	```
    	  
    	7. **Null注入**
    	  
    	     ```xml
    	      <property name="wife"><null/></property>
    	```
    	  
    	8. **Properties注入**
    	  
    	     ```
    	      <property name="info">
    	          <props>
    	              <prop key="学号">20190604</prop>
    	              <prop key="性别">男</prop>
    	              <prop key="姓名">小明</prop>
    	          </props>
    	      </property>
    	     ```

## 4、自动装配：

 1. 什么是自动装配：

     	1. spring会在应用上下文中为某个bean寻找其依赖的bean。

	2. 三种装配机制：

        	1. 在xml中显式配置；（最不推荐）
                  	2. 在java中显式配置；（注解）
                	3. 隐式的bean发现机制和自动装配。（重点讲解）

	3. 在xml中显式配置：

        	1. **autowire byName (按名称自动装配)**

        - 修改bean配置，增加一个属性  autowire="byName"

          ```xml
          <bean id="user" class="com.kuang.pojo.User" autowire="byName">
             <property name="str" value="qinjiang"/>
          </bean>
          ```

        - **小结：**当一个bean节点带有 autowire byName的属性时。

          1. 将查找其类中所有的set方法名，例如setCat，获得将set去掉并且首字母小写的字符串，即cat。
          2. 去spring容器中寻找是否有此字符串名称id的对象。
          3. 如果有，就取出注入；如果没有，就报空指针异常。

        	2. **autowire byType(按类型自动装配)**

        - 使用autowire byType首先需要保证：同一类型的对象，在spring容器中唯一。如果不唯一，会报不唯一的异常。

	4. 在java中显式配置；（注解）

        	1. 准备工作：

        - 在spring配置文件中引入context文件头

        - ```xml
          xmlns:context="http://www.springframework.org/schema/context"
          http://www.springframework.org/schema/context
          http://www.springframework.org/schema/context/spring-context.xsd
          ```

        	2. 开启属性注解支持：

        ```xml、
        <context:annotation-config/>
        ```

        	3. #### @Autowired

        - @Autowired是按类型自动转配的，不支持id匹配。
        - 需要导入 spring-aop的包！
        - 写在需要自动配置的属性的上一行

        #### @Qualifier

        	- 与autowired搭配使用，不可单独使用，可以根据byName的方式自动装配

        #### @Resource（java的方法）

        	- @Resource如有指定的name属性，先按该属性进行byName方式查找装配；
        - 其次再进行默认的byName方式进行装配；
        - 如果以上都不成功，则按byType的方式自动装配。
        - 都不成功，则报异常。

        **小结：**

        @Autowired与@Resource异同：

        1、@Autowired与@Resource都可以用来装配bean。都可以写在字段上，或写在setter方法上。

        2、@Autowired默认按类型装配（属于spring规范），默认情况下必须要求依赖对象必须存在，如果要允许null 值，可以设置它的required属性为false，如：@Autowired(required=false) ，如果我们想使用名称装配可以结合@Qualifier注解进行使用

        3、@Resource（属于J2EE复返），默认按照名称进行装配，名称可以通过name属性进行指定。如果没有指定name属性，当注解写在字段上时，默认取字段名进行按照名称查找，如果注解写在setter方法上默认取属性名进行装配。当找不到与名称匹配的bean时才按照类型进行装配。但是需要注意的是，如果name属性一旦指定，就只会按照名称进行装配。

        它们的作用相同都是用注解方式注入对象，但执行顺序不同。@Autowired先byType，@Resource先byName。

## 5、spring使用注解开发

> 环境准备：

需要先引入aop包（在先前引入的spring依赖中已有）

引入一个context约束（idea在使用context方法时自动会引入）

> Bean的实现：

说明：我们之前都是使用 bean 的标签进行bean注入，但是实际开发中，我们一般都会使用注解！

1、配置扫描哪些包下的注解

```
<!--指定注解扫描包-->
<context:component-scan base-package="com.kuang.pojo"/>
```

2、在指定包下编写类，增加注解

```
@Component("user")
// 相当于配置文件中 <bean id="user" class="当前注解的类"/>
public class User {
   public String name = "秦疆";
}
```

3、测试

```
@Test
public void test(){
   ApplicationContext applicationContext =
       new ClassPathXmlApplicationContext("beans.xml");
   User user = (User) applicationContext.getBean("user");
   System.out.println(user.name);
}
```



> 属性注入

使用注解注入属性

1、可以不用提供set方法，直接在直接名上添加@value("值")

```
@Component("user")
// 相当于配置文件中 <bean id="user" class="当前注解的类"/>
public class User {
   @Value("秦疆")
   // 相当于配置文件中 <property name="name" value="秦疆"/>
   public String name;
}
```

2、如果提供了set方法，在set方法上添加@value("值");

```
@Component("user")
public class User {

   public String name;

   @Value("秦疆")
   public void setName(String name) {
       this.name = name;
  }
}
```

> 小结

**XML与注解比较**

- XML可以适用任何场景 ，结构清晰，维护方便
- 注解不是自己提供的类使用不了，开发简单方便

**xml与注解整合开发** ：推荐最佳实践

- xml管理Bean
- 注解完成属性注入
- 使用过程中， 可以不用扫描，扫描是为了类上的注解

```
<context:annotation-config/>  
```

作用：

- 进行注解驱动注册，从而使注解生效
- 用于激活那些已经在spring容器里注册过的bean上面的注解，也就是显示的向Spring注册
- 如果不扫描包，就需要手动配置bean
- 如果不加注解驱动，则注入的值为null！

> 基于Java类进行配置

JavaConfig 原来是 Spring 的一个子项目，它通过 Java 类的方式提供 Bean 的定义信息，在 Spring4 的版本， JavaConfig 已正式成为 Spring4 的核心功能 。

测试：

1、编写一个实体类，Dog

```
@Component  //将这个类标注为Spring的一个组件，放到容器中！
public class Dog {
   public String name = "dog";
}
```

2、新建一个config配置包，编写一个MyConfig配置类

```
@Configuration  //代表这是一个配置类
public class MyConfig {

   @Bean //通过方法注册一个bean，这里的返回值就Bean的类型，方法名就是bean的id！
   public Dog dog(){
       return new Dog();
  }

}
```

3、测试

```
@Test
public void test2(){
   ApplicationContext applicationContext =
           new AnnotationConfigApplicationContext(MyConfig.class);
   Dog dog = (Dog) applicationContext.getBean("dog");
   System.out.println(dog.name);
}
```

4、成功输出结果！

说明：@Import(MyConfig2.class)  //导入合并其他配置类，类似于配置文件中的 inculde 标签

## 6、代理模式：

### 1、静态代理

​	问题引入：假设现在项目经理有一个需求：在项目现有所有类的方法前后打印日志。

​						你如何在**不修改已有代码的前提下**，完成这个需求？

1.为现有的每一个类都编写一个**对应的**代理类，并且让它实现和目标类相同的接口（假设都有）

<img src="https://pic4.zhimg.com/80/v2-001c5db900d8785d47c1a5a0c6f32762_1440w.jpg?source=1940ef5c" alt="img" style="zoom:150%;" />

2.在创建代理对象时，通过构造器塞入一个目标对象，然后在代理对象的方法内部调用目标对象同名方法，并在调用前后打印日志。也就是说，**代理对象 = 增强代码 + 目标对象（原对象）**。有了代理对象后，就不用原对象了

<img src="https://pic3.zhimg.com/80/v2-e302487f952bdf8e284afc0d8d6a770b_1440w.jpg?source=1940ef5c" alt="img" style="zoom:150%;" />

> 静态代理的缺陷：

程序员要手动为每一个目标类编写对应的代理类。如果当前系统已经有成百上千个类，工作量太大了。所以，现在我们的努力方向是：如何少写或者不写代理类，却能完成代理功能？

### **2、复习对象的创建**

很多初学Java的朋友眼中创建对象的过程：<img src="https://pic2.zhimg.com/80/v2-9cd31ab516bd967e1b8e68736931f8ba_1440w.jpg?source=1940ef5c" alt="img" style="zoom:150%;" />

反射下的对象创建：

​	![img](https://pic1.zhimg.com/80/v2-eddc430b991c58039dfc79dd6f3139cc_1440w.jpg?source=1940ef5c)

11Class对象包含了一个类的所有信息，比如构造器、方法、字段等。如果我们不写代理类，这些信息从哪获取呢？苦思冥想，突然灵光一现：代理类和目标类理应实现同一组接口。**之所以实现相同接口，是为了尽可能保证代理对象的内部结构和目标对象一致，这样我们对代理对象的操作最终都可以转移到目标对象身上，代理对象只需专注于增强代码的编写。**

**希望可以通过接口直接得到代理对象------问题：接口无法自己创建对象！**

### 		3、动态代理

动态代理相关的类和方法：java.lang.reflect.InvocationHandler接口和 java.lang.reflect.Proxy类，这两个类相互配合，入口是Proxy，所以我们先聊它。

Proxy有个静态方法：getProxyClass(ClassLoader, interfaces)，只要你给它传入类加载器和一组接口，它就给你返回代理Class对象。

用通俗的话说，**getProxyClass()这个方法，会从你传入的接口Class中，“拷贝”类结构信息到一个新的Class对象中，但新的Class对象带有构造器，是可以创建对象的。**打个比方，一个大内太监（接口Class），空有一身武艺（类信息），但是无法传给后人。现在江湖上有个妙手神医（Proxy类），发明了克隆大法（getProxyClass），不仅能克隆太监的一身武艺，还保留了小DD（构造器）...（这到底是道德の沦丧，还是人性的扭曲，欢迎走进动态代理）

**所以，一旦我们明确接口，完全可以通过接口的Class对象，创建一个代理Class，通过代理Class即可创建代理对象。**![img](https://pic2.zhimg.com/80/v2-d187a82b1eb9c088fe60327828ee63aa_1440w.jpg?source=1940ef5c)

![img](https://pic2.zhimg.com/80/v2-28223a1c03c1800052a5dfe4e6cb8c53_1440w.jpg?source=1940ef5c)

得到代理Class对象后，Class对象有一个构造器，，需要传入InvocationHandler。而且代理对象的每个方法内部都会调用handler.invoke()！InvocationHandler对象成了代理对象和目标对象的桥梁，不像静态代理这么直接。

当代理对象调用方法时，在传入InvocationHandler中包含了mothed方法和对应的参数，在调用handler.invoke()

**所有调用的方法都会最终导向invoke方法，需要在里面具体实现目标类的方法和代理方法**（调用目标类的方法需要又重新new目录类）![img](https://pic2.zhimg.com/80/v2-6b091b6d41bae1f88ba74a510acb24b1_1440w.jpg?source=1940ef5c)

但这种写法不够优雅，属于硬编码。我这次代理A对象，下次想代理B对象还要进来改invoke()方法，太差劲了。改进一下，让调用者把目标对象作为参数传进来：

```java
public class ProxyTest {
	public static void main(String[] args) throws Throwable {
		CalculatorImpl target = new CalculatorImpl();
                //传入目标对象
                //目的：1.根据它实现的接口生成代理对象 2.代理对象调用目标对象方法
		Calculator calculatorProxy = (Calculator) getProxy(target);
		calculatorProxy.add(1, 2);
		calculatorProxy.subtract(2, 1);
	}

	private static Object getProxy(final Object target) throws Exception {
		//参数1：随便找个类加载器给它， 参数2：目标对象实现的接口，让代理对象实现相同接口
		Class proxyClazz = Proxy.getProxyClass(target.getClass().getClassLoader(), target.getClass().getInterfaces());
		Constructor constructor = proxyClazz.getConstructor(InvocationHandler.class);
		Object proxy = constructor.newInstance(new InvocationHandler() {
			@Override
			public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
				System.out.println(method.getName() + "方法开始执行...");
				Object result = method.invoke(target, args);
				System.out.println(result);
				System.out.println(method.getName() + "方法执行结束...");
				return result;
			}
		});
		return proxy;
	}
}
```



**这样就非常灵活，非常优雅了。无论现在系统有多少类，只要你把实例传进来，getProxy()都能给你返回对应的代理对象。就这样，我们完美地跳过了代理类，直接创建了代理对象！**

不过实际编程中，一般不用getProxyClass()，而是使用Proxy类的另一个静态方法：**Proxy.newProxyInstance()，**直接返回代理实例，连中间得到代理Class对象的过程都帮你隐藏

```java
public class ProxyTest {
	public static void main(String[] args) throws Throwable {
		CalculatorImpl target = new CalculatorImpl();
		Calculator calculatorProxy = (Calculator) getProxy(target);
		calculatorProxy.add(1, 2);
		calculatorProxy.subtract(2, 1);
	}

	private static Object getProxy(final Object target) throws Exception {
		Object proxy = Proxy.newProxyInstance(
				target.getClass().getClassLoader(),/*类加载器*/
				target.getClass().getInterfaces(),/*让代理对象和目标对象实现相同接口*/
				new InvocationHandler(){/*代理对象的方法最终都会被JVM导向它的invoke方法*/
					public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
						System.out.println(method.getName() + "方法开始执行...");
						Object result = method.invoke(target, args);
						System.out.println(result);
						System.out.println(method.getName() + "方法执行结束...");
						return result;
					}
				}
		);
		return proxy;
	}
```

![img](https://pic1.zhimg.com/80/v2-6aacbe1e9df4fe982a68fe142401952e_1440w.jpg?source=1940ef5c)

> 代理对象的本质就是：**和目标对象实现相同接口的实例。**代理Class可以叫任何名字，whatever，只要它实现某个接口，就能成为该接口类型。

动态代理的弊端：

​	动态代理生成的代理对象，最终都可以用接口接收，和目标对象一起形成了多态，可以随意切换展示不同的功能。**但是切换的同时，只能使用该接口定义的方法。**

## 7、spring结合mybatis

### 1、环境准备：

pom依赖导入：

```xml
<dependencies>
    <dependency>
        <groupId>junit</groupId>
        <artifactId>junit</artifactId>
        <version>4.12</version>
    </dependency>
    <dependency>
        <groupId>mysql</groupId>
        <artifactId>mysql-connector-java</artifactId>
        <version>5.1.47</version>
    </dependency>
    <dependency>
        <groupId>org.mybatis</groupId>
        <artifactId>mybatis</artifactId>
        <version>3.5.2</version>
    </dependency>
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-webmvc</artifactId>
        <version>5.2.0.RELEASE</version>
    </dependency>
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-jdbc</artifactId>
        <version>5.2.0.RELEASE</version>
    </dependency>
    <dependency>
        <groupId>org.aspectj</groupId>
        <artifactId>aspectjweaver</artifactId>
        <version>1.8.13</version>
    </dependency>
    <!-- https://mvnrepository.com/artifact/org.mybatis/mybatis-spring -->
    <dependency>
        <groupId>org.mybatis</groupId>
        <artifactId>mybatis-spring</artifactId>
        <version>2.0.5</version>
    </dependency>

</dependencies>
```

### 2、mybatis结构：

java：Mapper(接口，声明操作数据库的方法) Mapper.xml(连接接口，对应方法编写sql语句)

resources:	mybatis-config.xml 

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-config.dtd">
<!--configuration核心配置文件-->
 <properties resource="db.properties">
```

db.properties

```properties
driver=com.mysql.jdbc.Driver
url=jdbc:mysql://localhost:3306/mybatis?useSSL=true&useUnicode=true&characterEncoding=UTF-8
username=root
password=root
```

工具类：utils:（得到sqlsession)



```java
//sqlSessionFactory --> sqlSession
public class MybatisUtils {
    private static SqlSessionFactory sqlSessionFactory;
    static{
        try {
            //使用Mybatis第一步：获取sqlSessionFactory对象
            String resource = "mybatis-config.xml";
            InputStream inputStream = Resources.getResourceAsStream(resource);
            sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
    //既然有了 SqlSessionFactory，顾名思义，我们就可以从中获得 SqlSession 的实例了。
    // SqlSession 完全包含了面向数据库执行 SQL 命令所需的所有方法。
    public static SqlSession getSqlSession(){
        return sqlSessionFactory.openSession();
    }
}
```

myService:操作mapper

```java
   SqlSession sqlSession = MybatisUtils.getSqlSession();
        UserMapper mapper = sqlSession.getMapper(UserMapper.class);
        User user = mapper.getUserById(1);
```

### 3、spring结合mybatis

1、增加spring-dao.xml配置

（代替db.properties）

```xml
<bean id="dataSource" class="org.springframework.jdbc.datasource.DriverManagerDataSource">
    <property name="driverClassName" value="com.mysql.jdbc.Driver"></property>
    <property name="url" value="jdbc:mysql://localhost:3306/mybatis?useSSL=false&amp;useUnicode=true&amp;characterEncoding=UTF-8"/>
    <property name="username" value="root"></property>
    <property name="password" value="root"></property>
</bean>
```

（建立sqlSessionFactory代替工具类,且可结合mybatis-config.xml)

```xml
<bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
        <property name="dataSource" ref="dataSource"></property>
        <property name="configLocation" value="classpath:mybatis-config.xml"></property>
        <property name="mapperLocations" value="classpath:com/kuang/mapper/*.xml">
        </property>
</bean>
```

（为Mapper建立实现类MapperImpl，减少了Service操作，使其更加存粹）

得到MapperImpl对象的两种方式：

方法一：spring-dao.xml中在ioc容器中存入sqlSession和对应的MapperImpl对象：

```xml
<bean id="sqlSession" class="org.mybatis.spring.SqlSessionTemplate">
        <constructor-arg index="0" ref="sqlSessionFactory"></constructor-arg>
    </bean>
    <bean id="userMapper" class="com.kuang.mapper.UserMapperImpl">
        <property name="sqlSession" ref="sqlSession"></property>
    </bean>
```

方法二：：spring-dao.xml中在ioc容器中存入MapperImpl对象，参数直接引入sqlSessionFactory、

```xml
<bean id="userMapper1" class="com.kuang.mapper.UserMapperImpl2">
        <property name="sqlSessionFactory" ref="sqlSessionFactory"></property>
    </bean>
```

在MapperImpl在继承SqlSessionDaoSupport，直接getSqlSession()得到SqlSession对象

## 8、事务

```xml
<bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
    <property name="dataSource" ref="dataSource"></property>
</bean>
<tx:advice id="txAdvice" transaction-manager="transactionManager">
    <tx:attributes>
        <tx:method name="add" propagation="REQUIRED"/>
        <tx:method name="*" propagation="REQUIRED"/>
    </tx:attributes>
</tx:advice>
<aop:config>
    <aop:pointcut id="txpointCut" expression="execution(* com.kuang.mapper.*.*(..))"/>
    <aop:advisor advice-ref="txAdvice" pointcut-ref="txpointCut"/>
</aop:config>
```

事务只在方法里面实现