# koaDemo
koa learn

### Koa 开发环境搭建

要求Ndoe版本 > v7.6,因为node.js 7.6版本完全支持async /await, 不需要再加入flag，

查看Node 版本方法（win版本）

`
打开运行 快捷键 win + R  然后输入cmd 打开命令行工具，命令行输入
`

 > node -v

Mac 更新方法

```
sudo npm install -g n
sudo n stable
```
#### 搭建环境

- 建立文件目录
```
cd koaDemo  进入koaDemo 文件夹
mkdir koa2  创建koa2 文件夹
cd koa2     进入koa2 文件夹
```
- 初始化生产package.json 文件
```
npm init -y
```
- 生成package.json, 安装koa包， npm 安装
```
3种安装方式
$ nvm install 7
$ npm i koa
$ node my-koa-app.js
```
index.js
```
const Koa = require('koa');
const app = new Koa();

app.use(async(ctx) =>{
    ctx.body ="Hello world"
})

app.listen(3000);
console.log('app start');
```
运行  node index.js
```
http://127.0.0.1:3000
```

### 02 async/ await 用法

```
async function testAsync() {
    return 'Hello world';
}

const res = testAsync();
console.log(res); // Promise { 'Hello world' }
```

### get 请求接收 

在koa2中GET请求通过request接收，但是接受的方法有两种：query和querystring。
- query: 返回的是格式化好的参数对象
- querystring: 返回的是请求字符串

```
http://127.0.0.1:3000/?user=wangyi&age=12


{"url":"/?user=wangyi&age=12","req_query":{"user":"wangyi","age":"12"},"req_querystring":"user=wangyi&age=12"}
```

> 从request接受Get请求

```
let url = ctx.url;
let request = ctx.request;
let req_query = request.query;
let req_querystring = request.querystring;
```

> 从上下文直接获取get请求

```
let ctx_query = ctx.query;
let ctx_querystring = ctx.querystring;

```
