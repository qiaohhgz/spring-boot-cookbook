interface module:  
承担了三个职责：  
开放接口层的职责：可直接封装 Service 方法暴露成 RPC 接口；通过 Web 封装成 http 接口；进行网
关安全控制、流量控制等。       
终端显示层的职责：各个端的模板渲染并执行显示的层。当前主要是 velocity 渲染，JS 渲染，JSP
渲染，移动端展示等。     
Web 层的职责：主要是对访问控制进行转发，各类基本参数校验，或者不复用的业务简单处理等


异常处理策略及日志规约：  
绝不应该继续往上抛异常，  
因为已经处于顶层，无继续处理异常的方式，如果意识到这个异常将导致页面无法正常渲染，
那么就应该直接跳转到友好错误页面，加上友好的错误提示信息。开放接口层要将异常处理成
错误码和错误信息方式返回


库版本号命名方式：主版本号.次版本号.修订号    
1） 主版本号：当做了不兼容的 API 修改，或者增加了能改变产品方向的新功能。    
2） 次版本号：当做了向下兼容的功能性新增（新增类、接口等）。    
3） 修订号：修复 bug，没有修改方法签名的功能加强，保持 API 兼容性。    
说明：    
注意：    
起始版本号必须为：1.0.0，而不是 0.0.1 正式发布的类库必须先去中央仓库进行查证，使版本号要有延续性，正式版本号不允许覆盖升级。
如当前版本：1.3.3，那么下一个合理的版本号：1.3.4 或 1.4.0 或 2.0.0



优化带宽ETag:     
http.headers().cacheControl().disable();  
第二次请求是要带上第一次请求的ETag值，注意ETag是有双引号包裹的      
如果没有变化，第二次请求服务器不会返回值并且HttpStatus会变为304(没有变化)    

##ssl:     
keytool -genkey -alias springboot-cookbook -keyalg RSA -keystore ./tomcat.keystore   
Enter keystore password:   
Re-enter new password:   
What is your first and last name?   
  [Unknown]:  springboot-cookbook   
What is the name of your organizational unit?   
  [Unknown]:  6kesong   
What is the name of your organization?   
  [Unknown]:  6kesong   
What is the name of your City or Locality?   
  [Unknown]:  sh   
What is the name of your State or Province?   
  [Unknown]:  sh   
What is the two-letter country code for this unit?   
  [Unknown]:  cn   
Is CN=springboot-cookbook, OU=6kesong, O=6kesong, L=sh, ST=sh, C=cn correct?   
  [no]:  yes   
Enter key password for <springboot-cookbook>   
        (RETURN if same as keystore password):   
Re-enter new password:   



