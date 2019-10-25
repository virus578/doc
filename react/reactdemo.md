1. 一个简单的点赞功能
   问题:不易复用 js代码 html全部复制

2. 结构复用 ---- 新建一个类  html页面抽离为render函数

3. 实现简单的组件化 ----- 按钮的状态 加入点击事件方法

4. 状态改变 -> 构建新的 DOM 元素更新页面  手动管理数据和dom之间的操作 代码维护性差 减少手动dom操作(多种状态就意味着很多的dom操作)

   加入 setState函数 修改数据(函数式)和 更新render函数(不用手动更新页面)
   但是没有 重新更新渲染

   ```react
   class LikeButton {
       constructor () {
         this.state = { isLiked: false }
       }
   
       setState (state) {
         this.state = state
         this.el = this.render()
       }
   
       changeLikeText () {
         this.setState({
           isLiked: !this.state.isLiked
         })
       }
   
       render () {
         this.el = createDOMFromString(`
           <button class='like-btn'>
             <span class='like-text'>${this.state.isLiked ? '取消' : '点赞'}</span>
             <span>👍</span>
           </button>
         `)
         this.el.addEventListener('click', this.changeLikeText.bind(this), false)
         return this.el
       }
     }
   ```

   

5. 重新插入新的 DOM 元素 加入onStateChange(插入新元素,删除旧元素) 
   每次调用 setState就会触发onStateChange 
   setState操作dom 用vitual-dom优化

   ```react
   ...
       setState (state) {
         const oldEl = this.el
         this.state = state
         this.el = this.render()
         if (this.onStateChange) this.onStateChange(oldEl, this.el)
       }
   ...
   ```

   

6. 抽离setSate 和 `_renderDOM` 方法会调用 `this.render` 来构建 DOM 元素并且监听 `onClick` 事件

   ```react
    class Component {
       setState (state) {
         const oldEl = this.el
         this.state = state
         this._renderDOM()
         if (this.onStateChange) this.onStateChange(oldEl, this.el)
       }
   
       _renderDOM () {
         this.el = createDOMFromString(this.render())
         if (this.onClick) {
           this.el.addEventListener('click', this.onClick.bind(this), false)
         }
         return this.el
       }
     }
   ```

7. 传入颜色

   ```react
     constructor (props = {}) {
         this.props = props
       }
   ```

   

   ```react
    class LikeButton extends Component {
       constructor (props) {
         super(props)
         this.state = { isLiked: false }
       }
   
       onClick () {
         this.setState({
           isLiked: !this.state.isLiked
         })
       }
   
       render () {
         return `
           <button class='like-btn' style="background-color: 			   ${this.props.bgColor}">
              <span class='like-text'>
               ${this.state.isLiked ? '取消' : '点赞'}
             </span>
             <span>👍</span>
           </button>
         `
       }
     }
   
     mount(new LikeButton({ bgColor: 'red' }), wrapper)
   ```

   



super关键字: 即可当函数又可以当对象

1.super做函数 代表父类的构造函数  子类的构造函数必须执行一次`super`函数。 

```js
class A {}

class B extends A {
  constructor() {
    super();
  }
}
```

2.super用作对象在普通方法 指父类的原型对象, 在静态方法中 指向父类

```js
class A {
  p() {
    return 2;
  }
}

class B extends A {
  constructor() {
    super();
    console.log(super.p()); // 2
  }
}

let b = new B();
```

 http://huziketang.mangojuice.top/books/react/lesson2

 https://segmentfault.com/a/1190000019928571  