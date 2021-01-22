# cplugins
日志组件

## 安装
项目根目录执行:
```
composer require cplugins/log
```

## 配置
config/app.php 目录下

注释以下配置
```
'log' => env('APP_LOG', 'single'),
```
增加以下配置
```
'log' => env('APP_LOG', 'daily'),
//保留30天的日志, 根据需求进行配置
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
