PHP Container & Facade Manager
===============

composer require topthink/think-container

Container
~~~
// 绑定一个类、闭包、实例、接口实现到容器
\think\Container::set('cache','\app\common\Cache');
// 从容器中获取对象的唯一实例
\think\Container::get('cache');
// 执行某个方法或者闭包 支持依赖注入
\think\Container::getInstance()->invoke($callable,$vars);
// 执行某个类的实例化 支持依赖注入
\think\Container::getInstance()->invokeClass($class,$vars);
~~~

Facade


定义一个`app\facade\App`类之后，即可以静态方式调用`\think\App`类的动态方法
~~~
<?php
namespace app\facade;

class App extends \think\Facade
{
    /**
     * 获取当前Facade对应类名
     * @access protected
     * @return string
     */
    protected static function getFacadeClass()
    {
	return '\think\App';
    }
}
~~~

或者动态绑定
~~~
\think\Facade::bind('app','\think\App');
\think\Facade::make('app');
\think\Facade::instance('app');
~~~