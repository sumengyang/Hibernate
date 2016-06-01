# Hibernate
Hibernate框架简述

Hibernate的核心组件

在基于MVC设计模式的JAVA WEB应用中，Hibernate可以作为模型层/数据访问层。它通过配置文件(hibernate.properties或hibernate.cfg.xml)和映射文件(***.hbm.xml)把JAVA对象或PO(Persistent Object,持久化对象)映射到数据库中的数据库，然后通过操作PO，对数据表中的数据进行增，删，改，查等操作。

除配置文件，映射文件和持久化类外，Hibernate的核心组件包括以下几部分：

a)Configuration类：用来读取Hibernate配置文件，并生成SessionFactory对象。

b)SessionFactory接口：产生Session实例工厂。

c)Session接口：用来操作PO。它有get(),load(),save(),update()和delete()等方法用来对PO进行加载，保存，更新及删除等操作。它是Hibernate的核心接口。

d)Query接口：用来对PO进行查询操。它可以从Session的createQuery()方法生成。

e)Transaction接口：用来管理Hibernate事务，它主要方法有commit()和rollback()，可以从Session的beginTrancation()方法生成。

Persistent Object

持久化对象可以是普通的Javabeans,惟一特殊的是它们与（仅一个）Session相关联。JavaBeans在Hibernate中存在三种状态：

1.临时状态(transient):当一个JavaBean对象在内存中孤立存在，不与数据库中的数据有任何关联关系时，那么这个JavaBeans对象就称为临时对象(Transient Object)。

2.持久化状态(persistent):当一个JavaBean对象与一个Session相关联时，就变成持久化对象(Persistent Object)

3.脱管状态(detached):在这个Session被关闭的同时，这个对象也会脱离持久化状态，就变成脱管状态(Detached Object)，可以被应用程序的任何层自由使用，例如可以做与表示层打交道的数据舆对象(Data Transfer Object)。

Hibernate的运行过程

Hibernate的运行过程如下：

A:应用程序先调用Configration类，该类读取Hibernate的配置文件及映射文件中的信息，并用这些信息生成一个SessionFactpry对象。

B:然后从SessionFactory对象生成一个Session对象，并用Session对象生成Transaction对象;可通过Session对象的get(),load(),save(),update(),delete()和saveOrUpdate()等方法对PO进行加载，保存，更新，删除等操作;在查询的情况下，可通过Session对象生成一个Query对象，然后利用Query对象执行查询操作;如果没有异常，Transaction对象将 提交这些操作结果到数据库中。
