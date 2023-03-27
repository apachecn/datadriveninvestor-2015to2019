# 用于 Keras 的烧瓶 API

> 原文：<https://medium.datadriveninvestor.com/flask-api-for-keras-87c06da174e8?source=collection_archive---------3----------------------->

> 使用 Flask 在 5 分钟内部署您的 ML 模型！

![](img/61a7b2681a30026e90e04f4bf60a41aa.png)

Photo by [Fabienne Hübener](https://unsplash.com/@saimiri_sciureus?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

在完成了机器学习部分涉及的所有 R&D 之后，能够部署您的模型并使其作为服务可用是很好的。

为了简单起见，我们将部署一个基于*异或*问题的简单 Keras 模型。

# 先决条件

```
pip install tensorflow keras flask
```

# 克拉斯

希望你能很容易理解这段代码。

## 开始训练

```
python medium_flask_keras_.py
```

训练之后，创建一个 **xor_model** 文件。它包含模型及其权重。

# 瓶

让我们使用 Flask 创建一个 API，以便通过 HTTP 请求轻松访问模型。

`def predict()`处理两个 **GET** 和 **POST** 请求，但是你只能坚持一个。如果没有指定`methods`，默认情况下它处理 GET 请求。

`with graph.as_default()`是必需的，因为 Keras 中有一个 bug，当用 Flask 线程交叉时。

如果您希望从本地网络外部访问您的服务器，则需要`host='0.0.0.0'`。也不要忘记端口转发。

## 启动服务器

```
python medium_flask_keras_server.py
```

# 测试我们的配置

您可以使用 web 浏览器发出 GET 请求。只需访问以下 URL:

> [http://your _ server _ address:5000/预测？a=0 & b=1](http://your_server_address:5000/predict?a=0&b=1)

结果应该类似于:

```
{"result":[0.9952542781829834]}
```

## 就是这样！

## 如果你喜欢这篇文章——我真的很感激你点击鼓掌按钮，这将对我有很大帮助。和平！😎