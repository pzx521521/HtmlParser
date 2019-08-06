# HtmlParser
HtmlParser delphi XE
##### 仅在xe下测试 理论上D7也可以使用
+ 因为
+   http://www.raysoftware.cn/?p=370       OnlyRead
+ *只能读取*
+ 而
+   https://github.com/ying32/htmlparser   XE3Upper
+ *仅仅支持XE3Upper*
##### 参考上面的东西 以http://www.raysoftware.cn/?p=370 为基础
+ 所以加了几个可以修改的方法
```
THtmlElement 
    procedure SetTagName(Value: WideString); stdcall;    
    procedure SetInnerText(Value: WideString); stdcall;
    function AppedChild(const ATag: string): IHtmlElement; stdcall;
    procedure _GetHtml(IncludeSelf: Boolean; Sb: TStringBuilder);
```    
+ 主要是增加节点和修改内容
+ 注意THtmlElement 中 content(SetInnerText) 和 Orignal 在 ```_GetHtml``` 中的应用
+ 原作者在_GetHtml中 把一个THtmlElement分为了头和尾2个部分, 详见 ```_GetHtml```方法
#### 待解决问题
+ 1.AppedChild 后使用 SetInnerText 时 如果InnerText中包含新的节点如: ```<a onclick="delphi_Test()">功能</a>```, 新的节点(<a>)并不会动态解析到list中, 即无法使用 ```FindElements SimpleCSSSelector``` Count 之类的也会错误, 仅仅在 _GetHtml 时正确
+ 所以尽量不要在InnerText(FContent)中添加包含子节点的东西 而是通过AppedChild 逐级添加 或者需要的时候重新解析
+ 2.格式问题...........  没有换行 没有tab 就是没有带格式的输出  贼丑 特别是读入的时候还保留了格式

