**nest --help 可以查看nestjs所有的命令**

 他的命令和 [angular](https://so.csdn.net/so/search?q=angular&spm=1001.2101.3001.7020)很像 

![](https://img-blog.csdnimg.cn/b56338e73ac148c4943f383fbebb9811.png)

 

**案例生成一个用户模块**

1. 生成 controller.ts

```
nest g co user
```

![](https://img-blog.csdnimg.cn/1a51af9b7d6f4727996cdc3d9867ee9c.png)

2. 生成 module.ts

```
nest g mo user
```

3. 生成 service.ts

```
nest g s user
```

![](https://img-blog.csdnimg.cn/9a1067993c094e4cb77e7b082201e161.png)

**以上步骤一个一个生成的太慢了我们可以直接使用一个命令生成[CURD](https://so.csdn.net/so/search?q=CURD&spm=1001.2101.3001.7020)**

```
nest g resource user
```

![](https://img-blog.csdnimg.cn/a2d4ced17e4a44ac9c2a2471307e80e9.png)

 第一次使用这个命令的时候，除了生成文件之外还会自动使用 `npm` 帮我们更新资源，安装一些额外的插件，后续再次使用就不会更新了。 

![](https://img-blog.csdnimg.cn/5c5aad4d1edc46af988b652b95c379ae.png)

 生成了一套标准的CURD 模板 