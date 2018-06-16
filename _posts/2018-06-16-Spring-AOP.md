---
layout: post
title: "Spring-AOP"
date: 2018-06-16
---

### 1. AOP概述
	a. AOP为Aspect Oriented Programming的缩写,意为:面向切面编程,通过预编译方式和运行期动态代理实现程序功能的统一维护的一种技术.
	
### 2. AOP特点
	a. AOP 是 OOP 的延续，是软件 开发中的一个热点，也是 Spring 框架中的一个重要内容，是函数式编程的一种衍生范型。
	b.  利用 AOP 可以对业务逻辑的各个部分进行隔离，从而使得业务逻辑各部分之间的耦合度降 低，提高程序的可重用性，同时提高了开发的效率。 
	c. AOP 是一个概念，并没有设定具体语言的实现，它能克服那些只有单继承特性语言的缺点， spring2.0 之后整合 AspectJ 第三方 AOP 技术。
	
### 3. AOP的主要功能
	a. 日志记录，性能统计，安全控制，事务处理，异常处理等等 .
	
### 4. AOP与OOP的区别
	a. OOP（ 面向对象编程）针对业务处理过程的实体及其属性和行为进行抽象封装，以获得更加清晰高效的逻辑单元划分。
	b. 而 AOP 则是针对业务处理过程中的切面进行提取，它所面对的是处理过程中的某个步骤或阶段，以获得逻辑过程中各部分之间低耦合性的隔离效果。这两种设计思想在目标上有着本质的差异。
	c. OOP 面向名词领域， AOP 面向动词领域
	
### 5. AOP相关术语
	a. 目标对象target:被代理增强的对象  
	b. 连接点join point:被拦截到的方法
	c. 切入点pointcut:被拦截到的方法当中可以插入增强的方法
	d. 通知advice:增强的代码,通知分为前置通知，后置通知，异常通知，最终通知，环绕通知
	e. 切面aspect(关系):通知和切点的结合，指定把什么（增强）插入到哪里（切点）去
	f. 织入weaving:通知插入到切点的过程
	g. 代理 Proxy:通知插入到切点通过代理完成的
	h. 引介 introduction:作用在类上，可以为一个类增加属性和方法
	
### 6. AOP实现
	a. 静态AOP：将切面代码直接编译到Java类文件中,在编译的时候完成增强，AspectJ AOP框架采用静态的方式
	b. 动态AOP：将切面代码进行动态织入实现的AOP,运行的时候完成增强，Spring采用这种方式，通过代理完成（jdk代理，cglib代理）
	
### 7. jdk代理与cglib代理
	a. jdk代理是一种基于接口的动态代理实现方式
	b. cglib代理既可以实现基于接口的动态代理,也可以实现非接口动态代理 
	c. 对于基于接口的动态代理实现,目标对象和代理对象是兄弟关系
	d. 对于基于非接口(继承)的动态代理实现,目标对象和代理对象是父子关系
	
### 8. AOP开发步骤
	a. 定义目标
	b. 定义通知
	c. 定义切点
	d. 定义切面（通知+切点）
	e. 生成代理

### 9. 通知类型
<table class="table table-striped table-hover">
	<tr class="info">
		<td>通知类型</td>
		<td>spring</td>
		<td>AspectJ</td>
		<td>特点</td>
	</tr>
	<tr>
		<td>前置通知</td>
		<td>BeforeAdvice</td>
		<td>Before</td>
		<td>目标方法执行前增强</td>
	</tr>
		<tr>
		<td>后置通知</td>
		<td>AfterReturningAdvice</td>
		<td>AfterReturning</td>
		<td>目标方法执行后增强</td>
	</tr>	
	<tr>
		<td>环绕通知</td>
		<td>MethodInterceptor</td>
		<td>Around</td>
		<td>目标方法执行前后进行增</td>
	</tr>	
	<tr>
		<td>抛出通知</td>
		<td>ThrowAdvice</td>
		<td>AfterThrowing</td>
		<td>目标方法抛出异常后的增</td>
	</tr>	
	<tr>
		<td>引介通知</td>
		<td>IntroductionInterceptor</td>
		<td>DeclareParents</td>
		<td>在目标类中添加一些新的方法或属性</td>
	</tr>	
	<tr>
		<td>最终通知</td>
		<td>-</td>
		<td>After</td>
		<td>不管是否异常，该通知都会执行</td>
	</tr>
</table>