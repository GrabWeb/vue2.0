# gshop

> A Vue.js project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).

前言

后台是从网上down下来的，接口里面有一部分，另一部分是用mock模拟。



### 服务器：

根目录有一个gshop-server.rar，解压到磁盘其它目录后运行npm start，开启服务器，默认3000端口。

### 项目启动

下载下来后，运行
```
npm i     //安装依赖
```
然后在根目录运行 
```
npm run dev     //启动项目，默认8080端口。
```
登陆账号为abc，密码为123



### 项目预览：

一个仿外卖的vue单页应用程序Web App（spa），包含常见的功能


# 技术选型与项目结构

## 技术选型



## 路由




## 项目结构



# 项目一些准备与说明

## 项目测试与打包发布

1. gshop-client_blank文件到项目文件（使用的是vue-cli2.0版本）下
2. 修改gshop-client_blank文件名称为gshop-client
3. 将gshop-client中的package.json里的"name": "gshop"改为自己的项目名称gshop-client
4. 在此文件夹中的config文件夹中修改index.js里的autoOpenBrowser属性改为true，这样在运行时就会自动打开网页

开发环境打包运行

在gshop-client路径的cmd命令行中运行npm run dev打包

生产环境打包运行

1. 在gshop-client路径的cmd命令行中运行npm run build打包，然后文件目录会生成一个dist文件夹，就是打包压缩可以上线的文件
2. 下载serve（应该是个包），npm install -g serve
3. 在gshop-client文件夹中运行serve dist，就可以访问5000端口（这里报错了，页面显示找不到path，因为端口被占用，把其它东西都关了即可）



## 关于字体图标

1. 阿里巴巴矢量图标网站
2. 在index.html中添加link标签
3. 把购物车中的整体链接粘贴到link标签中
4. 通过类名来使用
5. 要使用2个类名，第一个是iconfont，第二个就是字体的类名



## 使用git提交项目到github

1. git init 
2. git add .
3. git commit -m "描述"
4. git pull
5. git push
(若是第一次提交，经过一二步后，可在github创建新项目后根据提示进行操作)


# 项目开始

## 安装stylus

```
cnpm install stylus -D
cnpm install stylus-loader -D
```

- 测试

把App.vue文件的style里面加上 lang="stylus" ，启动npm run dev ，完美运行


根据目录结构创建底部和路由的vue文件


## 公共样式文件(共用样式)

1. 按项目目录重新创建
2. 在common中创建stylus文件夹，创建mixins.styl
3. 在vue模版中，给style增加  lang="stylus" rel="stylesheet/stylus"
4. 在static文件夹中创建style文件夹，创建reset.css


## 创建基本文件让项目可以运行

1. 创建App.vue和main.js

2. 成功启动了项目（要先安装stylus）
```
npm install stylus stylus-loader --save-dev
```

## index.html的移动端配置

- viewport

  ```html
  <meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0,minimum-scale=1.0,user-scalable=no">
  ```

- 解决0.3s延时

在head标签上面添加

```javascript
<script src="https://as.alipayobjects.com/g/component/fastclick/1.0.6/fastclick.js"></script>

<script>
	if ('addEventListener' in document) {
		document.addEventListener('DOMContentLoaded', function() {
		FastClick.attach(document.body);
		}, false);
	}
	if(!window.Promise) {
		document.writeln('<script src="https://as.alipayobjects.com/g/component/es6-promise/3.2.2/es6-promise.min.js"'+'>'+'<'+'/'+'script>');
	}
</script>
```



## 路由搭建

### 思路重点

1. main.js 是主入口文件
2. App.vue 文件作为大的外层架子，所有的内容都在app.vue 上面呈现。
3. main.js 的 el 控制 index.html
4. main.js 引入 App.vue 文件，实例化一个Vue
5. 通过 render ，让 App.vue 的内容 ，全替换掉 index.html 里 ID 为 app 的 div 区域
6. App.vue 里面，自然要把路由的 view 放进去了


### 安装

```
npm install vue-router
```

### 引入（在main.js）

```javascript
import VueRouter from 'vue-router'
Vue.use(VueRouter)
import router from './router/router.js'

tips:
//挂载到实例上
//一旦配置了router
//就多了3个标签和2个属性
//router-view router-link keep-alive
//$route(配置路由)   $router(路由器)      
//怎么用法要复习
```

### 配置路由

（在 router.js 中引入路由模版）

### App.vue

分析：

1. 页面由2个部分组成，上面是路由，下面的底部导航
2. 引入底部vue文件，挂载到conponents属性中

> tips
>
> 如果初始化的时候已经选了严格模式，解决：
>
> 直接把config/index.js里面的dev属性，useEslint设置为false



## 组件FooterGuide.vue

这是App底部的导航

1. 通过编程式导航实现路由的切换显示（$router）

2. 通过动态class和$route.path来实现tab样式切换

3. 通过阿里图标库, 显示导航图标

## 各导航路由组件——4个路由页面的


Msite.vue

Order.vue

Search.vue

Profile.vue



## 组件HeadTop.vue

由于顶部导航的内容有变化，可以看作和路由是一体的，所以可以提取成一个模块，提高复用性

1. 新建一个 HeadTop.vue
2. 让其它路由页面引入 HeadTop.vue 



## 使用slot插槽（vue内置语法，父传子）

HeadTop.vue 这个头部导航，根据每个路由不同，内容也变化，所以单独提取出来以后，要通过组件之间传值的方式，把父组件的title传给 HeadTop.vue。

如：

 Order.vue

```javascript
<template>
      <HeaderTop :title="title">
          <span class="header_search" slot="left">
              <i class="iconfont icon-sousuo"></i>
          </span>

          <span class="header_login" slot="right">
              <span class="header_login_text">登录|注册</span>
          </span>

</HeaderTop> 
</template>

<script>
  import HeaderTop from '../../components/HeaderTop/HeaderTop.vue'
  export default {
    data(){
      return {
        title:'订单列表'
      }
    },
    components:{
      HeaderTop
    }
  }
</script>
```

HeadTop.vue

```javascript
<template>
  <header class="header">
    <slot name="left"></slot>
    
    <span class="header_title">
    <span class="header_title_text ellipsis"> {{title}} </span>
    </span>
    
    <slot name="right"></slot>
  </header>
</template>

<script>
  export default {
    props:['title']
  }
</script>
```



## 使用swiper插件（首页轮播滑动插件）

可参考官方文档 [Swiper地址](http://www.swiper.com.cn/)

1. 安装

   ```
   npm install --save swiper
   ```

2. 在需要使用的页面（Msite.vue）引入

   ```javascript
   import Swiper from 'swiper'
   import 'swiper/dist/css/swiper.min.css'
   ```

3. html结构如下

   - 在写页面结构的时候，类名已经按这样写完毕，所以Msite不要动了

   ```html
   <div class="swiper-container">
       <div class="swiper-wrapper">
           <div class="swiper-slide">Slide 1</div>
           <div class="swiper-slide">Slide 2</div>
           <div class="swiper-slide">Slide 3</div>
       </div>
       <!-- 如果需要分页器 -->
       <div class="swiper-pagination"></div>
       
       <!-- 如果需要导航按钮 -->
       <div class="swiper-button-prev"></div>
       <div class="swiper-button-next"></div>
       
       <!-- 如果需要滚动条 -->
       <div class="swiper-scrollbar"></div>
   </div>
   ```

4. 在页面（Msite.vue）添加一个钩子函数，初始化Swiper

   ```javascript
   mounted(){
     new Swiper ('.swiper-container', {
       loop: true,
       // 如果需要分页器
       pagination: {
         el: '.swiper-pagination',
       }
     })
   }
   ```

## 组件ShopList.vue（把首页的 ShopList 商家列表单独提取出来）

1. 新建文件，在components新建ShopList，（和HeaderTop一样，都属于一般组件）
2. 在Msite.vue中引入 ShopList.vue ，并注册成组件，在模版中使用

> tips
>
> - 首页滑动到了一个位置，点击其它路由，锚点还在那个高度
> - 解决：给路由页面的模版内的外层容器添加，overflow：hidden

## 后台

### 启动后台

后台是基于node.js开发的，现成的

1. gshop-serve文件夹（服务器代码文件夹），进入里面，运行命令行（确保安装了mongodb并已启动）

   ```
   npm start 
   ```

2. 如何查看端口号：里面的bin文件夹有个www文件，里面有端口号，是4000

### postman

1. postman是用来测试API接口的chrome插件
2. 注册登陆
3. 创建调试集合名字gshop-client



## axios（前后台交互）

1. 安装

   ```
   npm install --save axios
   ```

2. 封装ajax请求模块

  - api/ajax.js  (ajax请求函数模块)

   ```js
   import axios from 'axios'

   export default function ajax(url = '', data = {}, type = 'GET') {
      return new Promise(function (resolve, reject) {
        let promise
        if (type === 'GET') {
          // 准备url query 参数数据
          let dataStr = '' //数据拼接字符串
          Object.keys(data).forEach(key => {
            dataStr += key + '=' + data[key] + '&'
          })
          if (dataStr !== '') {
              dataStr = dataStr.substring(0, dataStr.lastIndexOf('&'))
              url = url + '?' + dataStr
          }
          // 发送get 请求
          promise = axios.get(url)
        } else {
          // 发送post 请求
          promise = axios.post(url, data)
        }

        promise.then(response => {
          resolve(response.data)
        })
          .catch(error => {
            reject(error)
          })
      })
  }
   ```

  - api/index.js  (与后台交互模块) 

  ```js
  import ajax from './ajax'

  /**
    * 获取地址信息(根据经纬度串)
    */
  export const reqAddress = geohash => ajax('/api/position/' + geohash)

  /**
    * 获取msite 页面食品分类列表
    */
  export const reqCategorys = () => ajax('/api/index_category')

  /**
    * 获取msite 商铺列表(根据经纬度)
    */
  export const reqShops = ({latitude, longitude}) => ajax('/api/shops', {latitude, longitude})

  /**
    * 账号密码登录
    */
  export const reqPwdLogin = (name, pwd, captcha) => ajax('/api/login_pwd', {
name, pwd, captcha}, 'POST')

  /**
    * 获取短信验证码
    */
  export const reqSendCode = phone => ajax('/api/sendcode', {phone})

  /**
    * 手机号验证码登录
    */
  export const reqSmsLogin = (phone, code) => ajax('/api/login_sms', {phone, code}, 'POST')

  /**
    * 获取用户信息(根据会话)
    */
  export const reqUser = () => ajax('/api/userinfo')

  /**
    * 请求登出
    */
  export const reqLogout = () => ajax('/api/logout')
  ```

3. 配置代理，代理目标的基础路径，支持跨域

   - 在config的index.js配置文件的dev中，添加proxyTable，使用api替代服务器地址	

   - 修改 index.js配置

   ```
   proxyTable: {

      '/api': { // 匹配所有以'/api'开头的请求路径
          target: 'http://localhost:4000', // 代理目标的基础路径
          changeOrigin: true, // 支持跨域
          pathRewrite: {// 重写路径: 去掉路径中开头的'/api'
            '^/api': ''
          }
       }
   }
   ```

4. 然后在调用接口的时候直接使用/api，后面接上接口的其他路径信息，就可以，如：

   ```
   '/api/position/40.10038,116.36120'
   ```

## Vuex状态管理

安装

```
npm install --save vuex
```


### 在目录结构下的store，创建vuex仓库



### 如何将 vuex 在项目中使用

1. 1. 在 store 中的 index.js 引入相关模块

      ```js
      //index.js
      import Vue from 'vue'
      import Vuex from 'vuex'
      Vue.use(Vuex)
      ```

   2. 再导出一个vuex实例

      ```js
      //index.js
      export default new Vuex.Store({})
      ```

   3. 然后在 main.js 主入口中引入vuex主文件

      ```js
      //main.js
      import store from './store/index.js'
      ```

   4. 挂载store

      ```js
      //main.js
      new Vue({
        el: '#app',
        render: c => c(App),
        router: router,
        store
      })
      ```

### 在vuex核心文件里，写相应的内容

1. index.js（把vuex模块分开写，然后引入主文件里）

   ```js
   import Vue from 'vue'
   import Vuex from 'vuex'
   Vue.use(Vuex)
   
   import state from './state'
   import mutations from './mutations'
   import getters from './getters'
   import actions from './actions'
   
   export default new Vuex.Store({
     state,
     mutations,
     getters,
     actions,
   })
   ```

2. state.js

   ```js
   export default {
     name:'laoliu',
     latitude: 40.10038, // 纬度
     longitude: 116.36867, // 经度
     address: {}, // 地址信息对象
     categorys: [], // 分类数组
     shops: [], // 商家数组
   }
   ```

3. mutations-types.js

   ```js
   export const RECEIVE_ADDRESS = 'receive_address' // 接收地址信息
   export const RECEIVE_CATEGORYS = 'receive_categorys' // 接收分类数组
   export const RECEIVE_SHOPS = 'receive_shops' // 接收商家数组
   ```

4. mutations.js  （mutation 的主要用来处理state里面的数据，交互异步的东西给actions做）

   ```js
   import {RECEIVE_ADDRESS,RECEIVE_CATEGORYS,RECEIVE_SHOPS} from './mutations-types'
   
   export default {
     [RECEIVE_ADDRESS](state,address){
       state.address = address
     },
     [RECEIVE_CATEGORYS](state,categorys){
       state.categorys = categorys
     },
     [RECEIVE_SHOPS](state,shops){
       state.shops = shops
     }
   }
   ```

5. actions.js

> tips:
>
> 浏览器跨域的一种方式：配置代理。
>
> 浏览器有一个自带的代理服务器，监听本地端口，想跨域，就修改这个代理服务器的配置，用一种“欺骗”的行为达到跨域的目的

```js

  import {reqAddress, reqCategorys, reqShops} from '../api'
  import {RECEIVE_ADDRESS, RECEIVE_CATEGORYS, RECEIVE_SHOPS} from './mutation-types'

  export default {
    // 异步获取地址
    async getAddress({commit, state}) {
      const geohash = state.latitude + ',' + state.longitude
      const result = await reqAddress(geohash)
      commit(RECEIVE_ADDRESS, {address: result.data})
    },

    // 异步获取分类列表
    async getCategorys({commit}) {
      const result = await reqCategorys()
      commit(RECEIVE_CATEGORYS, {categorys: result.data})
    },

    // 异步获取商家列表
    async getShops({commit, state}) {
      const {latitude, longitude} = state
      const result = await reqShops({latitude, longitude})
      commit(RECEIVE_SHOPS, {shops: result.data})
    }
  }
```

> tips:
>
> code的意思是： code为0的时候，返回数据
>
>

## 动态渲染 ShopList.vue （商家列表）

1. 因为需要用到 Actions 里的东西，所以要引入 mapActions 来触发 Actions 里的东西

   ```js
   import {mapActions} from 'vuex'
   
     export default {
     mounted:function () {
       this.$store.dispatch('receive_shops')
     },
     computed:{
       ...mapState(['shops']),
       ...mapActions(['receive_shops'])
     }
   }
   ```

2. Actions 里的异步请求得到的值会赋给 state 里面的 shops 变量（商家数组），要用state.shops来v-for渲染到dom，所以要引入 mapState

   ```js
   import {mapState} from 'vuex'
   ```

3. 使用v-for渲染DOM



## 动态渲染 Msite.vue （轮播的导航图）

思路：

1. receive_categorys 是个数组，长度是16，轮播有2个，每个8个小导航
2. 那么需要把16个元素分成8个一组，放进一个数组中，也就是一个二维数组[ [8个],[8个] ]
3. 为什么要弄成二维数组呢？为了v-for遍历渲染dom：
4. 外层的数组来决定几个轮播，内层的数组来遍历出来每一个小导航



1. 导航大海报可以滑动并轮播，所以要用到 sweiper 插件（上面已经安装引入过了）

2. 两个轮播，每个轮播有8个小导航，也就是“分组”，vuex里state.categorys

3. 在 Msite.vue 里要用到异步的 action 来获取 categorys，所以要引入过来

   ```js
   import {mapState} from 'vuex'
   ```

4. 映射这个map

   ```js
   computed:{
   //...mapActions(['receive_categorys']),      //这里应该是多余的，不注释掉，receive_categorys会触发2次（如果Actions里给这个方法打印一个123，这行也映射，就会执行2次）
     ...mapState(['categorys']),
   }	
   ```

5. 然后在生命周期 mounted 中分发 actions 里面的 receive_categorys 获取分组信息

   ```js
   mounted:function () {
     this.$store.dispatch('receive_categorys')
   }
   ```

6. 设定几个变量

   ```js
   data(){
     return {
       title:'好吃外卖',
       categorysArr:[],    //来接收vuex里面的 categorys 分组数组，好拿来计算，
       categorysOut:[],     //外层数组，来决定几个轮播
       categorysIn:[],      //内层数组，来决定每个轮播几个导航
       baseImg:'http://localhost:4000'    
     }
   }
   ```

7. 在 methods 中写一个方法，实现上面的思路，当 actions 分发 receive_categorys 异步获取到数据，赋值给state里面的 categorys ，categorys 上面被映射到本组件中了，所以categorys 存在变化，那么就可以用watch监听 categorys 。等在 watch 中监听到categorys有变化，就触发methods里面的 categorysArr() ，

> 注意：为什么不写在computed里，因为 computed 里面有data中的一些变量，会自动触发方法，当触发的时候，categorysArr还没有拿到值，异步获取的，拿到的时候，页面早已加载完了，所以会报错

```js
methods:{
  changeArr:function () {
    this.categorysArr.forEach((item)=> {
      if(this.categorysIn.length<8){
        this.categorysIn.push(item)
      }else{
        this.categorysOut.push(this.categorysIn)
        this.categorysIn=[]
        this.categorysIn.push(item)
      }
    })
    this.categorysOut.push(this.categorysIn)
  }
}
```



1. watch监听categorys：

   ```js
   watch:{
     categorys(){
       this.categorysArr = this.categorys
       this.changeArr()   //这里是把一维数组变成二维数组的方法
       this.$nextTick(()=>{
         new Swiper ('.swiper-container', {
           loop: true,
           // 如果需要分页器
           pagination: {
             el: '.swiper-pagination',
           }
         })
       })
     }
   }
   ```

2. v-for渲染dom，略，但是有个细节：关于img的src属性的语法

   ```html
   <div class="food_container">
     <!--<img src="./img/nav/1.jpg">-->
     <!--//这里是个坑，img的src前面要加bind，里面才能写表达式，而且，v-for遍历的属性不能加 {{}} 这个大括号-->
     <img :src="baseImg+category.image_url">
   </div>
   ```



## 补充加载中的提示图svg，提高用户体验


## 解决 ShopList.vue 商家列表中的星星消失问题

图片路径样式有问题



## 组件Star.vue——抽离star模块


> tips：关于stylus的&
>
> &，它是父级的引用
>
> form表单内，点击了任何按钮，都默认提交了表单



## 根据给star模块传的值，来动态生成星星

思路：

1. 父组件给Star组件传值，传2个，一个是评价分数，Star组件拿到后，渲染出全星、半星、空星，第二个是尺寸，Star组件里的星星，有2X和3X图区别，所以要给定尺寸
2. Star组件接收父组件的值
3. 动态生成全星、半星、空星
4. - 把rating计算成一个数组
   - 整数是全星，大于0.5才显示半星，5减去整数是空星
   - 把结果存入一个数组
   - 通过数组v-for遍历出来对应的on half off
5. 计算的思路：
6. - 判断rating.floor（）是否小大于1
   - 如果大于1，循环创建“on”，push进数组
   - 否则，判断是否有half
   - 最后的余数，生成“off”进数组



## Login.vue

> tips
>
> - 要了解 $router 相关的常用方法，如$router.back() 

1. 新建文件，Login.vue页面

2. 制作一个左上角回退的功能

   ```html
   给左上角的<增加一个点击 $router.back() 回退方法
   
   <a href="javascript:" class="go_back" @click="$router.back()">
     <i class="iconfont icon-jiantou2"><</i>
   </a>
   ```

3. 制作一个在Login页面底部导航不显示的功能

   - 配置路由的时候，加上mata属性

     ```js
     routes: [
       {path: '/', redirect: '/Msite', mata: {show: true}},
       {path: '/Msite', component: Msite, mata: {show: true}},
       {path: '/Search', component: Search, mata: {show: true}},
       {path: '/Order', component: Order, mata: {show: true}},
       {path: '/Profile', component: Profile, mata: {show: true}},
       {path: '/Login', component: Login, mata: {show: false}}
     ]
     ```

   - 在App.vue 中，给底部导航组件，添加v-show，属性为$router.meta设置的布尔值

   - 这样一来，在 FooterGuide 组件中，有v-show来控制底部导航组件是否显示

     ```html
     <FooterGuide v-show="$route.meta.show"></FooterGuide>
     ```

##  

### 切换登陆方式

显示哪种登录方式是用class中的“ON”来控制的

思路：

1. 使用true/flase来控制ON的显示和隐藏

   ```js
   //data中省名msg:true
   :class="{on:msg}"   
   :class="{on:!msg}"
   ```

2. 短信登陆界面ON，密码界面登陆的就取反

   ```js
   <a href="javascript:;" :class="{on:msg}" @click="msg=!msg">短信登录</a>
   <a href="javascript:;" :class="{on:!msg}" @click="msg=!msg">密码登录</a>
   ```

3. 同样，下面的关联div也是如此，使用同一个flag就可以了



手机号验证

1. 给手机号input添加一个v-model，变量为phone（为什么呢？因为接口文档的里面是phone，这样后面提交请求的服务器验证手机号是否存在时方便）

   ```js
   <input type="tel" maxlength="11" placeholder="手机号" v-model="phone">
   ```

2. 如果手机号输入格式正确，那么获取验证码的颜色由灰变为黑，

   - 此button的文字颜色是否变化，是根据变量phone来决定，所以此button要有一个计算属性
   - 颜色变化用一个类来表示
   - 那么就要绑定一个class，内容以对象的形式来添加

> tips：一个模版中能写的变量只有3种：promie、data、computed。什么叫模版中能写的变量呢？就是template里面的 {{ }} 大括号里的内容

```js
//绑定一个class，内容以对象的形势来添加
<button disabled="disabled" class="get_verification" :class="{color:phoneNum}">获取验证码</button>
//此button的文字颜色是否变化，是根据变量phone来决定，所以此button要有一个计算属性
computed:{
  phoneNum(){
    return /^1\d{10}$/.test(this.phone)
  }
}
//颜色变化用一个类来表示
.get_verification
  position absolute
  top 50%
  right 10px
  transform translateY(-50%)
  border 0
  color #ccc
  font-size 14px
  background transparent
  &.color                             //在get_verification下面增加&，表示是它的引用，也就是级别在它下面
    color black
```

1. 消除 disabled 的禁用input属性

- disabled 只能接受要么是true要么是NULL，false是无效的
- 错误写法:

```js
:disabled="{phoneNum?null:'disabled'}"
:disabled="{phoneNum?null:disabled}"
```

- 正确写法: 判断 phoneNum 验证正则的计算方法是否为true

```js
:disabled="phoneNum?null:'disabled'"
```



### 触发“获取验证码”显示，并且增加倒计时

> 如下错误的time()方法，多次点击，仍然触发多次定时器
>
> ```js
> //模版
> <button :disabled="phoneNum?null:'disabled'" class="get_verification" :class="{color:phoneNum}" @click="time()">获取验证码{{timeNum}}</button>
> //代码
> data(){
>     return{
>         timeNum:''
>     }
> },
> methods:{
>   time(){
>     if(tid){
>       clearTimeout(tid)
>     }
>     this.timeNum=this.timeMax
>     let tid = setInterval(()=> {
>       this.timeNum--
>       if(this.timeNum<=0){
>         clearInterval(tid)
>       }
>     },1000)
>   }
> }
> ```
>
> 正确的代码：
>
> tips:   0也是属于false
>
> ```js
> time(){
>     if(!this.timeNum){
>       this.timeNum = 30
>       let tid = setInterval(()=> {
>         this.timeNum--
>         if(this.timeNum<=0){
>           clearInterval(tid)
>         }
>       },1000)
>     }
> }
> ```



### 密码的显示/隐藏切换 

1. 圆球的移动
2. 开关背景的变色
3. input的type属性由tel和password切换