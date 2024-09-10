## 一  知识结构

#### 1  `DispatcherServlet`

1.1  上下文层次结构
1.2  特殊Bean类型
1.3  Web MVC配置
1.4  Servlet配置
1.5  处理请求
1.6  路径匹配
1.7  拦截
1.8  异常
1.9  视图解析

#### 2  带注解的控制器

2.1  声明
2.2  映射请求
2.3  URI模式
2.4  模型
2.5  异常

#### 3  处理程序方法

3.1  `@RequestParam`
3.2  `@RequestHeader`
3.3  `@CookieValue`
3.4  `@ModelAttribute`
3.5  `@RequestBody`
3.6  `@ResponseBody`

## 二  主要内容

​	Spring Web MVC在Java servlet的基础上，提供了对于MVC实现的支持，通常简称为Spring MVC。
​	Spring MVC和许多其它Web框架一样，围绕前端控制器模式设计。`DispatcherServlet`是Spring MVC的中央`Servlet`，它提供了一个处理请求的共享算法，而实际的请求处理由可配置的委托组件执行；例如，可以配置用于请求拦截、视图解析、异常处理的委托组件。这些委托组件由Java注解或XML配置文件配置，并由Spring自动扫描和组装。
​	`DispatcherServlet`需要链接到一个`WebApplicationContext`。可以拥有一个上下文层次结构，一个根`WebApplicationContext`在多个`DispatcherServlet`实例之间共享，每个实例都有自己的子`WebApplicationContext`。

​	`DispatcherServlet`处理请求时，先绑定`WebApplicationContext`，再绑定一些解析器，最后对于具体请求搜索处理器执行。在解析请求和请求处理期间可以抛出并处理异常。
​	通常用`PathPatternParser`和已解析模式进行路径匹配。

​	请求处理由具体的特殊Bean执行。`HandleMapping`处理程序拦截。`HandlerExceptionResolver`处理异常，可以拥有一个异常处理器链；处理异常后，可以返回一个错误页面。`ViewResolver`用于解析视图。

​	可以使用Spring注解完成以上工作。
​	为定义控制器Bean，使用`@Controller`注解或`@RestController`注解。
​	为映射请求，使用`@RequestMapping`注解，可以映射URL，HTTP或其他请求。还可以使用HTTP方法的特定快捷方式变体。通常使用`PathPattern`映射URL模式，可以在模式中捕获URI变量。
​	为使用模型，使用`@ModelAttribute`注解。
​	为捕获并处理异常，使用`@ExceptionHandler`注解。

​	还有一些注解用于方法参数和返回值。`@RequestParam`注解用于绑定Servlet请求参数。`@RequestHeader`注解用于将HTTP请求头绑定到方法参数。`@CookieValue`将HTTP Cookie的值绑定到方法参数。`@ModelAttribute`将请求参数绑定到模型对象上。最后，`@RequestBody`和`@ResponseBody`用于序列化和反序列化对象。

## 三  重点梳理

- 理解`DispatcherServlet`，理解其工作原理、工作方式和工作流程。
- 理解并掌握带注解的控制器。
- 理解并掌握用于处理程序方法的参数和返回值的Spring注解。

## 四  难点解析

## 五  重要图表

无

## 六  薄弱点清单



------

