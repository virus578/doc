如何用js对象表现一个一个dom元素

```html
<div class='box' id='content'>
  <div class='title'>Hello</div>
  <button>Click</button>
</div>
```

每个dom元素结构都可以用js的对象来表示

```js
{
  tag: 'div',
  attrs: { className: 'box', id: 'content'},
  children: [
    {
      tag: 'div',
      arrts: { className: 'title' },
      children: ['Hello']
    },
    {
      tag: 'button',
      attrs: null,
      children: ['Click']
    }
  ]
}
```

react.js支持在js里写html代码  编译的过程就会把jsx转为js的对象结构

```react
import React, { Component } from 'react'
import ReactDOM from 'react-dom'
import './index.css'

class Header extends Component {
  render () {
    return (
      <div>
        <h1 className='title'>React 小书</h1>
      </div>
    )
  }
}

ReactDOM.render(
  <Header />,
  document.getElementById('root')
)
```

编译后

```react
import React, { Component } from 'react'
import ReactDOM from 'react-dom'
import './index.css'

class Header extends Component {
  render () {
    return (
     React.createElement(
        "div",
        null,
        React.createElement(
          "h1",
          { className: 'title' },
          "React 小书"
        )
      )
    )
  }
}

ReactDOM.render(
  React.createElement(Header, null), 
  document.getElementById('root')
);
```

 *所谓的 JSX 其实就是 JavaScript 对象* 

 ![JSX 描述 React.js 组件图片](http://huzidaha.github.io/static/assets/img/posts/44B5EC06-EAEB-4BA2-B3DC-325703E4BA45.png) 

为什么jsx不直接渲染dom 而经过这一层呢

1.不一定把元素渲染在浏览器上 可能渲染在app, cavans上

2.render函数把虚拟dom 转化为dom 使用diff算法比较减少dom操作 优化性能