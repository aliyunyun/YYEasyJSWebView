# EasyJSWKWebView
Enable adding Javascript Interface to WKWebView like Android WebView
类似与Android WebView，注册类对象和类名称的方式实现Javascript与WKWebView的交互

###JS调用Objective-C

首先创建个类,类实例方法需要与js端方法名称保持一致

    #import "testJavaScript.h"

    @implementation testJavaScript

    -(void)JSCallOC
    {
   
    }

    -(void)OCCallJS
    {
    
    }
    @end
    
 注册类对象给WKWebview
 
    testJavaScript* bridge = [[testJavaScript alloc]init];
    
    [_webView addJavascriptInterfaces:bridge WithName:@"testJavaScript"];   
    

在JS代码里面，调用Objective-C方法：

    window.testJavaScript.JSCallOC();
    
    
    
###Objective-C调用JS
   
   直接调用WKWebView API 
   
    - (void)evaluateJavaScript:(NSString *)javaScriptString completionHandler:(void (^ __nullable)(__nullable id, NSError * __nullable error))completionHandler;  
  即可  
  
  
  例如：
  
    [_webView evaluateJavaScript:[NSString  stringWithFormat:@"OCCallJS('%@')",@"厉害了world哥"]completionHandler:nil];


具体代码请参考工程代码