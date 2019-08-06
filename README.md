# HtmlParser
HtmlParser delphi XE
仅在xe下测试 理论上D7也可以使用
因为
  http://www.raysoftware.cn/?p=370       OnlyRead
只能读取
而
  https://github.com/ying32/htmlparser   XE3Upper
仅仅支持XE3Upper
参考上面的东西 以http://www.raysoftware.cn/?p=370 为基础
所以加了几个可以修改的方法
THtmlElement 
    procedure SetTagName(Value: WideString); stdcall;
    procedure SetInnerHtml(Value: WideString); stdcall;
    procedure SetInnerText(Value: WideString); stdcall;
    function AppedChild(const ATag: string): IHtmlElement; stdcall;
主要是增加节点和修改内容
注意THtmlElement 中 content(SetInnerText) 和 Orignal(SetInnerHtml) 的不同
详情参考html中的InnerText和InnerHtml

