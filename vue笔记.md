# 第一天
## 01-创建vue实例
创建vue实例，初始化渲染的核心步骤：
1. 准备容器
2. 引包（官网）
3. 创建vue实例 new Vue（）
4. 指定配置项el data => 渲染数据
   * el指定挂载点，选择器指定控制的是哪个盒子（el 会接受个字符串参数，指定盒子）
   * data提供数据
```HTML
    <!-- 
        创建一个vue实例，初始化渲染
        1.准备容器
        2.引包（开发版/生产者包）
        3.创建实例
        4.添加配置 => 完成渲染
     -->

     <div id="app">
        <!-- 这里将来会填写用来渲染的代码逻辑 -->
        {{ msg }}
        <a href="#">{{ count }}</a>
     </div>

     <!-- 引入开发版本包，有更完整的注释和警告 -->
     <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>

     <script>
        // 一旦引入了vuejs核心包，在全局环境，就有了vue构造函数
        const app = new Vue(
            {
                // 通过 el 配置环境，指定vue管理的是哪一个盒子
                el: '#app',
                // 通过data提供数据
                data: {
                    msg: 'hello 你好',
                    count: 666
                }
            }
        )
     </script>
```

演示：
![Alt text](./pic/vue_pic/image3.png)

## 02—插值表达式{{ }}
插值表达式是一种vue的模版语法，但是不具备解析标签的能力
1. 作用：利用表达式（是可以被求值的代码，JS引擎会计算出结果）进行差值，渲染到页面中
2. 语法：{{ 表达式 }}
3. 注意点：
    * 使用的数据必须是**存在**的
    * 支撑的是表达式，而非语句，比如：if，for...就不行
    * 不能在标签属性中使用{{ }}插值表达式

```html
 <div id="app">
        {{ nickname.toUpperCase() }}
        {{ nickname+',hello' }}
        <p>{{ age >= 18 ? '成年' : '未成年'}}</p>
        <p>{{ friend.desc }}</p>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>

    <script>
        const app = new Vue({
            el:'#app',
            data:{
                nickname:'tony',
                age:18,
                friend: {
                    name:'jepen',
                    desc:'热爱学习 vue',
                }
            }
        })
    </script>
```
## 03-响应式特性
响应式-数据一旦修改，视图自动更新
```html
    <div id="app">
      {{ msg }}
    </div>

    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>

    <script>
        const app = new Vue({
            el:'#app',
            data:{
                // 响应式数据——一旦修改数据，视图立马改变
               msg:'你好，黑马',
            }
        })
    // data中的数据是会添加到 实例上的
    // 所以说， 可以通过 实例.属性名 = 新值 来修改数据
    app.msg = '你好,hello';    
    </script>
```

## 04-Vue指令
### 初始指令
为什么会用到指令呢——因为插值表达式不会解析标签
带有v-前缀的特殊标签属性
### v-html
```html
    <div id="app">
        <div v-html="msg"></div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>

    <script>
        const app = new Vue({
            el:'#app',
            data:{
                // 这里用 ``，因为是多行字符串，不能单纯用''                
                msg:`
                <a href="https://www.jd.com/?cu=true">
                京东
                </a>
                `
            }
        })
    </script>
```

效果演示：![](mk-2024-01-21-03-00-57.png)

