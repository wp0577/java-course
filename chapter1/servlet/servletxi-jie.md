* 可以多个URl对应一个servlet

* 在对servlet进行映射的时候，可以使用通配符：\*.do 或者 /\*

  1. 匹配规则是看谁的匹配度高进行优先级选择。

  2. \*.do的优先级最低

* 当Servlet被第一次访问后，就被加载到内存，以后该实例对各个请求服务，即在使用中是单例的。

  1. 如果一个变量需要多个用户共享，则应当在访问该变量的时候，加同步机制synchronized\(object\){/code}

  2. 如果一个变量不需要共享，则直接在doGet\(\) 或者doPost\(\)定义，这样不存在线程安全问题。

* &lt;load-on-startup&gt;

  ```
      1.初始化一些数据，可以完成一些比如定时发送邮件等功能
  ```

---

![](/http/import.png)

---

#### SendRedirect\(\)可以实现重定向功能\(可以带数据给下一个页面\): 一个WEb资源收到客服端请求后, 通知客户端去访问另一个web资源.





