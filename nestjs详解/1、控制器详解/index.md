**Controller Request （获取前端传过来的参数）** [nestjs](https://so.csdn.net/so/search?q=nestjs&spm=1001.2101.3001.7020) 提供了方法参数装饰器 用来帮助我们快速获取参数 如下 

| @Request()              | req                              |
| :---------------------- | -------------------------------- |
| @Response()             | res                              |
| @Next()                 | next                             |
| @Session()              | req.session                      |
| @Param(key?: string)    | `req.params`/`req.params[key]`   |
| @Body(key?: string)     | `req.body`/`req.body[key]`       |
| @Query(key?: string)    | `req.query`/`req.query[key]`     |
| @Headers(name?: string) | `req.headers`/ req.headers[name] |

 调试工具可以使用[postMan](https://so.csdn.net/so/search?q=postMan&spm=1001.2101.3001.7020) ApiFox 等 

 下载地址 [Apifox - API 文档、调试、Mock、测试一体化协作平台 - 接口文档工具，接口自动化测试工具，接口Mock工具，API文档工具，API Mock工具，API自动化测试工具](https://www.apifox.cn/?utm_source=baidu_sem1) 

![](D:\cwb\typora文件\内容图片\74fbf871d5004e58abe3fba981b2fbb2.png)

**1、获取get请求参数**

 可以使用Request[装饰器](https://so.csdn.net/so/search?q=装饰器&spm=1001.2101.3001.7020) 或者 Query 装饰器 跟express 完全一样 

![](D:\cwb\typora文件\内容图片\9f673fd619b643ebad0d0d02cadb02e8.png)

 也可以使用Query 直接获取 不需要在通过req.query 了 

![](D:\cwb\typora文件\内容图片\3957dc61a1cc4719b92ae236a59d7c89.png)

```js
import { Controller, Get, Post, Body, Patch, Param, Delete, Version, Request, Query } from '@nestjs/common';
import { UserService } from './user.service';
import { CreateUserDto } from './dto/create-user.dto';
import { UpdateUserDto } from './dto/update-user.dto';
 
@Controller('user')
export class UserController {
  constructor(private readonly userService: UserService) { }
 
  @Get()
  find(@Query() query) {
    console.log(query)
    return { code: 200 }
  }
}
```



**2、获取参数**

 可以使用Request装饰器 或者 Body 装饰器 跟express 完全一样 

![](D:\cwb\typora文件\内容图片\210ac37854714438a5f2c2b5385967b4.png)

 或者直接使用Body 装饰器 

![](D:\cwb\typora文件\内容图片\d54ed57d83b24ae38377e1c0d0e17372.png)

 也可以直接读取key 

![](D:\cwb\typora文件\内容图片\33454cfde24b46b6b0ede32eb89bbf82.png)

```js
import { Controller, Get, Post, Body, Patch, Param, Delete, Version, Request, Query } from '@nestjs/common';
import { UserService } from './user.service';
import { CreateUserDto } from './dto/create-user.dto';
import { UpdateUserDto } from './dto/update-user.dto';
 
@Controller('user')
export class UserController {
  constructor(private readonly userService: UserService) { }
 
  @Get()
  find(@Query() query) {
    console.log(query)
    return { code: 200 }
  }
 
  @Post()
  create (@Body() body) {
     
    console.log(body)
 
    return {
       code:200
    }
  }
}
```



**3、动态路由**

 可以使用Request装饰器 或者 Param 装饰器 跟express 完全一样 

![](D:\cwb\typora文件\内容图片\b790aeebe8f444488f721491cb2581a9.png)

![](D:\cwb\typora文件\内容图片\96a5bc5570df4d24a976347017d1517e.png)

```js
import { Controller, Get, Post, Body, Patch, Param, Delete, Version, Request, Query } from '@nestjs/common';
import { UserService } from './user.service';
import { CreateUserDto } from './dto/create-user.dto';
import { UpdateUserDto } from './dto/update-user.dto';
 
@Controller('user')
export class UserController {
  constructor(private readonly userService: UserService) { }
 
  @Get()
  find(@Query() query) {
    console.log(query)
    return { code: 200 }
  }
 
  @Post()
  create (@Body('name') body) {
     
    console.log(body)
 
    return {
       code:200
    }
  }
 
  @Get(':id')
  findId (@Param() param) {
     
    console.log(param)
 
    return {
       code:200
    }
  }
}
```



**4、读取header信息**

 我在调试工具随便加了一个cookie 

![](D:\cwb\typora文件\内容图片\1618ecf69b214bd49fffeab19abb897c.png)

```js
import { Controller, Get, Post, Body, Patch, Param, Delete, Version, Request, Query, Ip, Header, Headers } from '@nestjs/common';
import { UserService } from './user.service';
import { CreateUserDto } from './dto/create-user.dto';
import { UpdateUserDto } from './dto/update-user.dto';
 
@Controller('user')
export class UserController {
  constructor(private readonly userService: UserService) { }
 
  @Get()
  find(@Query() query) {
    console.log(query)
    return { code: 200 }
  }
 
  @Post()
  create (@Body('name') body) {
     
    console.log(body)
 
    return {
       code:200
    }
  }
 
  @Get(':id')
  findId (@Headers() header) {
     
    console.log(header)
 
    return {
       code:200
    }
  }
}
```



**5、状态码**

使用 HttpCode 装饰器 控制接口返回的状态码 

![img](D:\cwb\typora文件\内容图片\d3fc2406b79f40c296f9bba4223b80c8.png)

```js
import { Controller, Get, Post, Body, Patch, Param, Delete, Version, Request, Query, Ip, Header, Headers, HttpCode } from '@nestjs/common';
import { UserService } from './user.service';
import { CreateUserDto } from './dto/create-user.dto';
import { UpdateUserDto } from './dto/update-user.dto';
 
@Controller('user')
export class UserController {
  constructor(private readonly userService: UserService) { }
 
  @Get()
  find(@Query() query) {
    console.log(query)
    return { code: 200 }
  }
 
  @Post()
  create (@Body('name') body) {
     
    console.log(body)
 
    return {
       code:200
    }
  }
 
  @Get(':id')
  @HttpCode(500)
  findId (@Headers() header) {
    return {
       code:500
    }
  }
}
```