# 笔记

## 脚手架文件结构：

    ├─ node_modules
    ├─ public
    │ ├─ favicon.ico：页签图标
    │ └─ index.html：主页面
    ├─ src
    │ ├─ assets：存放静态资源
    │ │ └─logo.png
    │ ├─ components：存放静态资源
    │ │ └─HelloWorld.vue
    │ ├─ App.vue：汇总所有组件
    │ ├─ main.js：入口文件
    ├─ .gitignore：git 版本管制忽略的配置
    ├─ babel.config.js：babel 的配置文件
    ├─ package-lock.json：包版本控制文件
    ├─ package.json：应用包配置文件
    └─ README.md：应用描述文件

## 关于不同版本的 Vue：

-   vue.js 与 vue.runtime.xxx.js 的区别：
    (1).vue.js 是完整版的 Vue，包含：核心功能+模板解析器。
    (2).vue.runtime.xxx.js 是运行版的 Vue，只包含：核心功能：没有模板解析器。

-   因为 vue.runtime.xxx.js 没有模板解析器，所以不能使用 template 配置项，需要使用
    render 函数接收到 createElement 函数去指定具体内容。

## vue.config.js 配置文件

> 使用 vue inspect > output.js 可以查看到 Vue 脚手架的默认配置。
> 使用 vue.config.js 可以对脚手架进行个性化定制，详情见：https://cli.vuejs.org/zh

## ref 属性

    1.被用来给元素或子组件注册引用信息（id 的替代者）
    2.应用在 html 标签上获取的是真实 DOM 元素，应用在组件标签上是组件实例对象（vc）
    3.使用方式：
        打标识：<h1 ref="xxx">....</h1> 或 <school ref="xxx"></school>
        获取：this.$refs.xxx

## 配置项 props

    功能：让组件接收外部传过来的数据
        (1).传递数据：
            <Demo name="xxx"/>
        (2).接收数据：
            第一种方式（只接收）：
                props:['name']

            第二种方式（限制类型）：
                props:{
                  name:Number
                }

            第三种方式（限制类型、限制必要性、指定默认值）：
                props:{
                  name:{
                    type:String, //类型
                    required:true,//必要性
                    default:'老王'//默认值
                  }
                }
    备注：props是只读的，Vue底层会监测你对props的修改，如果进行了修改，就会发出警告；

## mixin(混入)

    功能：可以把所有组件共用的配置提取成一个混入对象
      使用方式：
        第一步定义混合，例如：
          {
            data(){....},
            methods:{....}
            ....
          }
        第二步使用混入，例如：
          (1).全局混入：Vue.mixin(xxx)
          (2).局部混入：mixins:['xxx']

## 插件

    功能：用于增强Vue
    本质：包含install方法的一个对象，install的第一个参数是Vue，第二个以后的参数是插件使用者传递的数据。
    定义插件：
      对象.install = function (Vue, options) {
          // 1.添加全局过滤器
          Vue.filter(....)

          // 2.添加全局指令
          Vue.directive(....)

          // 3.配置全局混入（合）
          Vue.mixin(....)

          // 4.添加实例方法
          Vue.prototype.$myMethod = function (){....}
          Vue.prototype.$myProperty = xxx
      }

## scoped样式
    作用：让样式在局部生效，防止冲突。
    写法：<style scoped>