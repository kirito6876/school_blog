#基于laravel5.2的博客系统
>此项目是我大学毕业设计所写的，我基本上功能上是按Wordpress写的一个博客系统，其中可能会有bug，因为我当时在工作，每天只能晚上写。
如果有什么问题可以发我邮箱:adk@adki.me

[演示地址：http://blog.adki.me/](http://blog.adki.me/)

##安装方法
上传完网站程序后对网站目录进行权限设置执行：
```shell
$ chown www:www -R 你的项目所在目录

例如：我的目录是/home/liangzhi/桌面/html/my/laravel-blog-demo,www-data为运行apache的用户

$ chown www-data:www-data -R /home/liangzhi/桌面/html/my/laravel-blog-demo

```

进入网站目录，执行更新composer依赖：
```shell
$ composer update
```

配置laravel框架的配置文件
首先把`app/Providers/AppServiceProvider.php`文件中：
```php
$seo_index = Seo::findOrFail(1);
$seo_photography = Seo::findOrFail(2);
$seo_blog = Seo::findOrFail(3);
$links = Link::all();
view()->share('seo_index',$seo_index);
view()->share('seo_photography',$seo_photography);
view()->share('seo_blog',$seo_blog);
view()->share('links',$links);
```

这段代码剪切出来，执行完下面的命令后再粘贴回去


修改数据库用户与密码

```shell
$  cp .env.example  .env
```

将.env中的数据库名字，数据库用户，密码修改成你环境的配置


执行laravel数据库表创建命令

```shell
$ php artisan migrate
```

执行laravel数据填充命令

```shell
$ php artisan db:seed
```
重新生成密钥

```shell
$ php artisan key:generat
```




执行完成之后访问网址，享受自己的博客平台吧！！！

默认用户名：adk@adki.me 密码：111111
