---
title: "Python的第三方库requests的使用"
layout: post
category: rote
tags: [python, lxml]
excerpt: "Requests 是用Python语言编写，基于 urllib，采用 Apache2 Licensed 开源协议的 HTTP 库。它比 urllib 更加方便，可以节约我们大量的工作，完全满足 HTTP 测试需求。Requests 的哲学是以 PEP 20 的习语为中心开发的，所以它比 urllib 更加 Pythoner."
---
原文链接:http://blog.csdn.net/shanzhizi/article/details/50903748

发送请求与传递参数
先来一个简单的例子吧！让你了解下其威力：

#引言

Requests 是用Python语言编写，基于 urllib，采用 Apache2 Licensed 开源协议的 HTTP 库。它比 urllib 更加方便，可以节约我们大量的工作，完全满足 HTTP 测试需求。Requests 的哲学是以 PEP 20 的习语为中心开发的，所以它比 urllib 更加 Pythoner。

(1)发送请求与传递参数：
先来一个简单的例子吧！让你了解下其威力：

      import requests
      r = requests.get(url='http://www.itwhy.org')    # 最基本的GET请求
      print(r.status_code)    # 获取返回状态
      r = requests.get(url='http://dict.baidu.com/s', params={'wd':'python'})   #带参数的GET请求
      print(r.url)
      print(r.text)   #打印解码后的返回数据
      
带参数的请求实例：

      import requests
      requests.get('http://www.dict.baidu.com/s', params={'wd': 'python'})    #GET参数实例
      requests.post('http://www.itwhy.org/wp-comments-post.php', data={'comment': '测试POST'})    #POST参数实例

POST发送JSON数据：

      import requests
      import json
 
      r = requests.post('https://api.github.com/some/endpoint', data=json.dumps({'some': 'data'}))
      print(r.json())

定制header：

      import requests
      import json

      data = {'some': 'data'}
      headers = {'content-type': 'application/json',
                 'User-Agent': 'Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:22.0) Gecko/20100101 Firefox/22.0'}

      r = requests.post('https://api.github.com/some/endpoint', data=data, headers=headers)
      print(r.text)
