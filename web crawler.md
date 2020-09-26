## 网络爬虫

网络爬虫是一种按照一定的规则，自动地抓取万维网信息的程序或者脚本。

### 爬虫入门程序

#### 环境准备

- JDK1.8
- IntelliJ IDEA
- IDEA自带的Maven

![image-20200924142818317](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200924142818317.png)

![image-20200924143354940](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200924143354940.png)

![image-20200924145737373](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200924145737373.png)

### idea爬虫

```java
package cn.itcast.crawler.test;

import org.apache.http.HttpEntity;
import org.apache.http.client.methods.CloseableHttpResponse;
import org.apache.http.client.methods.HttpGet;
import org.apache.http.impl.client.CloseableHttpClient;
import org.apache.http.impl.client.HttpClients;
import org.apache.http.util.EntityUtils;

import java.io.IOException;

public class Crawlerfirst {
    public static  void  main(String[] args) throws IOException {
        //1.打开浏览器，创建Httpclient对象
        CloseableHttpClient httpClient = HttpClients.createDefault();
        //2.输入网址,发起get请求,创建HttpGet对象
        HttpGet httpGet = new HttpGet("https://movie.douban.com/" );

        httpGet.setHeader("User-Agent","Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/85.0.4183.83 Safari/537.36");

        //3.按回车，发起请求，返回响应，使用httpClient对象发请求
        CloseableHttpResponse response = httpClient.execute(httpGet);
//        System.out.println(response.getStatusLine());
//
//        System.out.println(EntityUtils.toString(response.getEntity()));
//        System.out.println(response);

        //4.解析响应，获取数据
        //判断状态码是不是200
        if (response.getStatusLine().getStatusCode() == 200) {
            HttpEntity httpEntity = response.getEntity();
            String content = EntityUtils.toString(httpEntity, "utf-8");
            System.out.println(content);
        }
    }
}
```

F12之后刷新， Status Code为200， 输入框内代码和User-Agent

![image-20200924211541623](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200924211541623.png)

![image-20200924211811354](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200924211811354.png)

#### log4j

```
log4j.rootLogger=DEBUG,A1
log4j.logger.cn.incest = DEBUG

log4j.appender.A1=org.apache.log4j.ConsoleAppender
log4j.appender.A1.layout=org.apache.log4j.PatternLayout
log4j.appender.A1.layout.ConversionPattern=%-d{yyyy-MM-dd HH:mm:ss,SSS} [%t] [%c]-[%p] %m%n
```

