1.computed的传参

 https://blog.csdn.net/xlelou/article/details/81477391 

 https://blog.csdn.net/cxwtsh123/article/details/83089690 

2.watch的深度监听 

 https://blog.csdn.net/xlelou/article/details/81477391 

3.vue使用sass的全局变量

 https://www.cnblogs.com/Mrrabbit/p/11180287.html 

 https://segmentfault.com/q/1010000019750954 

 https://github.com/vuejs/vue-cli/issues/3783 

 [https://cli.vuejs.org/zh/guide/css.html#%E5%90%91%E9%A2%84%E5%A4%84%E7%90%86%E5%99%A8-loader-%E4%BC%A0%E9%80%92%E9%80%89%E9%A1%B9](https://cli.vuejs.org/zh/guide/css.html#向预处理器-loader-传递选项) 

4.prop

- 对象数组的默认值必须由函数返回

  ```vue
  props:{
  	propC: {
  		type: Object,
  		default: ()=> {}
  	}
  }
  ```

  

- prop自定义验证函数

  ```vue
  props:{
  	propC: {
  		validator(val) {
  			return [1,2,3].indexOf(value) !== -1
  		}
  	}
  }
  ```

  

- prop和attr

  ```vue
  <prop :prop="prop" attr="attr" />
   <p>{{ `${prop} ${$attrs.attr}` }}</p>
  ```

  

5..sync修饰符

```vue
<text-document v-bind.sync="doc"></text-document>
等于 v-model
```

6.插槽

7.style和class

8.混入

9.渲染函数和jsx

10.边界

11:key和v-if&v-for

 `key` 的特殊属性主要用在 Vue 的虚拟 DOM 算法，在新旧 nodes 对比时辨识 VNodes。如果不使用 key，Vue 会使用一种最大限度减少动态元素并且尽可能的尝试修复/再利用相同类型元素的算法。使用 key，它会基于 key 的变化重新排列元素顺序，并且会移除 key 不存在的元素。 

 https://cn.vuejs.org/v2/api/#key 

 https://v1-cn.vuejs.org/guide/list.html#track-by 

12表单修饰符:

```
.lazy
.number
.trim
```

13.组建中的is

14.keep-alive

 https://www.cnblogs.com/zhuzhenwei918/p/6905140.html 

 https://cn.vuejs.org/v2/api/#keep-alive 

页面不会出现生命周期函数调用

