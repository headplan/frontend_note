# 快速应用

**演示应用**

```css
<meta charset="UTF-8">
<link href="https://cdn.bootcss.com/bootstrap/3.3.7/css/bootstrap.css" rel="stylesheet">
<style>
    .btn.btn-primary {
        background: #000;
        border-color: azure;
    }
    .container-login {
        max-width: 500px;
    }
</style>
<div class="container container-login">
    <h1>登录</h1>
    <form>
        <div class="alert alert-success">登录成功~ 正在跳转...</div>
        <div class="form-group">
            <label>用户名</label>
            <input class="form-control" type="text">
        </div>
        <div class="form-group">
            <label>密码</label>
            <input class="form-control" type="password">
        </div>
        <div class="form-group">
            <button class="btn btn-primary btn-block" type="submit">登录</button>
        </div>
    </form>
</div>
```

**栅格系统**

```css
# 默认母元素12份,col-md-3,代表占用3列.md表示屏幕尺寸为中尺寸,sm是小尺寸,xs极小尺寸
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <link href="https://cdn.bootcss.com/bootstrap/3.3.7/css/bootstrap.css" rel="stylesheet">
</head>
<body>
    <div class="col-sm-4">
        <h2>侧栏</h2>
        <div>首页</div>
    </div>
    <div class="col-sm-4">
        <h1>内容</h1>
        <p>Bootstrap是Twitter推出的一个用于前端开发的开源工具包。它由Twitter的设计师Mark Otto和Jacob Thornton合作开发,是一个CSS/HTML框架。</p>
    </div>
    <div class="col-sm-4">
        <h3>附侧栏</h3>
        <p>Bootstrap是Twitter推出的一个用于前端开发的开源工具包。它由Twitter的设计师Mark Otto和Jacob Thornton合作开发,是一个CSS/HTML框架。</p>
    </div>
</body>
</html>
```

**表单**

```css
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <link href="https://cdn.bootcss.com/bootstrap/3.3.7/css/bootstrap.css" rel="stylesheet">
    <style>
        .container-reg {
            max-width: 500px;
        }
    </style>
</head>
<body>
<form class="container container-reg">
    <h1>注册</h1>
    <div class="form-group form-inline">
        <div class="form-group has-error">
            <label class="control-label">姓名</label>
            <input class="form-control input-lg" type="text">
        </div>
        <div class="form-group has-success">
            <label class="control-label">电话</label>
            <input class="form-control input-sm" type="text">
        </div>
    </div>
    <div class="form-group">
        <label>充值金额</label>
        <div class="input-group">
            <div class="input-group-addon">¥</div>
            <input class="form-control" type="text">
        </div>
    </div>
    <div class="form-group has-warning">
        <label class="control-label">来自</label>
        <select class="form-control">
            <option value="1">北京昌平回龙观</option>
            <option value="1">北京昌平回龙观</option>
            <option value="1">北京昌平回龙观</option>
        </select>
    </div>
    <div class="row">
        <div class="col-sm-4">
            <input class="form-control" type="text" placeholder="XXXXXX">
        </div>
        <div class="col-sm-4">
            <input class="form-control" type="text">
        </div>
        <div class="col-sm-4">
            <input class="form-control" type="text">
        </div>
    </div>
</form>
</body>
</html>
```

**按钮**

```css
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <link href="https://cdn.bootcss.com/bootstrap/3.3.7/css/bootstrap.css" rel="stylesheet">
</head>
<body>
<div class="well">
    <p>
        <button class="btn btn-default">戳我</button>
        <button class="btn btn-primary">戳我</button>
        <button class="btn btn-danger">戳我</button>
        <button class="btn btn-warning">戳我</button>
        <button class="btn btn-info">戳我</button>
        <a class="btn btn-default" href="https://baidu.com">Baidu</a>
        <input class="btn btn-default" type="submit" value="按钮">
    </p>
    <p>
        <button class="btn btn-primary btn-lg">戳我</button>
        <button class="btn btn-primary">戳我</button>
        <button class="btn btn-primary btn-sm">戳我</button>
        <button class="btn btn-primary btn-xs">戳我</button>
    </p>
    <p>
        <button class="btn btn-primary btn-block">戳我</button>
    </p>
    <p>
        <button class="btn btn-default">戳我</button>
        <button class="btn btn-default active">戳我</button>
        <button class="btn btn-default" disabled="disabled">戳我</button>
    </p>
</div>
</body>
</html>
```

**按钮组**

```css
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <link href="https://cdn.bootcss.com/bootstrap/3.3.7/css/bootstrap.css" rel="stylesheet">
</head>
<body>
<div class="well">
    <div class="btn-toolbar">
        <div class="btn-group btn-group-lg">
            <button class="btn btn-default">戳我</button>
            <button class="btn btn-default">戳我</button>
            <button class="btn btn-default">戳我</button>
        </div>
        <div class="btn-group">
            <button class="btn btn-default">戳我</button>
            <button class="btn btn-default">戳我</button>
            <button class="btn btn-default">戳我</button>
        </div>
        <div class="btn-group btn-group-sm">
            <button class="btn btn-default">戳我</button>
            <button class="btn btn-default">戳我</button>
            <button class="btn btn-default">戳我</button>
        </div>
        <div class="btn-group btn-group-xs">
            <button class="btn btn-default">戳我</button>
            <button class="btn btn-default">戳我</button>
            <button class="btn btn-default">戳我</button>
        </div>
    </div>
    <br>
    <div class="btn-group-vertical">
        <button class="btn btn-default">戳我</button>
        <button class="btn btn-default">戳我</button>
        <button class="btn btn-default">戳我</button>
    </div>
</div>
</body>
</html>
```

**导航\(局部\)**

```css
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <link href="https://cdn.bootcss.com/bootstrap/3.3.7/css/bootstrap.css" rel="stylesheet">
    <style>
        body {
            max-width: 500px;
            margin: 20px auto;
        }
    </style>
</head>
<body>
    <ul class="nav nav-tabs nav-justified">
        <li class="active"><a href="#">登录</a></li>
        <li><a href="#">注册</a></li>
        <li><a href="#">忘记密码</a></li>
    </ul>
    <div>
        <h2>登录</h2>
        Bootstrap是Twitter推出的一个用于前端开发的开源工具包。它由Twitter的设计师Mark Otto和Jacob Thornton合作开发,是一个CSS/HTML框架。
    </div>
    <br>
    <br>


    <ul class="nav nav-pills">
        <li class="active"><a href="#">登录</a></li>
        <li><a href="#">注册</a></li>
        <li><a href="#">忘记密码</a></li>
    </ul>
    <div>
        <h2>登录</h2>
        Bootstrap是Twitter推出的一个用于前端开发的开源工具包。它由Twitter的设计师Mark Otto和Jacob Thornton合作开发,是一个CSS/HTML框架。
    </div>
    <br>
    <br>


    <div class="row">
        <div class="col-xs-4">
            <ul class="nav nav-pills nav-stacked">
                <li class="active"><a href="#">登录</a></li>
                <li><a href="#">注册</a></li>
                <li><a href="#">忘记密码</a></li>
            </ul>
        </div>
        <div class="col-xs-8">
            <div>
                <h2>登录</h2>
                Bootstrap是Twitter推出的一个用于前端开发的开源工具包。它由Twitter的设计师Mark Otto和Jacob Thornton合作开发,是一个CSS/HTML框架。
            </div>
        </div>
    </div>
</body>
</html>
```

**导航栏\(整站\)**

```css
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <link href="https://cdn.bootcss.com/bootstrap/3.3.7/css/bootstrap.css" rel="stylesheet">
</head>
<body>
    <div class="navbar navbar-default">
        <div class="container">
            <div class="navbar-header">
                <a href="#" class="navbar-brand">Lartisan</a>
            </div>
            <ul class="nav navbar-nav">
                <li><a href="#">首页</a></li>
                <li><a href="#">产品</a></li>
                <li><a href="#">联系我们</a></li>
            </ul>
            <form class="navbar-form navbar-left">
                <div class="form-group">
                    <input class="form-control" type="text">
                </div>
                <button type="submit" class="btn btn-default">搜索</button>
            </form>
            <ul class="nav navbar-nav navbar-right">
                <li><a href="#">登录</a></li>
                <li><a href="#">注册</a></li>
            </ul>
        </div>
    </div>
    <div class="container">
        <div>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Dolores, maiores, modi. Blanditiis delectus
            dolorum eligendi enim eos inventore itaque maxime minus officiis, quis quisquam ratione repellat sequi
            tempora tempore. Esse.
        </div>
        <div>Atque delectus eius in labore omnis? Architecto corporis cum distinctio ducimus id ipsa magni mollitia qui
            recusandae tempora? Ad aspernatur doloremque doloribus expedita iste maiores odio provident, quae quidem
            temporibus!
        </div>
        <div>A architecto at consectetur dolorum, ducimus est, ex illo ipsum iure laboriosam nam officiis, quae quidem
            quos soluta sunt voluptatibus. Aliquid cupiditate debitis ex laboriosam molestiae nisi perspiciatis quas
            velit.
        </div>
        <div>Ab aspernatur commodi corporis deleniti distinctio dolorem enim fugiat in ipsam iure iusto molestiae
            necessitatibus nemo nisi nulla numquam, officia pariatur perferendis placeat porro qui quia sunt ut. Amet,
            voluptas.
        </div>
        <div>Ad, architecto asperiores culpa cum delectus deleniti esse facilis fugit ipsam iusto laboriosam molestiae
            non numquam quod reiciendis sapiente sed tenetur! Architecto autem nisi perferendis quidem. Deserunt fugit
            magnam neque?
        </div>
        <div>Aliquid dignissimos dolorem ea fugiat, harum illum iusto numquam omnis reiciendis rem reprehenderit
            repudiandae rerum sit soluta sunt? Accusamus commodi dolorem dolores, fugit hic labore non officia quam qui
            ut.
        </div>
        <div>At atque aut doloribus excepturi facilis illo inventore ipsa molestias nesciunt obcaecati provident
            quaerat, quia reiciendis sapiente similique tempore ut vero? Accusamus adipisci delectus distinctio ipsum
            non quis, temporibus voluptatem!
        </div>
        <div>A, aliquid aperiam aut cum fugit ipsa maxime neque perspiciatis quae sint temporibus voluptate
            voluptatibus. Accusamus earum enim impedit magni mollitia, nam perferendis rem ullam? Aliquid dolores harum
            reiciendis vitae!
        </div>
        <div>Deserunt dicta dignissimos, dolor error est eum facilis fuga fugiat in inventore iure labore laborum magnam
            molestiae molestias neque nesciunt numquam perspiciatis placeat quasi quo sint ullam unde velit voluptates.
        </div>
        <div>A ab accusantium asperiores assumenda cupiditate delectus dolor, earum et eum eveniet impedit libero magnam
            modi neque nobis obcaecati perferendis qui quis quos repellat sapiente similique suscipit tempora vel
            veniam.
        </div>
    </div>
</body>
</html>
```

**面板**

```css
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <link href="https://cdn.bootcss.com/bootstrap/3.3.7/css/bootstrap.css" rel="stylesheet">
    <style>
        body {
            max-width: 400px;
            margin: 20px auto;
        }
    </style>
</head>
<body>
    <div class="panel panel-default">
        <div class="panel-heading">
            <div class="panel-title">用户统计</div>
            <div class="small text-muted">每日用户情况统计</div>
        </div>
        <div class="panel-body">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Adipisci, commodi dolore ea eaque est eveniet facere id ipsam, itaque iure nemo odit officiis omnis perferendis quas quidem quisquam similique voluptatibus.
        </div>
        <div class="panel-footer">
            <div class="small text-muted">
                数据更新于5秒钱
            </div>
        </div>
    </div>
    <div class="panel panel-success">
        <div class="panel-heading">用户统计</div>
        <div class="panel-body">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Adipisci, commodi dolore ea eaque est eveniet facere id ipsam, itaque iure nemo odit officiis omnis perferendis quas quidem quisquam similique voluptatibus.
        </div>
    </div>
    <div class="panel panel-warning">
        <div class="panel-heading">用户统计</div>
        <div class="panel-body">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Adipisci, commodi dolore ea eaque est eveniet facere id ipsam, itaque iure nemo odit officiis omnis perferendis quas quidem quisquam similique voluptatibus.
        </div>
    </div>
    <div class="panel panel-danger">
        <div class="panel-heading">用户统计</div>
        <div class="panel-body">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Adipisci, commodi dolore ea eaque est eveniet facere id ipsam, itaque iure nemo odit officiis omnis perferendis quas quidem quisquam similique voluptatibus.
        </div>
    </div>
    <div class="panel panel-info">
        <div class="panel-heading">用户统计</div>
        <div class="panel-body">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Adipisci, commodi dolore ea eaque est eveniet facere id ipsam, itaque iure nemo odit officiis omnis perferendis quas quidem quisquam similique voluptatibus.
        </div>
    </div>
</body>
</html>
```

**表格**

```css
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <link href="https://cdn.bootcss.com/bootstrap/3.3.7/css/bootstrap.css" rel="stylesheet">
    <style>
        body {
            max-width: 400px;
            margin: 20px auto;
        }
    </style>
</head>
<body>
    <table class="table">
        <thead>
            <tr>
                <th>用户名</th>
                <th>邮箱</th>
                <th>注册于</th>
            </tr>
        </thead>
        <tbody>
            <tr class="success">
                <td>小明</td>
                <td>xiaoming@baidu.com</td>
                <td>2012-12-21</td>
            </tr>
            <tr class="danger">
                <td>小红</td>
                <td>xiaohong@baidu.com</td>
                <td>2012-12-21</td>
            </tr>
            <tr class="warning">
                <td>小花</td>
                <td>xiaohua@baidu.com</td>
                <td>2012-12-21</td>
            </tr>
            <tr class="info">
                <td>小强</td>
                <td>xiaoqiang@baidu.com</td>
                <td>2012-12-21</td>
            </tr>
        </tbody>
    </table>
    <table class="table table-striped">
        <thead>
        <tr>
            <th>用户名</th>
            <th>邮箱</th>
            <th>注册于</th>
        </tr>
        </thead>
        <tbody>
        <tr>
            <td>小明</td>
            <td>xiaoming@baidu.com</td>
            <td>2012-12-21</td>
        </tr>
        <tr>
            <td>小红</td>
            <td>xiaohong@baidu.com</td>
            <td>2012-12-21</td>
        </tr>
        <tr>
            <td>小花</td>
            <td>xiaohua@baidu.com</td>
            <td>2012-12-21</td>
        </tr>
        </tbody>
    </table>
    <table class="table table-hover">
        <thead>
        <tr>
            <th>用户名</th>
            <th>邮箱</th>
            <th>注册于</th>
        </tr>
        </thead>
        <tbody>
        <tr>
            <td>小明</td>
            <td>xiaoming@baidu.com</td>
            <td>2012-12-21</td>
        </tr>
        <tr>
            <td>小红</td>
            <td>xiaohong@baidu.com</td>
            <td>2012-12-21</td>
        </tr>
        <tr>
            <td>小花</td>
            <td>xiaohua@baidu.com</td>
            <td>2012-12-21</td>
        </tr>
        </tbody>
    </table>
    <table class="table table-bordered table-hover">
        <thead>
        <tr>
            <th>用户名</th>
            <th>邮箱</th>
            <th>注册于</th>
        </tr>
        </thead>
        <tbody>
        <tr>
            <td>小明</td>
            <td>xiaoming@baidu.com</td>
            <td>2012-12-21</td>
        </tr>
        <tr>
            <td>小红</td>
            <td>xiaohong@baidu.com</td>
            <td>2012-12-21</td>
        </tr>
        <tr>
            <td>小花</td>
            <td>xiaohua@baidu.com</td>
            <td>2012-12-21</td>
        </tr>
        </tbody>
    </table>
</body>
</html>
```

**其他组件**

```css
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <link href="https://cdn.bootcss.com/bootstrap/3.3.7/css/bootstrap.css" rel="stylesheet">
    <style>
        body {
            margin: 20px auto;
        }
    </style>
</head>
<body>
    <div class="col-xs-4">
        <div class="list-group">
            <a href="#" class="list-group-item">item</a>
            <a href="#" class="list-group-item">item</a>
            <a href="#" class="list-group-item">item</a>
            <a href="#" class="list-group-item">item</a>
        </div>
    </div>
    <div class="col-xs-8">
        <div>
            <div class="alert alert-success">OK~</div>
        </div>
        <ul class="breadcrumb">
            <li><a href="#">首页</a></li>
            <li><a href="#">列表</a></li>
            <li class="active">lorem <span class="badge">50K</span></li>
        </ul>
        <div>
            <h1>lorem</h1>
            <p>
                <span class="label label-success">Lorem</span>
                <span class="label label-warning">tag</span>
                <span class="label label-danger">标签</span>
            </p>
            <div>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Debitis dolorem earum error facere id impedit
                libero modi nobis obcaecati odio odit perspiciatis praesentium quod repellendus suscipit tempora, ullam,
                veniam voluptatibus.
            </div>
            <div>Animi, assumenda cumque dicta eaque error et eum facere facilis iste minus necessitatibus quidem,
                reiciendis reprehenderit sit sunt velit, veritatis! Blanditiis debitis eaque in ipsum maiores nobis
                perferendis <span class="label label-default">quasi</span> sapiente.
            </div>
            <div>Commodi debitis deleniti dolor dolorum eveniet illum ipsam itaque, labore minus nihil officia placeat
                repellat voluptatem. Ab aliquid est facere, incidunt, libero maiores minima nam nemo perferendis porro rem
                rerum.
            </div>
            <div>Ad expedita facilis laudantium minima omnis possimus tempore voluptatem! Cupiditate eaque inventore nam
                quisquam repellat! At, corporis debitis delectus eligendi ex inventore ipsa laudantium nam necessitatibus
                odio, praesentium recusandae totam!
            </div>
            <div>
                <button class="btn btn-info">赞 <span class="badge">10</span></button>
            </div>
        </div>
        <ul class="pagination">
            <li><a href="#">上一页</a></li>
            <li class="active"><a href="#">1</a></li>
            <li><a href="#">2</a></li>
            <li><a href="#">3</a></li>
            <li><a href="#">下一页</a></li>
        </ul>
        <ul class="pager">
            <li><a href="#">上一页</a></li>
            <li><a href="#">1</a></li>
            <li class="active"><a href="#">2</a></li>
            <li class="disabled"><a href="#">3</a></li>
            <li class="disabled"><a href="#">下一页</a></li>
        </ul>
    </div>
</body>
</html>
```



