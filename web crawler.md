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

```java
package cn.itcast.crawler.test;

import org.apache.http.HttpEntity;
import org.apache.http.client.methods.CloseableHttpResponse;
import org.apache.http.client.methods.HttpGet;
import org.apache.http.impl.client.CloseableHttpClient;
import org.apache.http.impl.client.HttpClients;
import org.apache.http.util.EntityUtils;
import sun.net.www.http.HttpClient;

import java.io.IOException;

public class Crawlerfirst {
    public static void main(String[] args) throws IOException {
        //1.打开浏览器，创建HttpClient对象
        CloseableHttpClient httpClient = HttpClients.createDefault();
        //2.输入网址,发起get请求创建HTTPGet对象
        HttpGet httpGet = new HttpGet("http://www.itcast.cn");
        //3.按回车，发起请求 返回响应httpclient对象发起请求
        CloseableHttpResponse response = httpClient.execute(httpGet);
        //4.解析响应，获取数据
        //判断状态码是否为200
        if(response.getStatusLine().getStatusCode()==200){
            HttpEntity httpEntity = response.getEntity();
            String content = EntityUtils.toString(httpEntity,"utf-8");
            System.out.println(content);
        }
    }
}
```

