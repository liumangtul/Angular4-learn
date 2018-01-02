## Lesson 1

一个angular应用至少包含一个模块（module）和组件（component）

***.module.ts <br>
***.component.ts


### 1、模块-module
    将应用中的不同部分组织成一个单元（包括组件，服务，指令等）
### 2、组件-component
* 组件是Angular应用最基本的构建块，可以把一个组件理解为一段带有业务逻辑和数据的html
* 组件可以有父子关系
* 组件可以调用服务（service）：service是用来封装可重复使用的业务逻辑，比如获取商品信息的逻辑
* 组件可以调服务（service），服务（service）也可以调服务（service）
### 3、指令-directive
* 允许你向html元素添加自定义行为,比如自动完成的指令.

#### 总结
组件，服务，模块是用来完成功能的
模块是用来打包和分发这些功能
学起来，感觉很多理论和angularJs1.x 的概念基本相同，但是语法变了。
比如定义个控制器之前是用controller，现在直接在typescript的类里面定义控制器

## Lesson 2
npm install -g @angular/cli;

ng new auction

目录结构介绍


e2e 端到端的测试
angular-cli.json angular命令行工具的配置文件
        在这里引入jquery，bootstrap包

editorconfig webstorm配置文件
karma.conf.js 执行自动化测试配置
protractor.conf.js 与karma。conf类似，也是用来做测试
tslint.json 制定typescript代码质量检查的配置


app -- 不多说了，基本代码都是放在这里的
assets --存放静态资源的，例如image
environments —环境配置，配置生产环境，开发环境等

index.html 你懂的
main.ts 入口文件
polyfills.ts 兼容补丁
style.css 应用的全局的样式
test.ts 测试
tsconfig
...

组件介绍：

#### 1、@Component ---组件元数据装饰器 简称装饰器
告诉框架如何处理一个typescript类
装饰器包含多个属性，这些属性的值叫做元数据
angular会根据元数据的值来渲染组件，执行组件的逻辑
#### 2、template—模版
    定义组件的外观-htm形式 绑定数据
#### 3、Controller—控制器
普通的typescript类
被@Component装饰器装饰
控制器包含所有组件的属性和方法
通过数据绑定与模版来通讯
template 模版展现控制器controller的数据
controller控制器处理模版module上发生的事件

以上3个是组件的必备要素

    ```
    import { Component } from '@angular/core';

    @Component({
      selector: 'app-root',
      templateUrl: './app.component.html',
      styleUrls: ['./app.component.css']
    })
    export class AppComponent {
      title = 'app';
    }

    ```

  selector    组件名
  templateUrl 模版
  styleUrls   样式

  AppComponent 控制器

app.component.html
```
    <h1>
      Welcome to {{ title }}!
    </h1>
```


输入属性 - @inputs（） ---传递数据
输出属性 - @outputs（）---组件之间共享数据等
providers---注入器
依赖注入
生命周期
Lifecycle Hooks

app.module.ts

```
    import { BrowserModule } from '@angular/platform-browser';
    import { NgModule } from '@angular/core';


    import { AppComponent } from './app.component';


    @NgModule({
      declarations: [
        AppComponent
      ],
      imports: [
        BrowserModule
      ],
      providers: [],
      bootstrap: [AppComponent]
    })
    export class AppModule { }

```