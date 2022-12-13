
1.SpringMVC注解@RequestParam(value = "xxx",required = false),required=false 作用
	根据某个属性查询时，在页面的传递信息用Controller控制器接收时，可能页面没有传递所需要的值，
	这个时候就会抛出参数绑定异常。加上这个注解之后，就可以防止抛出异常。
2.SpringBoot的注解@MapperScan标记在启动类上，@MapperScan({"com.test.demo","com.test1.demo"})，可以扫描多个路径，
  配置好扫描路径可以自动扫描所有的mapper接口，所有的mapper接口上无需添加mybatis的@Mapper注解
3.文件上传表单：SpringMVC源码解析书P75
4.idea中统计代码行数 安装插件Statistic；代码检查安装SonarLint；VO类中自动生成代码安装Lombok；
  mybatis中的maaper接口与mapper.xml文件相互跳转安装MyBatisX

------------------------------------------------------------------------------------------------

1、基于请求信息的条件映射
   对于HTTP请求来说，请求中可以包含很多信息，包括请求路径，请求方法，请求头等信息，而请求头中又包括几个通用的信息，例如请求提类型Content-Type和可接收的返回类型
@RequstMapping注解中提供了多个属性，每个属性都作为一种判断条件，对应于HTTP请求中的一个信息。当请求通过DispatcherServlet分发是，与该注解相关的处理器查找类RequestMappingHandlerMapping遍历所有@RequestMapping注解的信息，根据请求信息查找到与注解中配置的条件属性匹配度最高的注解，该注解所标记的方法就是最终被选择的处理器方法.
处理器查找匹配的过程中是需要结合全部请求属性进行条件判断的,使用RequestMappingInfo代表符合条件，其中包含了@RequestMapping中的所有属性
2、处理器参数解析
   参数解析通过HandlerMethodArgumentResolver组件实现，该组件提供supportsParameter方法，接收MethodParameter类型的参数
   对于http请求，可以通过URL和请求头传递参数，但只建议传递一些比较简单的字符串，对于比较复杂且数据量较大的数据，则通过请求体来传递 @RequestBody 标记参数。比如传过来一个对象参数，用该注解来标记参数。
3、返回值处理
   返回值处理通过HandlerMethodReturnValueHandler，该组件提供supportsReturnType，类似处理器参数解析，接收MethodParameter类型的参数
   @RequestBody和@ResponsBody对应，前者是把请求体反序列化为指定类型的对象，后者则是把指定类型的对象序列化为响应体返回给客户端
   @Restcontroller标记在类上，所有处理器方法均按照@ResbonseBody返回
4、控制器增强
   数据绑定：通过注解@InitBinder可以为数据绑定其添加新的类型转换器
   模型属性：通过在非处理器方法上标记@ModelAttribute，可以为所有的处理器方法附加模型属性。在执行处理器方法前限制性注解标记的方法，并添加该方法的返回值到Model中
   异常处理：当处理器方法中发生异常且未被处理器捕获时，会通过异常处理器对该异常进行处理。通过@ExceptionHandler可以为处理器方法声明异常处理方法
   请求体与响应体增强：在@RequestBody和@ResponseBOdy的处理中增强消息转换功能，可以在读请求体前、读请求体后、写响应器前对数据做一些特殊处理，需要在类上标记@ControllerAdvice
   
------------------------------------------------------------------------------------------------
IDEA命令：

1、Ctrl+N按名字搜索类

相当于eclipse的ctrl+shift+R，输入类名可以定位到这个类文件，就像idea在其它的搜索部分的表现一样，搜索类名也能对你所要搜索的内容多个部分进行匹配，而且如果能匹配的自己写的类，优先匹配自己写的类，甚至不是自己写的类也能搜索。

2、Ctrl+Shift+N按文件名搜索文件

同搜索类类似，只不过可以匹配所有类型的文件了。

3、Ctrl+H

查看类的继承关系，例如HashMap的父类是AbstractMap，子类则有一大堆。

4、Ctrl+Alt+B查看子类方法实现

Ctrl+B可以查看父类或父方法定义，但是不如ctrl+鼠标左键方便。但是在这里，Ctrl+B或ctrl+鼠标左键只能看见Map接口的抽象方法put的定义，不是我们想要的，这时候Ctrl+Alt+B就可以查看HashMap的put方法。

5、Alt+F7查找类或方法在哪被使用

相当于eclipse的ctrl+shif+H,但是速度快得多。

6、Ctrl+F/Ctrl+Shift+F按照文本的内容查找

相当于eclipse的ctrl+H，速度优势更加明显。其中Ctrl+F是在本页查找，Ctrl+Shift+F是全局查找。

7、Shift+Shift搜索任何东西

shift+shift非常强大，可搜索类、资源、配置项、方法等，还能搜索路径。其中搜索路径非常实用，例如你写了一个功能叫hello，在java，js，css，jsp中都有hello的文件夹，那我们可以搜索"hello/"找到路径中包含hello的文件夹。

8、查看接口的实现类

IDEA 风格 ctrl + alt +B     或者     Ctrl+Alt+鼠标左键

浏览器无痕状态            Ctrl + Shift + N

切换到上一个类            Ctrl + Tab
右键各类文件              Git -> rollback可以回滚未提交之前的状态<br>
自动补全左边              Ctrl + Alt + V <br>
抽取参数                  Ctrl + Alt + P <br>
抽取方法                  Ctrl + Alt + M <br>
导入Class                 Alt + Enter  <br>
修改名称                  Shift + F6    <br>
复制一行                  Ctrl + D    <br>
删除一行                  Ctrl + X    <br>
搜索类中的方法            Ctrl + F12  然后再复制需要查找的方法<br>
搜索任何东西              Shift + Shift  <br>
查看类的继承关系          Ctrl + H  <br>
查看类的所有结构          Ctrl + F12
打断点                    鼠标左键
格式化代码                Ctrl + Alt + L
代码上下移动              Ctrl + Shift + Up/Down
代码左移				  Shift + Tab
代码右移                  Tab
最近打开的文件            Ctrl + E
方法参数提示              Ctrl + P
idea本身的配置            Ctrl + Shift + Alt + ?
到达函数实现的地方        Ctrl + Alt + B
查看类等的定义的地方      Ctrl + B
html选中标签              Ctrl + W   先选中部分然后按快捷键即可
关闭当前代码窗            Ctrl + F4
重写方法的实现            Ctrl + O
删除无用的import          Ctrl + Alt + O
返回上次编辑的地方        Ctrl + Alt + <-
find in path失灵          Ctrl + Alt + F
看方法在哪里实现的        Alt + F7
参数改变位置              Ctrl + F6
切换大小写				  Ctrl + Shift + U
try-Catch快捷键           Ctrl + T
点进方法的实现            Ctrl + Alt 之后再点击
快速编辑一列              Alt + 鼠标左键下拉 然后输入内容