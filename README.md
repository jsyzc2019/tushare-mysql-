# tushare-mysql
通过财经接口tushare获取财经数据，并存储至mysql数据库中
暂时提供了前复权、无复权、股票每日信息、指数信息 四个数据类型的落库能力。


使用方法：
1. config 文件中填好相应配置内容
2. 做数据库、环境依赖准备 最好用python 3.8
3. terminal： python run.py

特点：
1. 由于tushare对请求这有200/min的限制，为了确保请求安全，重写了tushare.pro_bar() 和query两个方法.遇到超频会等，确保每一个请求都能拿到数据。
2. 可扩展：如果要增加数据类型的话，可以继承ts_mysql 中 父类 TushareMysqlEngine 去实现新的数据落库子类
3. 数据自检测：由于前复权在复权日需要重新reload所有日期的数据信息，qfq子类中（包括index）可以自动检测并回刷。
