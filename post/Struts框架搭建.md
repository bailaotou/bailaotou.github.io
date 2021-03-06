--# Struts2授课

## 项目主页

```
http://struts.apache.org/
```

## 项目下载

```
MVC框架
1.接收前台传递的参数
2.调用业务逻辑
3.重定向或转发
```

```
https://struts.apache.org/download.cgi#struts2526
```

```
https://dist.apache.org/repos/dist/release/struts/2.5.26/
```

## Struts2框架的定位

```
   MVC全名是Model View Controller，是模型(model)－视图(view)－控制器(controller)的缩写，一种软件设计典范，用一种业务数据、逻辑、界面显示分离的方法组织代码，将业务逻辑聚集到一个部件里面，在改进和个性化定制界面及用户交互的同时，不需要重新编写业务逻辑。MVC被独特的发展起来用于映射传统的输入、处理和输出功能在一个逻辑的图形化用户界面的结构中。
   MVC开始是存在于桌面程序中的，M是指业务模型，V是指用户界面，C则是控制器，使用MVC的目的是将M和V的实现代码分离，从而使同一个程序可以使用不同的表现形式。C存在的目的则是确保M和V的同步，一旦M改变，V应该同步更新。更好的调节M和V的搭配。
   MVC是一种框架模式，说到底是一种框架，而不是一种设计模式，框架通常是代码重用，而设计模式是设计重用，而架构则介于两者之间，部分代码重用，部分设计重用，有时分析也可重用。
   
   1：耦合性低
　　视图层和业务层分离，这样就允许更改视图层代码而不用重新编译模型和控制器代码,[例如，改写jsp,html,css,javascirpt的代码，并不需要重启服务器]同样，一个应用的业务流程或者业务规则的改变只需要改动MVC的模型层即可【例如，换表名查询，更改一些查询的条件，或者使用动态sql还是静态的sql，只用更改model即可】。因为模型与控制器和视图相分离，所以很容易改变应用程序的数据层和业务规则。

    2：重用性高
　　随着技术的不断进步，需要用越来越多的方式来访问应用程序。MVC模式允许使用各种不同样式的视图来访问同一个服务器端的代码，因为多个视图能共享一个模型，它包括任何WEB(HTTP)浏览器或者无线浏览器(wap)，比如，用户可以通过电脑也可通过手机来订购某样产品，虽然订购的方式不一样，但处理订购产品的方式是一样的。由于模型返回的数据没有进行格式化，所以同样的构件能被不同的界面使用。【例如，模型层实现了同样的分页，不同的视图层可以用一万种不同的显示方法，例如百度搜索下面的分页和谷歌搜索下面的分页】MVC使开发和维护用户接口的技术含量降低。

    3：部署快
　　使用MVC模式使开发时间得到相当大的缩减，它使程序员(Java开发人员)集中精力于业务逻辑，界面程序员(HTML和JSP开发人员)集中精力于表现形式上。【例如，前端后端可以分工作业，效率高，方便多开发人员间的分工】

    4：可维护性高
　　分离视图层和业务逻辑层也使得WEB应用更易于维护和修改。【例如：如果想改业务逻辑，只用改业务逻辑，如果想改视图，只用改视图，如果想增加功能，只需要增加即可，分层最大的好处就是容易后期维护降低维护成本，和增加新的功能，提高代码重用性，从而提高开发效率】

    5：有利软件工程化管理
　　由于不同的层各司其职，每一层不同的应用具有某些相同的特征，有利于通过工程化、工具化管理程序代码。控制器也提供了一个好处，就是可以使用控制器来联接不同的模型和视图去完成用户的需求，这样控制器可以为构造应用程序提供强有力的手段。给定一些可重用的模型和视图，控制器可以根据用户的需求选择模型进行处理，然后选择视图将处理结果显示给用户。【因为控制器重点在于分配，更好的结合视图和模型】 
```

##  Struts2框架搭建步骤

### A.新建web项目(推荐创建Maven项目)

### B.导入相关jar包(推荐使用Maven方式)

```
commons-fileupload-1.2.2.jar
commons-io-2.0.1.jar
commons-lang3-3.1.jar
freemarker-2.3.19.jar
javassist-3.11.0.GA.jar
ognl-3.0.6.jar
struts2-core-2.3.14.jar
xwork-core-2.3.14.jar
```

```xml
 <!-- Struts2的核心包 -->
   <dependency>
       <groupId>org.apache.struts</groupId>
       <artifactId>struts2-core</artifactId>
       <version>2.3.16</version>
    </dependency>
   </dependencies>
```

### C. 在项目中找到web.xml,添加核心过滤器

```xml
 <filter>
  	<filter-name>struts2</filter-name
  		org.apache.struts2.dispatcher.ng.filter.StrutsPrepareAndExecuteFilter
  	</filter-class>
  </filter>
  <filter-mapping>
  	<filter-name>struts2</filter-name>
  	<url-pattern>/*</url-pattern>
  </filter-mapping>
```

### D. 添加核心配置文件

```
1.新建resources资源文件夹


2.在该资源文件夹下新建struts.xml核心配置文件


3.展开struts2-core-2.3.14.jar,找到struts-2.0.dtd,struts-2.1.7.dtd,struts-2.1.dtd,struts-2.3.dtd
打开其中任意一个,找到以下代码段
<!DOCTYPE struts PUBLIC
	"-//Apache Software Foundation//DTD Struts Configuration 2.3//EN"
	"http://struts.apache.org/dtds/struts-2.3.dtd">
	


4.拷贝上面的dtd头文件到struts.xml中



5.添加根标签<struts> 
struts.xml示例如下
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE struts PUBLIC "-//Apache Software Foundation//DTD Struts Configuration 2.1//EN" "http://struts.apache.org/dtds/struts-2.1.dtd">
<struts>

</struts>	
```

### E.创建一个Action类

```java
package com.hbwl.action;

import org.apache.struts2.convention.annotation.Action;
import org.apache.struts2.convention.annotation.Namespace;


public class testAction extends ActionSupport{
    /**
     * 
     * MethodName: execute
    *  Description: 
    *  @author javazhao
     */
   public void execute(){
        System.out.println("调用了TestAction里面的execute方法");
    }
    
     /**
     * 
     * MethodName: test
    *  Description: 
    *  @author javazhao
     */
   public void test(){
        System.out.println("调用了TestAction里面的test方法");
    }
    
    /**
     * 
     * MethodName: login
    *  Description: 
    *  @author javazhao
     */
   public String login(){
        System.out.println("调用了TestAction里面的test方法");
       return "SUCCESS";
    }
    
 }
```

### F.配置Action类

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE struts PUBLIC "-//Apache Software Foundation//DTD Struts Configuration 2.1//EN" "http://struts.apache.org/dtds/struts-2.1.dtd">
<struts>
<package name="struts2" extends="struts-default" namespace="/">
    <action name="exec" class="com.hbwl.action.testAction"></action>
    <action name="test" class="com.hbwl.action.testAction" method="test"></action>
    <action name="login" class="com.hbwl.action.testAction" method="login">
    <result name="success">/WEB-INF/page/success.jsp</result>
    </action>
</package>
</struts>
```

## 配置文件介绍

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE struts PUBLIC
    "-//Apache Software Foundation//DTD Struts Configuration 2.3//EN"
    "http://struts.apache.org/dtds/struts-2.3.dtd">

<struts>

    <!-- 把它设置为开发模式，发布时要设置为false -->
    <constant name="struts.devMode" value="true" />
    <!-- 设置在class被修改时是否热加载，发布时要设置为false -->
    <constant name="struts.convention.classes.reload" value="true"/>
    <!-- 自动动态方法的调用，使用这个设置后可以这样调用：action!method -->
    <constant name="struts.enable.DynamicMethodInvocation" value="true" />
    <!-- 指定jsp文件所在的目录地址 -->
    <constant name="struts.convention.result.path" value="/WEB-INF/content/" />
    <!-- 使用struts-default默认的转换器，如果是rest的使用：rest-default，rest需要rest的jar插件 -->
    <constant name="struts.convention.default.parent.package" value="struts-default"/>
    <!-- 用于配置包名后缀。默认为action、actions、struts-->
    <constant name="struts.convention.package.locators" value="actions" />
    <!-- 用于配置类名后缀，默认为Action，设置后，Struts2只会去找这种后缀名的类做映射 -->
    <constant name="struts.convention.action.suffix" value="Action"/>
    <!-- 设置即使没有@Action注释，依然创建Action映射。默认值是false。因为Convention-Plugin是约定优于配置的风格，
        可以不通过注解根据预先的定义就能访问相应Action中的方法 -->
    <constant name="struts.convention.action.mapAllMatches" value="true"/>
    <!-- 自定义jsp文件命名的分隔符 -->
    <constant name="struts.convention.action.name.separator" value="-" />
    <!-- 国际化资源文件名称 -->
    <constant name="struts.custom.i18n.resources" value="i18n" />
    <!-- 是否自动加载国际化资源文件  -->
    <constant name="struts.i18n.reload" value="true" />
    <!-- 浏览器是否缓存静态内容 -->
    <constant name="struts.serve.static.browserCache" value="false" />
     <!-- 上传文件大小限制设置 -->
    <constant name="struts.multipart.maxSize" value="-1" />
    <!-- 主题，将值设置为simple，即不使用UI模板。这将不会生成额外的html标签 -->
    <constant name="struts.ui.theme" value="simple" />
    <!-- 编码格式 -->
    <constant name="struts.i18n.encoding" value="UTF-8" />

</struts>
```

```properties
struts.devMode  可选值true,false （默认false），在开发模式下，struts2的动态重新加载配置和资源文件的功能会默认生效。同时开发模式下也会提供更完善的日志支持。  

struts.i18n.reload 可选值true,false（默认值依赖于struts.devMode），是否自动重新加载本地的资源文件。

struts.i18n.encoding  主要用于设置请求编码（默认值（UTF-8）） ，Head和Include标签的解析编码。  资源和配置文件的解析编码。

struts.configuration.xml.reload 可选值true,false（默认值依赖于struts.devMode）是否自动重新加载XML配置文件

struts.action.extension  设置struts的Action请求的后缀，支持多个时以逗号隔开。

struts.action.excludePattern 设置struts所排除的url（通过正则表达式匹配）（支持多个，以逗号隔开）

struts.tag.altSyntax 可选值true，false（默认true） 是否支持ognl表达式

struts.url.http.port 设置生成URL所对应的http端口

struts.url.https.port 设置生成URL所对应的https端口

struts.url.includeParams 可选值 none, get, all (默认get)，设置URL是否包含参数，以及是否只包含GET方式的参数。

struts.locale 设置struts2默认的locale，决定使用哪个资源文件。

struts.ui.templateDir 该属性指定视图主题所需要模板文件的位置，该属性的默认值是template，即默认加载template路径下的模板文件

struts.ui.theme 该属性指定视图标签默认的视图主题，该属性的默认值是xhtml。

struts.ui.templateSuffix 该属性指定模板文件的后缀，该属性的默认属性值是ftl。该属性还允许使用ftl、vm或jsp，分别对应FreeMarker、Velocity和JSP模板

struts.multipart.saveDir 设置上传临时文件的默认目录

struts.multipart.maxSize 设置上传的临时文件的最大限制

struts.objectFactory.spring.autoWire 可选值（name, type, auto, constructor,name）（默认name），设置spring的自动装配方式，只有引入spring插件后才有效。

struts.objectFactory.spring.autoWire.alwaysRespect （默认false）设置是否总是以自动装配策略创建对象。

struts.objectFactory.spring.useClassCache （默认false）对象工厂是否使用类缓存，开发模式无效。

struts.xslt.nocache （默认为false）设置XsltResult是否不是用缓存。

struts.custom.properties 设置用户的自定义属性文件名列表（用，隔开）

struts.custom.i18n.resources 设置用户自定义的资源文件路径列表（用，隔开）

struts.serve.static （默认false） 设置是否支持静态资源请求（要求url在struts或static下）

struts.serve.static.browserCache （默认false） 是否在静态资源响应中设置缓存。只有在支持静态资源时有效。
 
struts.el.throwExceptionOnFailure （默认false）是否在解析el表达式或无法找到属性时抛出RuntimeException

struts.ognl.logMissingProperties （默认false）是否日志无发找到的属性

struts.ognl.enableExpressionCache 是否缓存ognl解析的表达式。

struts.enable.DynamicMethodInvocation （默认false）是否支持动态的方法调用,在URL上通过!method指定方法。

struts.enable.SlashesInActionNames 在URL中的Action段中是否支持斜线

struts.mapper.alwaysSelectFullNamespace （默认false） 是否总是用最后一个斜线前的URL段作为namespace

核心对象Constants

struts.actionProxyFactory 设置ActionProxy的实体工厂，该工厂同时也生成默认的ActionInvoctation

struts.xworkConverter 设置XWorkConverter对象，该对象用于获取各种类型的转换器。

struts.unknownHandlerManager 设置UnknownHandlerManager的实现类，用于处理无法找到方法等异常。

struts.multipart.handler  设置mutipartRequest的handler （默认是jakarta）对应类，org.apache.struts2.dispatcher.multipart.JakartaMultiPartRequest

struts.mapper.class 可选值（struts，composite，restful，restful2）设置URL解析且映射到ACTION的实现，（默认struts）.

struts.mapper.prefixMapping 通过URL前缀映射到对应的Mapper，格式为urlPrefix1:mapperName2,urlPrefix2:mapperName2。必须添加mapperClass为org.apache.struts2.dispatcher.mapper.PrefixBasedActionMapper，并指定struts.mapper.class为该mapper。
    struts.mapper.composite 设置是否支持复合（多个）actionMapper，mapperName用逗号隔开。必须配置struts.mapper.class 为composite 才会生效
    struts.mapper.idParameterName 用于Restful2ActionMapper作为URL中id所对应的parameterName
    struts.ognl.allowStaticMethodAccess （默认false）设置ognl表达式是否支持静态方法。
    struts.configuration 设置struts2的Settings类。（2.1.2后不再使用）
    struts.urlRenderer 设置struts2的URL render（用于生成的URL），（默认struts），类名org.apache.struts2.components.ServletUrlRenderer
    struts.objectFactory 设置struts2的对象工厂，默认（struts），类名org.apache.struts2.impl.StrutsObjectFactory，当引入struts2-spring插件之后，则被修改为org.apache.struts2.spring.StrutsSpringObjectFactory
    struts.xworkTextProvider 设置struts2的资源文件内容提供类的实现。默认为com.opensymphony.xwork2.TextProviderSupport
    struts.actionValidatorManager 设置ActionValidatorManager 的实现类。
    struts.valueStackFactory 设置struts2的ValueStack工厂的实现。
    struts.reflectionProvider 设置ReflectionProvider的实现类
    struts.reflectionContextFactory 设置ReflectionContextFactory的实现类
    struts.patternMatcher 设置PatternMatcher的实现类
    struts.staticContentLoader 设置StaticContentLoader的实现类
```

## 动态方法调用

```xml
动态方法调用的基本规则如下:
http://IP地址:端口/项目/NAMESPACE/ActionName!Method
优点:不需要去配置action的method属性
缺点:每一个Action都得注册一下


<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE struts PUBLIC "-//Apache Software Foundation//DTD Struts Configuration 2.1//EN" "http://struts.apache.org/dtds/struts-2.1.dtd">
<struts>
<constant name="struts.enable.DynamicMethodInvocation" value="true" />
<package name="struts2" extends="struts-default" namespace="/">
<action name="ActionName" class="类路径" >
</package>
</struts>
```

## 通配符匹配

```xml
通配符匹配路径示意：
http://IP地址:端口/项目/NAMESPACE/类的去掉Action部分_Method名称_返回的页面的名称
优点:通用,遵循规定的路径格式
缺点:限制了规范 配置时必须遵循该规范

<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE struts PUBLIC "-//Apache Software Foundation//DTD Struts Configuration 2.1//EN" "http://struts.apache.org/dtds/struts-2.1.dtd">
<struts>
<constant name="struts.enable.DynamicMethodInvocation" value="true" />
<package name="struts2" extends="struts-default" namespace="/">
<action name="*_*_*" class="类路径{1}"  method="{2}">
<result name="默认不写就是success">/WEB-INF/page/{1}/{3}.jsp</result>
</action>
</package>
</struts>
```

## 参数传递

```
1.传递普通的数据类型
2.传递对象
3.传递对象集合
4.传递集合对象
5.传递Map


原则:
1.Action类中的属性名称 必须要Form中的表单控件的name值保持一致
2.该属性必须要有set方法
3.符合转换规则 可以进行直接转换  例如 前台 值是int类型的字符串  后台就可以使用int类型的属性来接收
4.格式:
a.普通的类型  name           后台 name属性
b.对象的类型  user.name      后台 private User user
c.数组的类型  user[0].name   后台  private List<User> user=new ArrayList<User>();
d.Map类型    param['name']   后台 private  Map<String,String> param;
PS:Map的value值如果是Object    默认是字符串数组
```

## 获取Web元素

### 方式01

```java
package com.hbwl.action;

import javax.servlet.ServletContext;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import javax.servlet.http.HttpSession;

import org.apache.struts2.interceptor.ServletRequestAware;
import org.apache.struts2.interceptor.ServletResponseAware;

import com.opensymphony.xwork2.ActionSupport;
import com.hbwl.entity.User;



public class LoginAction extends ActionSupport implements ServletRequestAware,ServletResponseAware{
     private  User user;
     private  HttpServletRequest request;
     private  HttpServletResponse response;
     private  HttpSession session;
     private  ServletContext application;
     
     
     public  String  doLogin()
     {
    	 if(user.getUname().equals("admin")&&user.getPwd().equals("123456"))
    	 {
    		 session.setAttribute("loginUser", user);
    		 return  SUCCESS;
    	 }
    	 else
    	 {
    		 //数据回显
    		 //添加错误信息到前台
    		 this.addActionError("用户名或者密码错误");
    		 return LOGIN;
    	 }	 
    	 
     }
       
	public void setUser(User user) {
		this.user = user;
	}

	public User getUser() {
		return user;
	}


	public void setServletResponse(HttpServletResponse response) {
		this.response=response;
		
	}

```

### 方式02

```java
package com.hbwl.action;

import javax.servlet.ServletContext;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import javax.servlet.http.HttpSession;

import org.apache.struts2.ServletActionContext;

import com.opensymphony.xwork2.ActionSupport;
import com.hbwl.entity.User;

/**
 * 工厂  多实例多线程
 * @author Administrator
 *
 */
public class Login2Action extends ActionSupport{
  private  HttpServletRequest request;
  private  HttpServletResponse response;
  private  HttpSession session;
  private  ServletContext application;
  private  User user;
  
  
  public Login2Action() {
  //使用Struts2的ServletActionContext对象获取request元素
	request=ServletActionContext.getRequest();
	session=request.getSession();
	application=ServletActionContext.getServletContext();
	//使用Struts2的ServletActionContext对象获取response元素
	response=ServletActionContext.getResponse();
}

  
  public  String  doLogin()
  {
 	 if(user.getUname().equals("admin")&&user.getPwd().equals("123456"))
 	 {
 		 session.setAttribute("loginUser", user);
 		 return  SUCCESS;
 	 }
 	 else
 	 {
 		 //数据回显
 		 //添加错误信息到前台
 		 this.addActionError("用户名或者密码错误");//对应的前端标签为<s:actionerror>
 		 this.addActionMessage("用户名是我的"); 		 //对应的前端标签为<s:actionmessage>
 		 this.addFieldError("name","随便啦"); //对应的前端标签为<s:fielderror>
 		 this.addFieldError("password","来一把LOL");
 		 return LOGIN;
 	 }	 
 	 
  }


public User getUser() {
	return user;
}


public void setUser(User user) {
	this.user = user;
} 
}
```

### 方式03

```java
package com.hbwl.action;

import java.util.Map;


import org.apache.struts2.interceptor.ApplicationAware;
import org.apache.struts2.interceptor.RequestAware;
import org.apache.struts2.interceptor.SessionAware;

import com.opensymphony.xwork2.ActionSupport;


//实现RequestAware, SessionAware,ApplicationAware接口的方式获取web元素
public class Login3Action extends ActionSupport  implements RequestAware, SessionAware,ApplicationAware
		 {
	private Map<String, Object> request; //HTTPSERVELTREQUEST
	private Map<String, Object> session;
	private Map<String,Object> application;
	
	

	public void setApplication(Map<String, Object> application) {
		this.application=application;
		
	}


	public void setSession(Map<String, Object> session) {

		this.session = session;
	}

	public void setRequest(Map<String, Object> request) {
		this.request = request;

	}


}

```

### 方式04

```java
package com.hbwl.action;

import java.util.Map;


import com.opensymphony.xwork2.ActionSupport;

public class Login4Action extends ActionSupport {

    private Map<String,Object> request;
    private Map<String,Object> session;
    private Map<String,Object> application;

    
    //使用ActionContext对象获取web元素
	public Login4Action() {
	request=(Map<String,Object>)ActionContext.getContext().get("request");
	session=ActionContext.getContext().getSession();
	application=ActionContext.getContext().getApplication();	
	}
	
	}
```

## 返回值类型

```xml
2种  
重定向 Response.sendRedirect("/index.jsp")
转发    request.getRequestDispatcher("/index.jsp").forward(request,response) ;

转发        
Chain  Action跳转Action  Action链
DispatherResult  Action跳页面  默认
重定向
Redirect
RedirectAction
默认的name是success  默认的type=dispatcher(默认就是转发)
<action name="自定义" class="自定义的" method="execute">
<result name="success" type="dispatcher">页面</result>
</action>
       
chain        
特点 Action跳Action  并且将上一个Action的接收的参数 继续往下一个Action传递
LoginAction   name
RegisterAction name
        

<package name="package1" extends="struts-default" namespace="/">
<action name="user" class="com.oraclewdp.action.LoginAction" method="doLogin">
<result  type="chain">
<param name="namespace">/</param>
<param name="actionName">register</param>
</result>
</action>
<action name="register" class="com.oraclewdp.action.RegisterAction" method="doRegister">
<result >/index.jsp</result>
</action>
</package>


       
redirect
特点:又可以跳页面 又可以跳Action
缺点:不能传递数据  但是我们可以通过路径加参数的方式传递数据
使用redirect到页面 无法将数据转发到页面 因为这种方式 是重定向的方式
使用redirect到页面+参数  页面必须要使用getParamter去接收 不能通过EL表达式去获取 因为这种方式本质就是重定向
细节:XML不支持&符号  必须使用转义字符&amp;来代替&
<package name="package2" extends="struts-default" namespace="/redirect">
<action name="user" class="com.oraclewdp.action.LoginAction" method="doRedirect">
<result  type="redirect" name="tojsp">/index.jsp</result>
<result   type="redirect"   name="tolist">/redirect/list?pageindex=1&amp;pagesize=5</result>
</action>

<action name="list"  class="com.oraclewdp.action.LoginAction" method="list">
<result>/index.jsp</result>
</action>
</package>

       
redirectAction 
特点:跳转到Action中
除了namespace和actionName之外的所有都是自定义的参数 
这些自定义的参数可以有n个 
<action name="tobaidu" class="com.hbwl.action.LoginAction">
<result name="tobaidu" type="redirectAction">
<param name="namespace">/redirect</param>
<param name="actionName">iambaidu</param>
<param name="hello">say</param>
<param name="world">i am baidu</param>
<param name="nihao">nihao</param>
</result>
</action>
```

## 错误处理

### JSP处理方式

```xml
  <error-page>
  <error-code>404</error-code>
  <location>/error/404.jsp</location>
  </error-page>
  
  <error-page>
  <exception-type>java.lang.NullPointerException</exception-type>
  <location>/error/500.jsp</location>
  </error-page>
  
  <error-page>
  <error-code>500</error-code>
  <location>/error/500.jsp</location>
  </error-page>
```

### Struts2的处理方式

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE struts PUBLIC "-//Apache Software Foundation//DTD Struts Configuration 2.1//EN" "http://struts.apache.org/dtds/struts-2.1.dtd">
<struts>
	<package name="package" extends="struts-default" namespace="/">

		<!--默认的Action 当请求的Action不存在 则默认跳转到这个Action中 -->
		<default-action-ref name="errorAction"></default-action-ref>

        <action name="errorAction">
         <result>/error/404.jsp</result>		
		</action>
        
		<!--全局的结果集 多个Action如果返回相同的结果 可以将这个结果定义在全局 -->
		<global-results>
			<result name="404" type="redirect">/error/404.jsp</result>
			<result name="500" type="redirect">/error/500.jsp</result>
		</global-results>


		<!--当碰到异常后 自动去到全局结果集中去寻找 然后自动跳转到对应的页面 -->
		<global-exception-mappings>
		<!--当捕获到异常之后 自动跳转到505 这个result name对应的页面 -->
	<exception-mapping  exception="java.lang.Exception"  result="500" ></exception-mapping>
		</global-exception-mappings>		
		</package>


```

## 国际化

```xml
国际化internationalization  i18n
演示:www.oracle.com

1.修改全局的属性default.properties
i18n配置
<constant name="struts.custom.i18n.resources" value="i18n"></constant>


2.根据语言准备属性文件
属性文件的命名规范为                 i18n_zh_CN.properties
                                 i18n_en_US.properties
                                 i18n_ja_JP.properties
                                 i18n_ko_KR.properties
 
 3.编写属性文件
 i18n_zh_CN.properties
 student=学生
 teacher=教师
 schoolfellow=校友
 examinee=考生
 visitor=访客
 
 
i18n_en_US.properties
student=student
teacher=teacher
schoolfellow= schoolfellow
examinee= examinee
visitor= visitor
 
 
i18n_ja_JP.properties
student=学生
teacher=教師
schoolfellow=校友
examinee=受験生
visitor=ビジター 
      
i18n_ko_KR.properties     
student=학생
teacher=교사
schoolfellow=교우
examinee=수험생 
visitor=손님

4. 在页面上 使用s标签
<s:text value="student">

5.动态切换
struts2最核心的功能就是拦截器
在进入每一个Action之前  都会经过默认的拦截器
<default-interceptor-ref name="defaultStack"/> 默认的拦截器栈

 <interceptor-stack name="defaultStack">  拦截器栈
                <interceptor-ref name="exception"/> 拦截器
                <interceptor-ref name="alias"/>
                <interceptor-ref name="servletConfig"/>
                <interceptor-ref name="i18n"/>
                <interceptor-ref name="prepare"/>
                <interceptor-ref name="chain"/>
                <interceptor-ref name="debugging"/>
                <interceptor-ref name="scopedModelDriven"/>
                <interceptor-ref name="modelDriven"/>
                <interceptor-ref name="fileUpload"/>
                <interceptor-ref name="checkbox"/>
                <interceptor-ref name="multiselect"/>
                <interceptor-ref name="staticParams"/>
                <interceptor-ref name="actionMappingParams"/>
                <interceptor-ref name="params">
                  <param name="excludeParams">dojo\..*,^struts\..*</param>
                </interceptor-ref>
                <interceptor-ref name="conversionError"/>
                <interceptor-ref name="validation">
                    <param name="excludeMethods">input,back,cancel,browse</param>
                </interceptor-ref>
                <interceptor-ref name="workflow">
                    <param name="excludeMethods">input,back,cancel,browse</param>
                </interceptor-ref>
            </interceptor-stack>

i18n的拦截器的处理机制:
如果发现你的路径后面 有一个request_locale参数  在i18n的拦截器中会被接收 
当i18n的拦截器接收到这个参数之后  就动态的改变浏览器语言的优先级了

拦截器和过滤器最本质的区别
过滤器可以过滤所有 
拦截器只能拦截Action

点击超级链接
<a href="ActionName?request_locale=zh_CN">中文</a>
<a href="ActionName?request_locale=en_US">英文</a>
<a href="ActionName?request_locale=ja_JP">日文</a>
<a href="ActionName?request_locale=ko_KR">韩文</a>


补充
  HTML标签 <input type="button" value='<s:property value="%{getText('student')}"/>'>
  S标签  <s:submit name="student" value="%{getText('student')}"/>

国际化的三种级别
Action级别  
场景:整个项目都要做国际化处理
1.和Action类在同一目录
2.命名规格 ActionName_zh_CN.properties


包级别
场景:多个Action需要使用同一个资源文件
1.放在包里面 com.oraclewdp.. 任意目录
2.命名规则
package_zh_CN.properties


全局级别 
场景:只有少量数据需要做国际化
1.配置全局的资源文件的名称  配置常量
<constant name="struts.custom.i18n.resources" value="xx,xxx,xxxx"></constant>
2.资源文件必须放在src目录
3.资源文件的命名规则是
xx_zh_CN.properties
xxx_en_US.properties
xxxx_ko_KR.properties

```

## 数据校验

### 方法校验

```java
Struts2 提供一些自带了一些校验的功能   但是必须要继承ActionSupport类
步骤:
1。你要校验哪个方法,就针对该方法去新建一个校验方法
校验方法的名称规范为validateMethod   即validation+方法(方法名首字母大写)
2.方法校验失败后 会自动去寻找
<result name="input">错误页面</result>


//执行请求的方法
public  String  doAdd()
	{
		
    	 System.out.println("helloworld");
		return this.SUCCESS;
	}

//校验doAdd方法
	public void  validateDoAdd()
	{
		if(user==null)
		{
			this.addActionError("用户对象为空");		
		}
		else
		{
			if(StringUtils.isEmpty(user.getName()))
			{
				this.addFieldError("name","用户名不能为空!");
			}
			if(StringUtils.isEmpty(user.getPwd()))
			{
				this.addFieldError("password", "密码不能为空!");
			}
		}	
		
	}
```

## UI标签

```
c标签
<%@ taglib prefix="c"  uri="http://java.sun.com/jsp/jstl/core"%>
s标签
<%@ taglib prefix="s"  uri="/struts-tags"%>
回显

表单标签的通用属性

*与css相关的属性
        cssClass, cssStyle, cssErrorClass, cssErrorStyle
*与触发事件相关的属性
      onblur, onchange, onclick, ondbclick, onfocus, onkeydown, onkeypress,    onkeyup, onmousedown, onmousemove, onmouseout, onmouseover, onmouseup,onselect

*与悬浮提示相关的属性
     jsTooltipEnabled: 是否允许用javascript来生成悬浮提示
     tooltip：悬浮提示的内容
     tooltipDelay:悬浮提示出现的延迟时间，以ms为单位
     tooltipIconPath：悬浮提示使用图标的URL路径
   
*其他来源于HTML的属性
    accesskey：指定快捷键，如果设置这个属性为x，按Alt+xz组合键就可以快速定位到这个生成的HTML组件
    disabled, id, tabindex, title
    
*与提示文本相关的属性
     label：用来显示在HTML组件前的文本
     key：同label一样，也是用来显示在HTML组件前的文本，但是其内容取自国际化信息
     labelposition：标签文本显示的位置，可以选择top或者left


 *与模板和主题相关的属性
    template, templateDir, theme
    *是否为必填的属性
    required：指定此生成的HTML组件是否为必填项
    requiredposition：指定此生成的HTML组件是必填项时提示信息显示的位置，可以是left或者right

    {18,19,20,21,22,23} 代表是一个数组或者是List 
    #{key:value,key1,value1} 代表一个Map


使用这个s标签
1.自己加一些样式  一般来说我们是不需要这些样式

  <!--表单-->
  <s:form namespace=""  action=""  method="post">
  </s:form>


  <!--下拉框-->
  <s:select    label="小朋友"  list="#{1:'李博',2:'小红',3:'小强',4:'小明'}" 
   headerKey="0" headerValue="请选择" name="xiaopengyou"></s:select>



 <!--复选框-->
   是不是男人:<s:checkbox  name="nihao"></s:checkbox>
   
   <!--复选框组-->
   <s:checkboxlist list="#{'1':'小白','2':'小红','3':'小强','4':'小明'}" name="xiappengyou2"></s:checkboxlist>
   
   
    <!--左右框-->
  <s:optiontransferselect
    label="最喜爱的图书"
        name="javaBook"
        list="{'《Java Web开发详解》', '《Struts 2深入详解》', '《Java快速入门》'}"
        doubleName="cBook"
        doubleList="{'《VC++深入详解》', '《C++ Primer》', '《C++程序设计语言》'}"/>

   
<!--上下框-->
<s:updownselect name="a" label="请选择您喜欢的图书" labelposition="top"
    moveUpLabel="向上移动"
    list="{'Spring2.0宝典' , '轻量级J2EE企业应用实战' , 'JavaScript: The Definitive Guide'}"/>


<!--上传控件-->
   请上传您靓照: <s:file name="file" ></s:file>



  <!--二级级联-->
 <s:doubleselect label="请选择所在省市" 
       name="province" list="{'四川省','山东省'}" doubleName="city" 
       doubleList="top == '四川省' ? {'成都市', '绵阳市'} : {'济南市', '青岛市'}" />
       
```

## OGNL表达式

```
OGNL表达式    简单的对象导航语言
表达式的目的就是为了去一个地方去取数据
OGNL中的#、%和$符号

#、%和$符号在OGNL表达式中经常出现，而这三种符号也是开发者不容易掌握和理解的部分。在这里我们简单介绍它们的相应用途。

1．#符号的三种用法
   1）访问非根对象属性，例如示例中的#session.msg表达式，由于Struts 2中值栈被视为根对象，所以访问其他非根对象时，需要加#前缀。
实际上，#相当于ActionContext. getContext()；
#session.msg表达式相当于ActionContext.getContext().getSession(). getAttribute("msg") 。
   2）用于过滤和投影（projecting）集合，如示例中的persons.{?#this.age>20}。
   3） 用来构造Map，例如示例中的#{'foo1':'bar1', 'foo2':'bar2'}。

2．%符号
      %符号的用途是在标志的属性为字符串类型时，计算OGNL表达式的值。如下面的代码所示：
<h3>构造Map</h3>
    <s:set name="foobar" value="#{'foo1':'bar1', 'foo2':'bar2'}" />
    <p>The value of key "foo1" is <s:property value="#foobar['foo1']" /></p>
    <p>不使用％：<s:url value="#foobar['foo1']" /></p>
    %表示的是当前是一个字符串%{数据} 自动将数据转换成OGNL表达式  字符串
    <p>使用％：<s:url value="%{#foobar['foo1']}" /></p>

运行界面如下所示。

he value of key "foo1" is bar1

不使用%：#foobar['foo1']

使用%：bar1

结论
1.%{} 就是对<s:property>的一个简写 只能用于S标签 S标签中内置表达式解析
2.%{} 不能加单引号什么的
3. 只能用于s标签 其他的没用
4．$符号 不说了....基本上不用

$符号主要有两个方面的用途。
     1） 在国际化资源文件中，引用OGNL表达式，例如国际化资源文件中的代码：reg.agerange=国际化资源信息：年龄必须在${min}同${max}之间。
     2） 在Struts 2框架的配置文件中引用OGNL表达式，例如下面的代码片断所示：
     
1. 当使用OGNL调用静态方法的时候，需要按照如下语法编写表达式： 
@package.classname@methodname(parameter) 
2. 对于OGNL来说，java.lang.Math是其的默认类，如果调用java.lang.Math的静态方法时，无需指定类的名字，比如：@@min(4, 10); 
3. 对于OGNL来说，数组与集合是一样的，都是通过下标索引来去访问的。


获取List:<s:property value="testList"/><br>
获取List中的某一个元素(可以使用类似于数组中的下标获取List中的内容):
<s:property value="testList[0]"/><br>


获取Set:<s:property value="testSet"/><br>
获取Set中的某一个元素(Set由于没有顺序，所以不能使用下标获取数据):
<s:property value="testSet[0]"/><br> ×

获取Map:<s:property value="testMap"/><br>
获取Map中所有的键:<s:property value="testMap.keys"/><br>
获取Map中所有的值:<s:property value="testMap.values"/><br>
获取Map中的某一个元素(可以使用类似于数组中的下标获取List中的内容):
<s:property value="testMap['m1']"/><br>
获取List的大小:<s:property value="testSet.size"/><br>

4. 使用OGNL来处理映射（Map）的语法格式如下所示： 
#{‘key1’: ‘value1’, ‘key2’: ‘value2’, ‘key3’: ‘value3’}; 

5. 过滤（filtering）：collection.{? expression} 

6. OGNL针对集合提供了一些伪属性（如size，isEmpty），让我们可以通过属性的方式来调用方法（本质原因在于集合当中的很多方法并不符合JavaBean的命名规则），但我么你依然还可以通过调用方法来实现与伪属性相同的目的。 

7. 过滤（filtering），获取到集合中的第一个元素：collection.{^ expression} 

8. 过滤（filtering），获取到集合中的最后一个元素：collection.{& expression} 

9. 在使用过滤操作时，我们通常都会使用#this，该表达式用于代表当前正在迭代的集合中的对象（联想增强的for循环） 

10. 投影（projection）：collection.{expression} 

11. 过滤与投影之间的差别：类比于数据库中的表，过滤是取行的操作，而投影是取列的操作。 具体举例如下：

利用选择获取List中成绩及格的对象:<s:property value="stus.{?#this.grade>=60}"/><br>

利用选择获取List中成绩及格的对象的username:

<s:property value="stus.{?#this.grade>=60}.{username}"/><br>

利用选择获取List中成绩及格的第一个对象的username:

<s:property value="stus.{?#this.grade>=60}.{username}[0]"/><br>

利用选择获取List中成绩及格的第一个对象的username:

<s:property value="stus.{^#this.grade>=60}.{username}"/><br>

利用选择获取List中成绩及格的最后一个对象的username:

<s:property value="stus.{$#this.grade>=60}.{username}"/><br>

利用选择获取List中成绩及格的第一个对象然后求大小:

<s:property value="stus.{^#this.grade>=600}.{username}.size"/><br>
12． 在Struts2中，根对象就是ValueStack。在Struts2的任何流程当中，ValueStack中的最顶层对象一定是Action对象。 

13. parameters，#parameters.username 

request, #request.username 

session, #session.username 

application, #application.username 

attr, #attr.username 自动去request session application parameters找

以上几个对象叫做“命名对象”。 

14. 访问静态方法或是静态成员变量的改进。 

@vs@method 

15. 关于Struts2标签库属性值的%与#号的关系： 

1）. 如果标签的属性值是OGNL表达式，那么无需加上%{}。 

2）. 如果标签的属性值是字符串类型，那么在字符串当中凡是出现的%{}都会被解析成OGNL表达式，解析完毕后再与其他的字符串进行拼接构造出最后的字符串值。 

3）. 我们可以在所有的属性值上加%{}，这样如果该属性值是OGNL表达式，那么标签处理类就会将%{}忽略掉。 


%号使用的情况
遍历数据到s标签中 让标签根据数组下标自动去值栈中获取数据


<s:form>
   <s:iterator  value="#request.userList"  var="xiaobo"  status="index">
   <div>
   <!--s标签可以自动去值栈中获取数据-->
   <!--html标签必须要给value属性-->
   <s:textfield   name="xiaobo[%{#index.index}].name"></s:textfield>
   <s:password   name="xiaobo[%{#index.index}].pwd"></s:password>
   </div> 
   </s:iterator>
   <s:submit value="提交数据"/>
  </s:form>



#号 可以构建map  
#{1:'张三',2:'李四',3:'王五'}
可以从值栈的contextMap域中获取数据
#request.xxx
#session.xxx
s:iterator 标签中 必须加上#获取数据 例如#index.xxx


<s:iterator  value="#request.userList"  var="xiaobo"  status="index">
  ${index.even}
  ${index.odd}
  ${index.index}
  ${index.count}
  <s:if test="#index.even">
     <tr  style="color:red"><td><s:property value="#xiaobo.id"/></td></tr>
  </s:if>
  <s:else>
      <tr><td><s:property value="#xiaobo.id"/></td></tr>
  </s:else>
  </s:iterator>



$符号一般用于XML配置文件中 将上一个Action获取的动态参数继续向下一个Action传递


<package name="package2" extends="struts-default" namespace="/redirect">
<action name="user" class="com.oraclewdp.action.LoginAction" method="doRedirect">
<result  type="redirect" name="tojsp">/index.jsp</result>
<result   type="redirect"   name="tolist">/redirect/list?pageindex=${pageindex}&amp;pagesize=${pagesize}</result>
</action>
```

## 值栈原理

```
使用以下标签打开值栈
<s:debug><s:debug>

值栈=OGNLContext      
ROOT域    
ContextMap域

Root域中存放 整个Action
ContextMap域中 存放 request,session,application等内置对象

struts2如何处理值栈  流程代码如下


public class StrutsPrepareAndExecuteFilter implements Filter{

	public void destroy() {
		
		
	}

	public void doFilter(ServletRequest request, ServletResponse response,
			FilterChain chain) throws IOException, ServletException {
	   //1.去寻找一个mvc.xml  
		HttpServletRequest req=(HttpServletRequest)request;
		String actionName=req.getRequestURI();
		//2.获取你的请求
		actionName=actionName.substring(actionName.lastIndexOf("/"),actionName.length());
		//3.解析该文件  Map<Key,Value>
		Map<String,String>actionContextMap=new HashMap<String,String>();
		actionContextMap.put("/hello","com.oraclewdp.action.LoginAction");
		//4.你的请求和我当前的action 和map的key做一个比较
		if(actionContextMap.get(actionName)!=null)
		{
			String className=actionContextMap.get(actionName);
		    try {
		    	//5.比较成功的话 就从Map中拿到Value 将这个Value反射 实例化 执行其execute方法
		    	Class clz=Class.forName(className);
			Object o=clz.newInstance();
			//NoSuchMethodException
		   Method method=clz.getDeclaredMethod("execute",null);
		    Object result=method.invoke(o, null);
		  //6.注入我们值
		    //注入值
		    //先反射获取当前action的所有字段
		    //比较 字段 和提交的数据 是否一致
		    //如果一致 则调用set方法去注入数据
		     Field name=clz.getDeclaredField("name");
		    name.setAccessible(true);
		    name.set(o,"李博");
		  //7.新建一个OgnlContext对象
		    OgnlContext actionContext=new OgnlContext();
		  //8.将我们实例化这个类 放到Root域中
		    actionContext.setRoot(o);//ROOT域  一个直接从属性开始
		    //ContextMap域  #key.....
		  //9.将session,request,application放到OGNLContext的ContextMap域
		    actionContext.put("request",req); //重写后的request StrutsRequestWare  getAttribute();
		    actionContext.put("session",req.getSession());
		    actionContext.put("application",req.getSession().getServletContext());
		  //10.通过request.setAttribute("valueStack",OgnlContext);
		    req.setAttribute("valueStack",actionContext);
		  //11.通过Request.getRequestDispacther("页面").forward(request,response);
		    request.getRequestDispatcher("/index.jsp").forward(request,response);
		   chain.doFilter(req, response);
			} catch (Exception e) {
			}
		}
		
	}

	public void init(FilterConfig filterConfig) throws ServletException {
		// TODO Auto-generated method stub
		
	}
```

## 类型转换

```
默认的类型转换
```

```
1.自定义类型转换类  继承StrutsTypeConverter
2.重写里面的两个方法
convertFromString  从String类型 转换为你想要的类型
convertToString     将你的类型转换为String类型





package com.hbwl.conversion;


import java.text.DateFormat;
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;
import java.util.Map;

import org.apache.struts2.util.StrutsTypeConverter;

public class DateConversion extends StrutsTypeConverter {
   DateFormat format=new SimpleDateFormat("yyyy-MM-dd");
	/**
	 * 将String类型转换为Object(任意)类型
	 * Map context 上下文
	 * String[] values  传递过来的参数
	 * Class toClass 你需要转换的类型
	 */
	public Object convertFromString(Map context, String[] values, Class toClass) {
		//如果你将要转换的类型是一个日期类型的话
		if(toClass==Date.class)
		{	
		if(values.length>0)
		{	
			//那么我就从你传递过来的字符串数组中 获取第一个过来
		String value=values[0];
	    try {
			Date d= format.parse(value);
			return d;
		} catch (ParseException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		//将你当前的字符串类型转换为日期类型
		//返回给你
		}
		}
			return values;
	}

	/**
	 * 将什么类型转换为String类型
	 */
	public String convertToString(Map context, Object o) {
		System.out.println("这个是转换的方法");
		//如果当前的object对象是一个日期的对象
		if(o instanceof Date)
		{                             
		//将这个日期类型的对象格式化为字符串类型
		String d=format.format((Date)o);
		return d;
		}	
		         
		return "";
	}

}





转换器的级别
Action的级别
场景 只在当前的Action有效
注册 将我们自定义的类型 生效
1.属性文件的命名规范
A.和Action必须在同一目录
B.ActionName-conversion.properties
2.写法
类中的属性.属性=转换类的类路径
属性=转换类的类路径
user.birthday=com.hbwl.conversion.DateConversion
user.tel=com.hbwl.conversion.TelPhoneConversion



全局的级别
1.全局级别的类型转换的文件  
A.必须放在根目录中
B.命名规范 必须叫xwork-conversion.properties
java.util.Date=com.hbwl.conversion.DateConversion
```

## 文件上传

```
1.struts2的文件上传的步骤
页面Form   enctype="multipart/form-data"   method="post"
2.struts2的文件上传 是由FileUploadInterceptor拦截器来帮助我们封装
3.需要在Action中定义三个属性
<FileName>               java.io.File类型  二进制文件
<FileName>ContentType    java.lang.String类型  文件的类型
<FileName>FileName       java.lang.String类型   文件的名称
如何获取项目中目录的路径
application.getRealPath("/upload")
application.getRealPath("upload")
4.如何上传
src  源文件
desc 目标文件
需要提前引入IOUtils.jar包
FileUtils.copyFile(image, new File(upload,getUUIDFileName(imageFileName)));
5.自己封装了一个方法 给每一个上传文件做唯一标识
private  String  getUUIDFileName(String imageFileName)
	{
	   String prefix=imageFileName.substring(0,imageFileName.lastIndexOf("."));
	   String sufix=imageFileName.substring(imageFileName.lastIndexOf("."),imageFileName.length());
	   prefix+=UUID.randomUUID().toString().replace("-","");
	   return prefix+sufix;
	}
	
实例  多文件上传
回显  照片	
```

### 限制文件上传

```java
Struts2文件上传超出配置大小的解决办法
校验上传文件的大小
public void validateAuthImgUpload() {//validate()验证方法  
      InputStream picStream;  
	        byte[] byt = new byte[0];  
	        try {  
	            picStream = new FileInputStream(image);  
	           
	            byt = FileCopyUtils.copyToByteArray(picStream);  
	            picStream.close();  
	            if(byt.length>1048576){  
	                this.clearActionErrors();  
	                this.addActionError("上传图片超过1M大小限制");  
	                return "input";  
	            }  
	        } catch (FileNotFoundException e1) {  
	            this.clearActionErrors();  
	            this.addActionError("上传文件没有找到，正确选择文件");  
	        } catch (IOException e) {  
	            this.clearActionErrors();  
	            this.addActionError("IO Exception");  
	        }  
}	        
	        
	        
	        
校验上传文件的类型
 public void validateAuthImgUpload() {//validate()验证方法  
        if("".equals(picName)|| picName==null||pic == null){//验证不能为空  
             //this.clearActionErrors();//这个地方清也不对，不清也不对    
            this.addActionError("请输入图片名称并选择上传文件");  
        }else{  
             String fileName = this.getPicFileName();//取到文件名  
             int index = fileName.indexOf(".");//找到点号，准备取后缀名  
             String fix = fileName.substring(index+1);  
             if(!("jpg".equals(fix)||"png".equals(fix)||"bmp".equals(fix)||"gif".equals(fix))){  
                 this.clearActionErrors();  
                 this.addActionError("图片只能是  gif/jpg/png/bmp 格式");  
             }  
        }  
  
    }  
    
    
    
    @Override  
    public void addActionError(String anErrorMessage) {
    //这个是重写的addActionError的方法，去掉系统的提示，使用自已的  
        if(anErrorMessage.startsWith("Request exceeded allowed size limit")){  
            super.addActionError("上传图片超过1M大小限制");  
        }else{  
            super.addActionError(anErrorMessage);  
        }  
          
    }  
}  

```

## 文件下载

```java
@ParentPackage("struts-default")
@Namespace("/qq")
@Action(value="uploads",results={@Result(location="/index.jsp"),
		@Result(name="download",type="stream",
		params={"inputName","inputStream","contentDisposition", "attachment;filename=\"${fileName}\".jpg" })})
public class DownloadAction {
	private ServletContext application;
	private InputStream inputStream;
    private String  fileName;
	
	public DownloadController() {

		application = ServletActionContext.getServletContext();

	}

	public String download() throws Exception {
		// 接收id参数
		// 从数据表中根据id来做查询
		// 获取上传文件夹的路径
		String upload = application.getRealPath("/uploads");
		// 获取文件的路径
		fileName = "杨玉环.jpg";
		//
		try {
			inputStream = new FileInputStream(new File(upload, fileName));
		} catch (FileNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		return "download";

	}

	public InputStream getInputStream() {
		return inputStream;
	}

	public void setInputStream(InputStream inputStream) {
		this.inputStream = inputStream;
	}

    //中文乱码处理方式
	public String getFileName() {
		String name=null;
		try {
			name = new String(fileName.getBytes("UTF-8"),"ISO-8859-1");
		} catch (UnsupportedEncodingException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		return name;
	}

	public void setFileName(String fileName) {
		this.fileName = fileName;
	}
	
```

## 拦截器(重点)

```xml
拦截器是我们struts2中最核心的概念
拦截器=过滤器
共同点
在去访问某个资源之前 必须先去访问他
过滤器 实现filter接口
在访问我们某个Action之前  必须得先去访问他
拦截器 实现Interceptor  继承AbstractInterceptor  继承MethodFilterInterceptor

过滤器 先写类  再配置
拦截器 先写类  再配置


不同点
1.过滤器可以过滤所有资源
2.拦截器只能拦截Action





拦截器 
我们可以在struts-default.xml文件中 我们可以看到
   <interceptor name="alias" class="com.opensymphony.xwork2.interceptor.AliasInterceptor"/>
3个概念
拦截器类
实现Interceptor  继承AbstractInterceptor  继承MethodFilterInterceptor
例如:


package com.oraclewdp.interceptor;

import com.opensymphony.xwork2.ActionInvocation;
import com.opensymphony.xwork2.interceptor.AbstractInterceptor;


public class MyInterceptor2 extends AbstractInterceptor{

	
	public String intercept(ActionInvocation invocation) throws Exception {
		
		return null;
	}

}




配置
在包中添加这个
拦截器
拦截器栈
多个拦截器组成一个拦截器栈
一个拦截器栈中也可以有拦截器栈
d=(a,b,c)  f=(h,i,j)   z=(d,f)=(a,b,c,h,i,j)


	<interceptors>
		<!--注册自己的拦截器-->
		<interceptor name="my2" class="com.oraclewdp.interceptor.MyInterceptor2"></interceptor>
		<!--配置拦截器栈-->
		<interceptor-stack name="myStack">
		<interceptor-ref name="defaultStack"></interceptor-ref>
		<interceptor-ref name="my2"></interceptor-ref>
		</interceptor-stack>
		</interceptors>


覆盖struts2默认的拦截器栈
```

## 注解功能 

```
使用注解功能 需要添加3个jar包  PS xx是版本的意思
asm.xx.jar
asm-commons.xx.jar
struts2-convention-plugin-2.x.xx.jar

PS 导jar包的时候 一定要注意版本
plugin的版本要和struts-core的jar包的版本保持一致

XML的配置方式
<package name="com.oraclewdp.action.UiAction" extends="base"  namespace="/ui">
<global-results>
<result name="input">/index.jsp</result>
</global-results>

<global-exception-mappings>
<exception-mapping result="success" exception="java.lang.Exception"></exception-mapping>
</global-exception-mappings>

<action name="core" class="com.oraclewdp.action.UiAction">
<result>/index.jsp</result>
<result name="success2" type="redirect">/index.jsp</result>
</action>
</package>



注解的配置方式
@ParentPackage("base")//和配置文件的继承extends是一个意思
@Namespace("/ui")  //和配置文件中的namespace是一个意思
@Results(@Result(name="input",location="/index.jsp"))//和配置文件中的</global-results>是一个意思
@ExceptionMappings({@ExceptionMapping(result="success",exception="java.lang.Exception"),})//和配置文件中的<global-exception-mappings>是一个意思
@Action(value="core",results={@Result(location="/index.jsp"),@Result(name="success2",type="redirect",location="/index.jsp")})//和配置文件的<action标签是一个意思



推荐使用注解的方式来做项目 因为注解的方式配置在类中  
配置文件的缺点:Action配置一多了就晕了



<!-- 不进行扫描的包，用，分割，被包含的包，将不会被扫描成为action -->
    <constant name="struts.convention.exclude.packages" value="com.sean.service" />
    <!-- 进行扫描的根包，该包会被扫描成action -->
    <constant name="struts.convention.action.packages" value="com.sean.action" />
    <!-- 返回页面地址 -->
    <constant name="struts.convention.result.path" value="/WEB-INF/content/" />
    <!-- 用于进行action查找的后缀 -->
    <constant name="struts.convention.action.suffix" value="Action" />
    <!--用于生成action名字时的分隔符，比如DemoCustAction会被映射成为demo_cust,同时用于形成返回文件，比如访问DemoAction，return的值为input，插件会去指定不睦下，查找demo_input.jsp文件 -->
    <constant name="struts.convention.action.name.separator" value="_" />
    <!-- 指定的包会被进行扫描 -->
    <constant name="struts.convention.package.locators" value="action,actions,struts,struts2" />
    <!-- 返回页面类型 -->
    <constant name="struts.convention.relative.result.types" value="dispatcher,velocity,freemarker" />
    <!-- 开启动态调用函数，这个方法在struts2里面不推荐，可是在这里却可以实现动态方法的调用，不用自写action了 -->
    <constant name="struts.enable.DynamicMethodInvocation" value="true" />
    <!-- 开发模式 -->
    <constant name="struts.devMode" value="true" />
```

## 前后端分离

```
1.需要使用STRUTS2的json的插件功能 
需要引入
commons-beanutils-xx.jar
commons-lang-xx.jar
ezmorph-xx.jar
json-lib-xx.jar
struts2-json-plugin-xx.jar



ajax请求-后台  发送数据过来  json
第三方的工具 
目的1: 将java类 转换成为json格式的字符串
目的2:将json格式的字符串 转换为类
GSON
JSON-LIB
JACKSON

2.需要继承
@ParentPackage("json-default")


3.
使用struts2的插件的时候
@Result(name="jsonSuccess",type="json")
root参数 代表只要当前的action中的某个属性  属性值有且只能有一个
@Result(name="jsonSuccess",type="json",params={"root","result"})
包含哪些属性  可以有多个 使用,号分隔
@Result(name="jsonSuccess",type="json",params={"includeProperties","result,sex,job"})
不包含  可以有多个 使用,号分隔
@Result(name="jsonSuccess",type="json",params={"excludeProperties","result,sex,job"})
注意 会将当前的类的所有的属性转换为json格式
排除 我们不要的东西
```

