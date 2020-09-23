# Java web知识点

### Java web中四大属性范围汇总

***参考链接：https://www.cnblogs.com/bhlsheji/p/4710144.html***

首先区分客户端跳转和服务器跳转

- 客户端跳转（client跳转）：网址（地址栏）变化，页面变化
- 服务器跳转（server跳转）：网址（地址栏，即jsp:forward）不发生变化，但是页面也能变化

​	然后是以下四种属性范围

- page（pageContext）
  - 仅在一个页面中保存属性，跳转之后无效
  - 发生sever跳转后，无法获得跳转前的属性
- request
  - sever跳转之后有效
  - 但是通过超链接（a href=""或者/a）设置的属性无法取得
- session
  - 在一次会话中，不管何种跳转都能使用
  - 但是新开一个浏览器就不能使用
  - 在client跳转中，超链接中的属性也能获得（修改了地址栏数据）
- application
  - 在整个sever上保存，全部用户都能使用
  - 无论新开多少浏览器application属性均可取得，但是服务器又一次启动，之前的属性都将消失