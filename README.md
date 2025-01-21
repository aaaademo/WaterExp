
![30x30](https://user-images.githubusercontent.com/96420060/179494641-89ede898-38fb-42dd-b0e2-d36d643dd847.jpg)


## 20250120-修复SSL错误（_ssl.c:1007）

```python
import ssl
import requests

class TLSAdapter(requests.adapters.HTTPAdapter):
    def init_poolmanager(self, *args, **kwargs):
        ctx = ssl.create_default_context()
        ctx.set_ciphers("DEFAULT@SECLEVEL=1")
        ctx.options |= 0x4   # <-- the key part here, OP_LEGACY_SERVER_CONNECT
        kwargs["ssl_context"] = ctx
        return super(TLSAdapter, self).init_poolmanager(*args, **kwargs)

url = 'https://xxx.com/'

with requests.session() as s:
    s.mount("https://", TLSAdapter())
    print(s.get(url).content.decode('utf-8'))


```


# WaterExp：一款面向安服仔的扫描报告模板 和 碰瓷工具 
█ 打工人新时代的摸鱼解决方案，安抚仔挖不到洞的最后一丝欢颜！
  
    （不产生实际攻击）  
    （不会getshell）  
    （面向水报告）  
什么红队蓝队的，要什么shell，老夫日站就是看响应头缺啥一把梭，只要看得过去就能过！

# 配合《专业水报告漏洞模板.docx》食用更舒服
# 使用方式：
    py3 WaterExp.py -u http://www.target.com
    py3 WaterExp.py -f urls.txt

    扫描完毕复制漏洞名称
    打开模板文档
    ctrl+a打开微信截图，
    圈上对应响应头
    粘贴上文字
    粘贴到模板文档对应位置
    复制到新文档
    好了，可以出报告了
#渗透模板
![image](https://user-images.githubusercontent.com/96420060/179387550-4ed2491b-1ccd-4849-8387-2d9e57148f6d.png)

# 运行截图

![image](https://user-images.githubusercontent.com/96420060/189296502-106c8c34-8982-4f6d-a60a-61ddd1f8c7ac.png)

扫描结果
![image](https://user-images.githubusercontent.com/96420060/179387420-0bc4d65c-5d74-4ea4-a476-23b6409c8c48.png)
