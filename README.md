# java
git init
git add README.md
git commit -m "first commit"
git remote add origin git@github.com:liujijun/java.git
git push -u origin master

java SpringBoot 学习过程中遇到的问题记录：
1、关于Spring-Boot bean无法注入的问题（注意一般与文件包对应的位置有关）
  「
  错误信息：
  2017-04-22 16:14:19.778  WARN 37862 --- [  restartedMain] ationConfigEmbeddedWebApplicationContext : Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'configController': Unsatisfied dependency expressed through field 'authorSettings'; nested exception is org.springframework.beans.factory.NoSuchBeanDefinitionException: No qualifying bean of type 'com.commpany.sp.bean.AuthorSettings' available: expected at least 1 bean which qualifies as autowire candidate. Dependency annotations: {@org.springframework.beans.factory.annotation.Autowired(required=true)}
2017-04-22 16:14:19.780  INFO 37862 --- [  restartedMain] o.apache.catalina.core.StandardService   : Stopping service Tomcat
2017-04-22 16:14:19.793  INFO 37862 --- [  restartedMain] utoConfigurationReportLoggingInitializer :

Error starting ApplicationContext. To display the auto-configuration report re-run your application with 'debug' enabled.
2017-04-22 16:14:19.889 ERROR 37862 --- [  restartedMain] o.s.b.d.LoggingFailureAnalysisReporter   :

***************************
APPLICATION FAILED TO START
***************************

Description:

Field authorSettings in com.mycommpany.sp.controller.ConfigController required a bean of type 'com.commpany.sp.bean.AuthorSettings' that could not be found.
  解决方式：SpringBoot项目的Bean装配默认规则是根据Application类所在的包位置从上往下扫描！ 注意包的关系。
  」
2、数据库依赖问题
「
错误信息：2017-04-22 15:51:36.740  WARN 37711 --- [  restartedMain] ationConfigEmbeddedWebApplicationContext : Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'dataSource' defined in class path resource [org/springframework/boot/autoconfigure/jdbc/DataSourceConfiguration$Tomcat.class]: Bean instantiation via factory method failed; nested exception is org.springframework.beans.BeanInstantiationException: Failed to instantiate [org.apache.tomcat.jdbc.pool.DataSource]: Factory method 'dataSource' threw exception; nested exception is org.springframework.boot.autoconfigure.jdbc.DataSourceProperties$DataSourceBeanCreationException: Cannot determine embedded database driver class for database type NONE. If you want an embedded database please put a supported one on the classpath. If you have database settings to be loaded from a particular profile you may need to active it (the profiles "dev" are currently active).
2017-04-22 15:51:36.742  INFO 37711 --- [  restartedMain] o.apache.catalina.core.StandardService   : Stopping service Tomcat
2017-04-22 15:51:36.755  INFO 37711 --- [  restartedMain] utoConfigurationReportLoggingInitializer :

Error starting ApplicationContext. To display the auto-configuration report re-run your application with 'debug' enabled.
2017-04-22 15:51:36.759 ERROR 37711 --- [  restartedMain] o.s.b.d.LoggingFailureAnalysisReporter   :

***************************
APPLICATION FAILED TO START
***************************

Description:

Cannot determine embedded database driver class for database type NONE

Action:

If you want an embedded database please put a supported one on the classpath. If you have database settings to be loaded from a particular profile you may need to active it (the profiles "dev" are currently active).
解决的方式：去掉jdbc的依赖包
」
 
