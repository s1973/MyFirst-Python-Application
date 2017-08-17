# MyFirst-Python-Application
Notes of Michael Liao's python tutorial

http://t.cn/R2PDyWN

<br/>  

#### 需要安装的模块
* pip install aiohttp
* pip install jinja2
* pip install aiomysql

<br/> 

> @clssmethod @staticmethod

1. @clasmethod 以类而不是类的实例作为第一个参数传给该方法
2. @staticmethod 运行时既不需要类也不需要类的实例参与的方法
3. how to use : [https://stackoverflow.com/](https://stackoverflow.com/questions/12179271/meaning-of-classmethod-and-staticmethod-for-beginner/12179752#12179752)

> 关于继承中的 MetaClass 和 __new__

1. `__new__()`方法是在类准备将自身实例化时调用
2. 定义 class Model(dict,metaclass=ModelMetaclass) 时 此时创建了一个class Model对象 因为定义了metaclass 所以是根据ModelMetaclass来创建Model这个对象的 相当于将ModelMetaclass实例化 调用其__new__方法
3. 定义 class User(Model) 时 此时创建了一个class User对象 User是继承自Model的 因此也就是通过Model 也就是ModelMetaclass创建的一个对象 因此也调用了ModelMetaclass的__new__方法