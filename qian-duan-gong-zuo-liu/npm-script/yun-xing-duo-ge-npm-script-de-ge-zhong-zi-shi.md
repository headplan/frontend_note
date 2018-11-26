# 运行多个npm script的各种姿势

npm内置多命令运行机 , 互不阻塞的运行npm script : npm-run-all

前端项目会包含 js、css、less、scss、json、markdown 等格式的文件 . 为保障代码质量 , 给不同的代码添加检查是很有必要的 , 代码检查不仅保障代码没有低级的语法错误 , 还可确保代码都遵守社区的最佳实践和一致的编码风格 .

常用前端代码检查工具 :

* eslint : 可定制的js代码检查工具
* stylelint : 可定制的样式文件检查 , 支持css , less , scss
* jsonlint : json文件语法检查
* markdownlint-cli : Markdown文件最佳实践检查

常用的单测技术栈 :

* mocha : 测试用例组织 , 测试用例运行和结果收集的框架
* chai : 测试断言库 , 必要的时候可以结合sinon使用

> 测试工具如tap , ava也都提供了命令行接口 , 能很好的集成到 npm script 中 , 原理是相通的 .

整理基本的代码检查 , 单元测试命令的package.json : 

```
{

}
```



