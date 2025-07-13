## 2025.5-3

#### 1.你做过小程序/了解哪些小程序框架吗？

我之前有简单了解过小程序开发，在接到面试后，了解到咱们的主要业务是小程序开发，我简单过了一下基础知识，并利用 uniapp 搭建了一个 tabBar 小案例，知道它是基于 Vue 的跨平台开发框架，可以一套代码同时编译到微信小程序、H5、App。我了解了它的页面跳转方式、生命周期、rpx 单位，以及常用 API，也看过 uni-ui 组件库。目前虽然还没完整做过实战项目，但可以快速上手

> “H5 页面”本质上还是传统网页，只是做成了**适配手机端的版本**

#### 2.uniapp 页面跳转方式有哪些？（uniapp/小程序）

在 uniapp 中主要使用 `uni.navigateTo`、`redirectTo`、`switchTab` 和 `reLaunch` 等方法进行页面跳转，具体根据是否是 tab 页、是否保留页面栈来选择

```js
uni.navigateTo({ url: '/pages/detail/detail' }) // 保留当前页
uni.redirectTo({ url: '/pages/home/home' })     // 替换当前页
uni.switchTab({ url: '/pages/index/index' })    // 切 tabBar 页面
uni.reLaunch({ url: '/pages/start/start' })     // 重启整个 App
```

#### 3.uniapp 生命周期

```js
onLoad(options)                                 // 页面加载时触发，接收参数
onShow()                                        // 页面显示时触发
onHide()                                        // 页面隐藏时触发
onUnload()                                      // 页面卸载时触发
```

#### 4.uniapp 常用API

```js
// 发起网络请求
uni.request({
  url: 'https://api.example.com/list',
  method: 'GET',
  success: (res) => {
    console.log(res.data)
  }
})

// 显示提示
uni.showToast({
  title: '成功',
  icon: 'success'
})

// 存储数据
uni.setStorageSync('token', 'abc123')

// 读取数据
const token = uni.getStorageSync('token')
```

#### 5.移动端适配是怎么做的？

小程序开发中主要使用 `rpx` 单位，它可以根据不同屏幕自动缩放。比如在 750 设计图中，750rpx 刚好等于设备宽度，这样写的样式可以在不同设备中自适应。同时我也了解过在 H5 中通过 `meta viewport` 配置页面缩放，配合 `vw/vh`、媒体查询做响应式布局

**小程序中的适配方式：**

1. 使用 `rpx` 单位（最常用）
   + `rpx` 是微信小程序的自适应单位，会根据设备宽度自动缩放
   + 在 750px 的设计稿下，750rpx = 设备宽度
   + 举例：
     + iPhone6 屏幕宽是 375px，那么 1px ≈ 2rpx
     + 所以写 750rpx 的元素，在所有设备上都会铺满屏幕宽度
2. flex 弹性布局（配合 rpx 使用）
3. 百分比宽度（相对容器）
   + 配合 `width: 100%` 或 `width: 50%` 等百分比进行布局

**H5 移动端适配方式：**

H5 移动端适配的基础是在 `<head>` 中配置 `meta viewport`

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

> `width=device-width` 表示页面宽度等于逻辑分辨率的宽度，`initial-scale=1.0` 表示页面初始缩放为 1 倍（不缩放）

1. 使用媒体查询 + `rem`

   > flexible.js 是一个用来适配移动端的 js 库，实际开发中通常利用它来代替一个一个的媒体查询

   ```css
   /*使用媒体查询，给不同视口的屏幕设置不同的 HTMl 字号*/
   @media (width: 320px) {
     html {
       font-size: 32px;
     }
   }
   @media (width: 375px) {
     html {
       font-size: 37.5px;
     }
   }
   @media (width: 414px) {
     html {
       font-size: 41.4px;
     }
   }

   .box {
     width: 5rem;
     height: 3rem;
     background-color: pink;
   }

   <div class="box"></div>
   ```

2. 使用 `vw / vh` 单位





#### 1.说一下vue数据双向绑定的原理

Vue 的数据双向绑定是通过数据劫持和发布-订阅模式实现的。在 Vue 2 中，它主要使用了 `Object.defineProperty()` 来劫持 data 中的属性，当数据发生变化时通知视图更新；同时，视图上的变更也能通过 `v-model` 同步回数据，实现双向绑定。在 Vue 3 中，Vue 使用了 `Proxy` 对整个对象进行代理，提升了性能和灵活性

> **Vue 2：**
>
> - 用 `Object.defineProperty()` 把 data 中的每个属性都“劫持”起来，设置 getter 和 setter
> - 当你访问或修改数据时，Vue 能“感知”到变化，触发视图更新
> - 再结合 **发布-订阅模式（Dep + Watcher）**，将数据变化“通知”到视图

#### 2.js 中 == 和 === 有什么区别

在 JavaScript 中，`==` 是“宽松等于”，会进行类型转换后再比较，而 `===` 是“严格等于”，不会进行类型转换，要求值和类型都相等。开发中通常推荐使用 `===`，结果更加准确

```js
1 == '1'     // true   类型不同但值相等，== 会进行类型转换
1 === '1'    // false  类型不同（number 和 string）
```

#### 3. 你为什么选择我们公司

作为一名前端初学者，我希望能在真实的项目环境中不断实践学习，而咱们的团队规模适中，有成熟的业务，又愿意接受实习生，对我来说是非常宝贵的锻炼机会。

#### 4.如果你同时拿到多个 Offer，你会怎么选择

我会首先根据公司的业务、实习生负责的模块以及团队的氛围判断哪家公司更适合我成长，然后再结合薪资、租房、距离综合判断哪个offer更适合我