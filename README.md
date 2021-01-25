# cplugins/log
日志组件

## 安装
项目根目录执行:
```
composer require cplugins/log v1.0.4
```

## 配置
config/app.php 目录下

注释以下配置
```
'log' => env('APP_LOG', 'single'),
```
增加以下配置
```
// 按天拆分日志
'log' => env('APP_LOG', 'daily'),
// 保留30天的日志, 根据需求进行配置
'log_max_files' => 30,
```

## 使用 
```
$log = new LogHelper();
<!-- 该方法支持第二个参数, 传入exception对象-->
$log->info("提示信息");

<!-- 该方法支持第二个参数, 传入exception对象-->
$log->debug("调试信息");

<!-- 该方法支持第二个参数, 传入exception对象-->
$log->error("错误信息");

<!-- 该方法支持第二个参数, 传入exception对象-->
$log->warn("警告信息");
```

## 输出
```
格式： 时间 info 模块 类名 方法名 描述 code message trace
内容： [2021-01-23 11:49:07] production.INFO: /workspace/php-project/i-admin-manage-pc-interface App\Http\Controllers\Product\TemplateController testLog this is test  
```

## 优化
vendor/laravel/framework/src/Illuminate/Foundation/Exceptions/Handler.php文件 report方法修改如下
```
注释掉以下代码
// try {
//     $logger = $this->container->make(LoggerInterface::class);
// } catch (Exception $ex) {
//     throw $e; // throw the original exception
// }

// $logger->error(
//     $e->getMessage(),
//     array_merge($this->context(), ['exception' => $e]
// ));

追加以下代码
$log = new LogHelper();
$log->error("异常捕获", $e);
```


