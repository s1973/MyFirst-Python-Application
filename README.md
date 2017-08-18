# MyFirst-Python-Application
Notes of Michael Liao's python tutorial

http://t.cn/R2PDyWN

<br/>  

#### 需要安装的模块
* pip install aiohttp
* pip install jinja2
* pip install aiomysql
* pip install watchdog

<br/> 

> @clssmethod @staticmethod

1. @clasmethod 以类而不是类的实例作为第一个参数传给该方法
2. @staticmethod 运行时既不需要类也不需要类的实例参与的方法
3. how to use : [https://stackoverflow.com/](https://stackoverflow.com/questions/12179271/meaning-of-classmethod-and-staticmethod-for-beginner/12179752#12179752)

> 关于继承中的 MetaClass 和 \_\_new\_\_

1. `__new__()`方法是在类准备将自身实例化时调用
2. 定义 class Model(dict,metaclass=ModelMetaclass) 时 此时创建了一个class Model对象 因为定义了metaclass 所以是根据ModelMetaclass来创建Model这个对象的 相当于将ModelMetaclass实例化 调用其__new__方法
3. 定义 class User(Model) 时 此时创建了一个class User对象 User是继承自Model的 因此也就是通过Model 也就是ModelMetaclass创建的一个对象 因此也调用了ModelMetaclass的__new__方法
4. 定义派生类__init__方法时必须先显式调用其父类的__init__方法 否则会报错 因为不重写__init__时解释器会自动调用超类中已定义的__init__方法

> Python头注释及多行注释

1. `#!/usr/bin/env python3`声明该文件需要python环境运行 在linux mac下配置好path可以直接双击运行
2. `# -*- coding: utf-8 -*-`声明编码 文件中有中文时必须声明
3. python中除头注释外第一行字符串通常为该文件的介绍文字 不会进行解释
4. 多行注释 `三对单引号或三对双引号 `  (注意和多行字符串一样)

> jinja2的变量输出用的是双花括号 Vue.js数据绑定也是双花括号 如何处理

1. 尽量用`<div v-text="abc"></div>`而不是`<div>{{ abc }}</div>`
2. 把vue相关代码集中到一块，用raw:  `{% raw %}<ul><li>{{ item }}</li></ul>{% endraw %}`


> 多重继承中建议使用 super()

1. super不是一个函数 而是一个类名 super(B,self)事实上调用了super类的初始化函数 产生了一个super对象
2. super类的初始化函数并没有做什么特殊的操作 只是简单记录了类类型和具体实例
3. super(B,self).func 调用的是B的MRO列表中的下一个类的方法 而非简单理解的父类
4. Python的多重继承类是通过MRO的方式保证各个父类的函数被逐一调用 而且只调用一次 因此建议每个类都使用super 不要直接使用基类名去调用方法
5. reference: [http://blog.csdn.net/](http://blog.csdn.net/damiaomiao666/article/details/51473199)