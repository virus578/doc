# 第一阶段(动手实现react,jsx和react的消息机制)

## 动手实现react

## react的安装环境

```powershell
 npm i -g create-react-app
 create-react-app 'demo'
```



## 使用jsx

jsx是什么?

jsx是html和js混写的模板(方便使用) 本质上还是js(js也能实现一段html标签)

在编译阶段,

 ![JSX 描述 React.js 组件图片](http://huzidaha.github.io/static/assets/img/posts/44B5EC06-EAEB-4BA2-B3DC-325703E4BA45.png) 

为什使用react-dom

1. 不一定会把元素渲染到浏览器上,例如 cavans app
2. react-dom使用了diff算法尽可能减少dom操作



## 组件中render

react中一切皆组件

render必选返回一个jsx元素

jsx就是js里的对象

jsx元素变量:render里可以声明一个变量等于标签



表达式插入:{}可以是js代码,也可以是标签(条件返回)



html和jsx关键字冲突

class和for在js中是关键字

 html在jsx中class使用className代替 ,for使用htmlFor代替

## 组件的组合与嵌套

自定义组件必须使用大写字母开头,普通html使用小写字母开头

## 事件监听

react为什么要监听事件的变化

1. addEventlistern:react封装了事件监听(不用考虑兼容性),在事件前加上on并使用驼峰命名就能监听事件
   onClick只能用在普通标签上 不能用在组价上
2. event对象:react封装event和原生保持一致(考虑兼容性)

3. 事件中的this: 一般在某个类的实例方法里面的 `this` 指的是这个实例本身。但是在react中this是null/undefined


因为react调用你传给他的方法,并不是通过对象的方式调用,而是通过函数的方式调用 <font color="#ff0">使用bind可以拿到组件实例</font>





## 组件中state和setState

- state
  react通过state存储组件私有状态 修改state必须使用setState

- setState接受对象参数

  setState更新组件状态 并重新调用render方法 渲染页面

  为什么使用setState修改状态 通知react修改状态(函数式编程)

- setState接受函数参数
   当你调用 `setState` 的时候，*React.js 并不会马上修改 state*。而是把这个对象放到一个更新队列里面，稍后才会从队列当中把新的状态提取出来合并到 `state` 当中，然后再触发组件更新 

- setState合并(优化)
  react会把 JavaScript 事件循环中的消息队列的同一个消息中的 `setState` 都进行合并以后再重新渲染组件 

## 父子组件props

默认配置 defaultProps

prop不可改 

传递state下去使用setStatr修改state

双向数据绑定

## state vs props

 `state` 的主要作用是用于组件保存、控制、修改*自己*的可变状态。`state` 在组件内部初始化，可以被组件自身修改，而外部不能访问也不能修改。 

 `props` 的主要作用是让使用该组件的父组件可以传入参数来配置该组件。它是外部传进来的配置参数，组件内部无法控制也无法修改。除非外部组件主动传入新的 `props`，否则组件的 `props` 永远保持不变 

 *`state` 是让组件控制自己的状态，`props` 是让外部对组件自己进行配置*。 

 尽量少地用 `state`，尽量多地用 `props` 

 没有 `state` 的组件叫无状态组件（stateless component），设置了 state 的叫做有状态组件（stateful component）。因为状态会带来管理的复杂性，我们尽量多地写无状态组件，尽量少地写有状态的组件。这样会降低代码维护的难度，也会在一定程度上增强组件的可复用性。前端应用状态管理是一个复杂的问题，我们后续会继续讨论。 

 React.js 非常鼓励无状态组件，在 0.14 版本引入了函数式组件——一种定义不能使用 `state` 组件，例如一个原来这样写的组件： 

```react
class HelloWorld extends Component {
  constructor() {
    super()
  }

  sayHi () {
    alert('Hello World')
  }

  render () {
    return (
      <div onClick={this.sayHi.bind(this)}>Hello World</div>
    )
  }
}
const HelloWorld = (props) => {
  const sayHi = (event) => alert('Hello World')
  return (
    <div onClick={sayHi}>Hello World</div>
  )
}
```

 以前一个组件是通过继承 `Component` 来构建，一个子类就是一个组件。而用函数式的组件编写方式是一个函数就是一个组件，你可以和以前一样通过 `` 使用该组件。不同的是，函数式组件只能接受 `props` 而无法像跟类组件一样可以在 `constructor` 里面初始化 `state`。你可以理解函数式组件就是一种只能接受 `props` 和提供 `render` 方法的类组件。 

## 列表渲染数据

```react
class Index extends Component {
  render () {
    return (
      <div>
        {[
          <span>React.js </span>,
          <span>is </span>,
          <span>good</span>
        ]}
      </div>
    )
  }
}

ReactDOM.render(
  <Index />,
  document.getElementById('root')
)
```

 我们一般不会手动写循环来构建列表的 JSX 结构 

渲染组件抽离

 http://huziketang.mangojuice.top/books/react/lesson13 

key

React.js 的是非常高效的，它高效依赖于所谓的 Virtual-DOM 策略。简单来说，能复用的话 React.js 就会尽量复用，没有必要的话绝对不碰 DOM。对于列表元素来说也是这样，但是处理列表元素的复用性会有一个问题：元素可能会在一个列表中改变位置。例如：

```html
<div>a</div>
<div>b</div>
<div>c</div>
```

假设页面上有这么3个列表元素，现在改变一下位置：

```html
<div>a</div>
<div>c</div>
<div>b</div>
```

`c` 和 `b` 的位置互换了。但其实 React.js 只需要交换一下 DOM 位置就行了，但是它并不知道其实我们只是改变了元素的位置，所以它会重新渲染后面两个元素（再执行 Virtual-DOM 策略），这样会大大增加 DOM 操作。但如果给每个元素加上唯一的标识，React.js 就可以知道这两个元素只是交换了位置：

```html
<div key='a'>a</div>
<div key='b'>b</div>
<div key='c'>c</div>
```

这样 React.js 就简单的通过 `key` 来判断出来，这两个列表元素只是交换了位置，可以尽量复用元素内部的结构。

这里没听懂没有关系，后面有机会会继续讲解这部分内容。现在只需要记住一个简单的规则：*对于用表达式套数组罗列到页面上的元素，都要为每个元素加上 `key` 属性，这个 `key` 必须是每个元素唯一的标识*。一般来说，`key` 的值可以直接后台数据返回的 `id`，因为后台的 `id` 都是唯一的。

# 第二阶段(生命周期和react一些属性)



# 第三阶段(高阶组件和动手实现redux)