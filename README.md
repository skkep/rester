Rester
======

基于Slim+Eloquent的RESTful API框架。

#Usage

1. 路由：
```
//app/routes.php
<?php


//更多使用方法请阅读文档:
//http://docs.slimframework.com/#Routing-Overview

$app->get('/', function(){
    return json_encode(['hello' => 'world!']);
});

```
或者也可以使用控制器：

```
//app/routes.php

$app->get('/', 'HomeController:index'); //调用HomeController的index方法

```

更多路由的使用请阅读Slim官方文档：http://docs.slimframework.com/#Routing-Overview

2. 控制器

<?php

/**
 * 演示控制器
 */
class HomeController extends Controller
{
    public function index() {
        return $this->json(['app' => 'Rester', 'message' => 'Hello world!']);
    }

    //...
}

控制器里有用的方法有：
 - `$this->init()`  会在项目初始化完成后首先调用，可以用来做一些初始化或者每个方法都需要用到的动作，比如用户授权。
 - `$this->json(mixed $data [, int $status = 200])`  输出`json`格式数据，第二个参数为状态码。
 - `$this->jsonp(mixed $data [, string $callback = ''])` 输出`jsonp`数据，第二个参数为回调函数名，可选，为空默认从$_GET读取`callback`, 如果最终获取不到callback，输出等于`$this->json`。
 - `$this->validate(array $input, array $rules [, boolean $return = false])` 数据验证，默认验证失败主动返回错误json输出并停止往下运行，当`$return = true`时不停止运行，返回验证失败消息。
 - `$this->error(string $message, int $status [, array $errors = []])` 输出错误json， `$errors` 为错误明细，通常为数组，可选。

更多数据验证规则请参阅：http://laravel.com/docs/4.2/validation

# License

MIT
