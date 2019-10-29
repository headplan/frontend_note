# npm与yarn

> 新版本的nodejs已经默认安装了npm

**yarn安装**

```
curl -o- -L https://yarnpkg.com/install.sh | bash
或者
brew install yarn
或者直接用npm安装,因为npm用了淘宝的源,速度快一些
cnpm i -g yarn
# 全局安装
# 添加国内镜像
yarn config set registry "https://registry.npm.taobao.org"
```

**常用命令**

```
npm install === yarn / yarn install
npm install xxx save === yarn add xxx
npm uninstall xxx --save === yarn remove xxx
npm install xxx --save-dev === yarn add xxx --dev
npm update === yarn upgrade
npm install xxx -g === yarn global add xxx
```

错误记录

```
npm install --no-bin-links
```

--no-bin-links 这里解决虚拟机共享目录无能创建symlinks的问题 , 但是用了之后有些会会先command not found . 应该是bin的链接无法创建了 .

```
chown -R $USER /usr/local  
npm cache clear
```

**参考**

[http://www.cnblogs.com/y-lin/p/6532580.html](http://www.cnblogs.com/y-lin/p/6532580.html)

