# [JS如何判断一个对象是否为空、是否有某个属性](https://www.cnblogs.com/crackedlove/p/10039105.html)

判断一个对象是否为空

```js
//1.
function empty(obj) {
    for(let key in obj) {
        return false  //非空
    }
    return true // 为空
}
//2.
JSON.stingify(obj) === '{}' //相等为空对象
//3.
//Object.keys(obj) 返回一个给定对象自身可枚举属性组成的数组
Object.keys(obj).length === 0 //相等为空对象
```

js判断对象中是否有某个属性

```js
//1. .或者[]
//2. in运算符 如果某属性在指定对象上或其原型链上返回true
//3. obj.hasOwanProperty()对象自身属性中含有某属性，返回true。
```

# js里怎么判断一个对象是否是日期类型，即Date，用typeof返回的是object

```js
//用instance 
object instanceof Date
```

去掉input number类型的滚轮

https://www.cnblogs.com/yuzihong/p/10212518.html

自定义js方法

https://www.cnblogs.com/Marydon20170307/p/6541462.html

js数组去重 删除原数组 新建数组 取第一个还是最后一个

```js
 1.indexof
  let arr =[]
source_arr.filter(function (element, index, array) {
    return array.indexOf(element) === index;//取数组重复的第一个元素
    arr.includes(element) ? '' arr.push(element)
})
return arr
Array.prototype.distrinct  =funciton ()  {
    let arr = this,
        result = [],
        len = arr.length,
    	bool
    arr.forEach(function(r,i, arr){
        bool = arr.indexOf(r,i+1) //取数组重复的最后一个元素
        if(bool == -1){
            result.push(v)
        }
    })
    return result
}
//includes
function unique5(arr){
 var res = [];
 
 for(var i=0; i<arr.length; i++){
  if( !res.includes(arr[i]) ){ // 如果res新数组包含当前循环item
   res.push(arr[i]);
  }
 }
 return res;
}
//String.inludes 判断一个字符串是否在另一个字符串中
//2.[...new Set(arr)] Array.from(new Set([1,1,2,2,3]))
//3.双重for循环 占用内存高 慢
Array.prototype.distrinct = funciton ()  {
    let arr = this
    i,
    j,
    len = arr.length
    for(i = 0; i<len; i++) {
        for(j = i +1, j<len; j++) {
            if(arr[i] === arr[j]){
                arr.splice(j,1)
                len--
                j--
            }
        }
    }
	return arr
}
//4.对象属性不能相同的特点
let o = {}
o[1] =1
console.log(o) //{1:1}
Array.prototype.distrinct = funciton () {
    //js创建多个变量 cosnt赋值必须初始化
    let arr = this,
    i,
    obj = {},
    result= []
    len = arr.length
    for(i = 0; i< len ; i++){
        if(!obj[arr[i]]) {
            obj[arr[i]] = 1
            result.push(arr[i]) //取第一个
        }
    }
    return result
}
//5.数组排序递归 sort排序 splice删除相邻相同的数据
Array.prototype.distrinct = function() {
    let arr = this,
    len = arr.length
    arr.sort(function(a,b){
        return a - b
    })
    function loop(index) {
        if(index > 1) {
            if(arr[index]===arr[index -1]){
                arr.splice(index,1)
            }
            loop(index -1)
        }
    }
    loop(index -1)
    return arr
}

```

树转换为平行数组

```js

export default function(obj, childName, valueVame) {
    let list = []
    let transArray = function(obj, arr = []) {
      arr.push(obj[valueVame])
      list.push(arr)
      if (obj[childName]) {
        obj[childName].forEach(ele => {
          transArray(ele, arr.concat())
        })
      } else {
        list.push(arr)
      }
      return arr
    }
    transArray(obj)
    return list
  }
```

数组里的对象去重

js数组合并

caoncat() push()

array

那些方法直接修改原数组 splice sort reverse() push pop push shift unshift forEach

```js
/*push和unshift 添加一个或者多个元素返回新的length
*pop删除数组最后一个元素 shift删除数组第一个元素
*pop和shift 删除一个删除的元素 返回删除的元素 数组为空Wieundefined
*pop shift push unshift 类数组也能使用
*/
find 返回数组中满足条件的第一个值
every 数组每一个元素大于条件  返回true
some 数组任意一个元素大于条件 返回 true
forEach 返回undefined
filter 返回满足条件的元素数组
arr.map(function(currentValue, index, array){})//当前值,索引, 当前数组 ,this 代表当前数组
//返回值新数组
arr.reduce(function(accmulator, currentValue, index, array){
    return accmulator + currentValue
},4)
//返回值:函数累计处理的结果
arr.reduce(callback(accumulator, currentValue[, index[, array]])[, initialValue]) //累积器, 当前值,索引[可选], 当前数组[可选]
/*initialValue可选
作为第一次调用 callback函数时的第一个参数的值。
如果没有提供初始值，则将使用数组中的第一个元素。 在没有初始值的空数组上调用 reduce 将报错
*/
arr.sort((a,b) => a-b) //返回排序后的数组

Array.from(arrayLike[, mapFn[, thisArg]])// 可迭代的伪数组或可迭代对象
let s = new Set([2,2,4,5,6])
s = Array.from(s,x => x*x)
//Array.indexOf 返回数组给定元素第一个索引 不存在就返回-1 
/*两个参数 searchElement fromIndex(为负数从array.length + fromIndex,默认值为0) 负值很特*殊(大于本身的数组长度)
Array.include 也是如此*/
// String.indexOf 返回字符串第一次出现给定值的索引
// lastIndexOf
let s = [1,[1,2,[3]]]
s.flat()
var newArray = arr.flat([depth]) //depth指嵌套数组的结构深度 默认值为1 返回

```
https://www.cnblogs.com/chenshihaook/p/6186343.html

所有数据类型都有toString 和 valueOf 方法

[**js或jQuery获取当前屏幕的各种高度**]( https://blog.csdn.net/zzqworkspace/article/details/72725048 ) 

