

> 数组也是一种复合数据类型，在数组可以存储多个不同类型的数据
> 
> 
> * 数组中存储的是有序的数据，数组中的每个数据都有一个唯一的索引可以通过索引来操作获取数据
> * 数组中存储的数据叫做元素
> * 任何类型的值都可以成为数组中的元素


#### 基本操作


##### 创建数组



```
// 通过Array创建数组
const arr = new Array()

```


```
// 通过[]创建数组
const arr = []

```

##### 数组添加元素



```
// 通过索引添加元素
arr[0] = "test"
// 如果索引不是连续的，中间的索引也会创建，只是元素是空，应该避免使用非连续数组，性能不好
arr[3] = "2"

```


```
// 定义的时候添加元素
const a = new Array(1,3,4)
const arr = ["1","test"]

```

##### 读取元素



```
// 通过索引读取，如果读取一个不存在的元素，返回undefined
const arr = ["1","test"]
arr[0] // "1"

```

##### 获取数组长度



```
// 获取的实际值是数组的最大的索引+1,非连续数组因为有空值，不会特别准确
console.log(arr.length) 

// 向数组的最后添加元素
arr[arr.length] = "3"

// 修改长度,如果改大了，多出的部分会是空元素，如果改小，会从后往前删除元素
arr.length = 10 

```

##### 数组遍历 for\-of



```
arr = [1,2,3,4,5,6,7,8,9,10]

// 通过长度遍历-正序
for(let i=0; i < arr.length;++){
  console.log(arr[i])
}

// 通过长度遍历-倒序
for(let i=arr.length-1;i>=0;i--){
    console.log(arr[i])
}

// for-of语句可以用来遍历可迭代对象
for(let a of arr){
      console.log(a)
}


```

#### 数组方法(非破坏性)


[方法大全](https://github.com)


##### 增删改查



```
// 检查一个对象是否是数组
let arr = []
console.log(Array.isArray(arr)) // true

```


```
let arr = [1,2,3]
// 根据索引获取数组中的指定元素，
console.log(arr.at(2))

```


```
let arr = [1,2,3]
let arr1 = [4,5,6]

// 用来连接两个或多个数组
// 非破坏性方法，不会影响原数组，而是返回一个新的数组
let new_arr = arr.concat(arr1,[7,8])
console.log(new_arr) // [1,2,3,4,5,6,7,8]


```


```
let arr = [1,2,3,2]
// 获取元素在数组中第一次出现的索引
// 参数:要查询的元素，查询的起始位置
console.log(arr.indexOf(2)) // 1
console.log(arr.indexOf(2,2)) // 3

```


```
let arr = [1,2,3,2]
 // 获取元素在数组中最后一次出现的位置,找到了则返回元素的索引，没有找到返回-1
console.log(arr.lastIndexOf(2)) // 3


```


```
let arr = [1,2,3,2]
 // 将一个数组中的元素连接为一个字符串

console.log(arr.join("~")) // 1~2~3~2

```


```
let arr = [1,2,3,2]

// 用来截取数组（非破坏性方法）

/*
 参数:1.截取开始的索引(包括该索引元素)
     2.截取的结束索引（不包括该索引元素，该参数可以省略不写，如果省略则会一直截取到最后
     如果将两个参数全都省略，则可以对数组进行浅拷贝


*/
console.log(arr.slice(0,2)) // [1,2]

```

##### 深拷贝\&浅拷贝



```
// arr1和arr不是复制，两个指向的是一个内存地址，修改任意一个会影响其他数组
let arr = [1,2,3,2]
let arr1 = arr



/*
  浅拷贝
  通常对对象的拷贝都是浅拷贝
  浅拷贝对对象的浅层进行复制（只复制一层）
  如果对象中存储的数据是原始值，那么拷贝的深浅是不重要
  浅拷贝只会对对象本身进行复制，不会复制对象中的属性（或元素）
  调用slice时，会产生一个新的数组对象，从而完成对数组的复制- 浅拷贝
  
*/
 
let arr2 = [{"name":"l"},{"name":"q"}] 
let arr3 = arr.slice() 

 
/*
深拷贝
深拷贝指不仅复制对象本身，还复制对象中的属性和元素
因为性能问题，通常情况不太使用深拷贝

*/
let arr4 = [{"name":"l"},{"name":"q"}] 
let arr5 = structuredClone(arr4)

```

##### 展开运算符...



```
let arr = [{"name":1},{"name":2}]
// 可以将一个数组中的元素展开到另一个数组中或者作为函数的参数传递，
// 浅复制
let arr2 = [...arr]
console.log(arr2) // [ { name: 1 }, { name: 2 } ]


```

##### 对象的复制



```
/*
Object.assign(目标对象, 被复制的对象)
将被复制对象中的属性复制到目标对象里，并将目标对象返回
*/

const obj = {"name":1}
const  obj1 = Object.assign({},obj)
console.log(obj1) // { name: 1 }

```


```
const obj = {"name":1}

const  obj1 = Object.assign({"age":1},obj)
console.log(obj1) // { age: 1, name: 1 }


```


```
// 也可以使用展开运算符进行对象复制
const obj = {"name":1}

const  obj1 = {...obj}
console.log(obj1) // { name: 1 },将obj中的属性在新对象中展开

```

#### 数组方法(破坏性)



```
const  arr = []

// 向数组的末尾添加一个或多个元素，并返回新的长度
let l = arr.push(1,2,3)
console.log(l) // 3
console.log(arr) // [ 1, 2, 3 ]

```


```
const  arr = [1,2,3,4,5]
// 删除并返回数组的最后一个元素
let a = arr.pop()
console.log(a) //  5
console.log(arr) // [ 1, 2, 3, 4 ]
console.log(arr.length) // 4

```


```
const  arr = [1,2,3,4,5]
// 向数组的开头添加一个或多个元素，并返回新的长度
let a = arr.unshift(99,98)
console.log(a) //  7
console.log(arr) // [99, 98, 1, 2, 3, 4 ]

```


```
const  arr = [1,2,3,4,5]
// 删除并返回数组的第一个元素
let a = arr.shift()
console.log(a) //  1
console.log(arr) // [ 2, 3, 4, 5]
console.log(arr.length) // 4

```


```
// 可以删除、插入、替换数组中的元素
// 参数:1. 删除的起始位置  2. 删除的数量 3. 要插入的元素 返回值:删除的元素

// 删除元素
const  arr = [1,2,3,4,5]
let a = arr.splice(1,2)
console.log(a) // [2,3]
console.log(arr) // [1,4,5]

// 替换元素
const  arr = [1,2,3,4,5]
let a = arr.splice(1,1,"ao") // 可以写多个元素
console.log(a) // [2]
console.log(arr) // [ 1, 'ao', 3, 4, 5 ]


// 插入元素
const  arr = [1,2,3,4,5]
let a = arr.splice(1,0,"ao","to") //在下表为1的地方开始插入ao,to,后续元素后移
console.log(a) // []
console.log(arr) // [ 1, 'ao','to', 2, 3, 4, 5 ]


```


```
// 反转数组
const  arr = [1,2,"a","s",5]
arr.reverse()
console.log(arr) // [ 5, 's', 'a', 2, 1 ]



```

#### 数组去重



```
const arr = [1, 2, 3, 2, 4, 1];
// 使用set方法去重
const arr1 = [...new Set(arr)];
console.log(arr1); // [1, 2, 3, 4]

```


```
// 循环判断去重
const arr = [1, 2, 1, 3, 2, 2, 4, 5, 5, 6, 7]

const newArr = []

for(let ele of arr){
    if(newArr.indexOf(ele) === -1){
        newArr.push(ele)
    }
}

console.log(newArr)

```

#### 高阶函数


如果一个函数的参数或返回值是函数，则这个函数就称为高阶函数
将函数作为参数，意味着可以对另一个函数动态的传递代码


##### 回调函数



```
function user(fn,age){
    fn(age)
}

function admin(age){
    return age === 18;
}

// 一个函数当做参数传递给另一个函数，这个函数称作回调函数(callback)
user(admin,18)


// 通常回调函数使用匿名函数定义
user(a => age === 18,18)

```

可以通过高阶函数，来动态的生成一个新函数



```
function a(){
    return "hello"
}


function b(fn){
    return () => {
        // ... 其他自定义代码
        
        return fn()
    }
}

```

##### 闭包


可以利用函数，来隐藏不希望被外部访问到的变量


* 闭包：
闭包就是能访问到外部函数作用域中变量的函数
* 什么时候使用：
当我们需要隐藏一些不希望被别人访问的内容时就可以使用闭包
* 构成闭包的条件：



```
   1. 函数的嵌套

```

	2. 内部函数要引用外部函数中的变量
	3. 内部函数要作为返回值返回



```
function Sum() {
    let num = 0 // 位于Sum作用域中
    return () => {
        num++
        return num
    }
}


const newFn = new Sum()
console.log(newFn()) // 1
console.log(newFn()) // 2
console.log(newFn()) // 3


```

函数的作用域在函数创建时就已经确定(词法作用域)，和调用位置无关



```
// 闭包的原理就是利用词法作用域
let a = "全局"


function one(){
    console.log(a) // 全局
    return a
}



function two(){
    let a = "局部"
    console.log(a) // 局部
    one()  // 全局

    function three(){ 
        console.log(a) // 局部，函数定义是外部变量a是two中的a
    }
    return three
}



let fn = two()
fn()

```

闭包的生命周期：


1. 闭包在外部函数调用时产生，外部函数每次调用都会产生一个全新的闭包
2. 在内部函数丢失时销毁（内部函数被垃圾回收了，闭包才会消失）


注意事项：


* 闭包主要用来隐藏一些不希望被外部访问的内容，
* 这就意味着闭包需要占用一定的内存空间


相较于类来说，闭包比较浪费内存空间（类可以使用原型而闭包不能）


* 需要执行次数较少时，使用闭包
* 需要大量创建实例时，使用类


##### 递归


调用自身的函数称为递归函数


递归的作用和循环是基本 一致的



```
function test(num){
    // 终止条件
    if (num === 1){
        return 1
    }
     // 调用自身
    return test(num-1) * num
}

```

递归的核心思想就是将一个大的问题拆分为一个一个小的问题，小的问题解决了，大的问题也就解决了


编写递归函数，一定要包含两个要件：


1. 基线条件 —— 递归的终止条件
2. 递归条件 —— 如何对问题进行拆分



> 递归的作用和循环是一致的，不同点在于，递归思路的比较清晰简洁，循环的执行性能比较好
> 在开发中，一般的问题都可以通过循环解决，也是尽量去使用循环，少用递归
> 只在一些使用循环解决比较麻烦的场景下，才使用递归


#### 数组方法(回调函数参数)



```
/*
  sort用来对数组进行排序（会对改变原数组）
  sort默认会将数组升序排列
    注意：sort默认会按照Unicode编码进行排序，所以如果直接通过sort对数字进行排序
        可能会得到一个不正确的结果
  参数：
    - 可以传递一个回调函数作为参数，通过回调函数来指定排序规则
        (a, b) => a - b 升序排列
        (a, b) => b - a 降序排列
*/

let arr = [3,3,4,6,8,1,2,10]


arr.sort((a,b) => a -b)

console.log(arr)

```


```
/*
 用来遍历数组
 需要一个回调函数作为参数，这个回调函数会被调用多次
 数组中有几个元素，回调函数就会调用几次
 每次调用，都会将数组中的数据作为参数传递
 回调函数中有三个参数：
    element 当前的元素
    index 当前元素的索引
    array 被遍历的数组
*/

let arr = [3,3,4,6,8,1,2,10]


arr.forEach((element,index,array)=>{
    console.log(element)
    console.log(index)
    console.log(array)
})

```


```
/*
将数组中符合条件的元素保存到一个新数组中返回
需要一个回调函数作为参数，会为每一个元素去调用回调函数，并根据返回值(true、false)来决定是否将元素添加到新数组中
非破坏性方法，不会影响原数组

*/
/*
根据当前数组生成一个新数组
需要一个回调函数作为参数，
回调函数的返回值会成为新数组中的元素
非破坏性方法不会影响原数组
*/


let a = ["商城","账户","登录","注册"]


let b = a.map(ele => "- "
 + ele + "")

console.log(b) // [ '- 商城
', '- 账户
', '- 登录
', '- 注册
' ]



```


```
/*
可以用来将一个数组中的所有元素整合为一个值
参数：
    1. 回调函数，通过回调函数来指定合并的规则
    2. 可选参数，初始值
*/

let arr = [1,2,3,4,5,6,7,8,10]

let b = arr.reduce((a,b) => a+b)
console.log(b) // 46



let arr2 = [1,2,3,4,5,6,7,8,10]

let b2 = arr2.reduce((a,b) => a+b,10)
console.log(b2) // 56

```

#### 函数可变参数



```
/*
arguments是函数中又一个隐含参数
arguments是一个类数组对象（伪数组）
和数组相似，可以通过索引来读取元素，也可以通过for循环变量，但是它不是一个数组对象，不能调用数组的方法
arguments用来存储函数的实参，
无论用户是否定义形参，实参都会存储到arguments对象中
可以通过该对象直接访问实参

*/


function test(){
    console.log(arguments) // { '0': 1, '1': 3, '2': 4 }
    console.log(arguments[0]) // 1

}


test(1,3,4)

```


```
/*
可变参数，在定义函数时可以将参数指定为可变参数
- 可变参数可以接收任意数量实参，并将他们统一存储到一个数组中返回
- 可变参数的作用和arguments基本是一致，但是也具有一些不同点：
    1. 可变参数的名字可以自己指定
    2. 可变参数就是一个数组，可以直接使用数组的方法
    3. 可变参数可以配合其他参数一起使用,当可变参数和普通参数一起使用时，需要将可变参数写到最后

*/


function test(...args){
    console.log(args) // [ 1, 3, 4 ]
    console.log(args[0]) // 1]


}


test(1,3,4)

```

#### call和apply


调用函数除了通过函数()调用外，还可以通过其他的方式调用



```
function test(){
  return "hello"
}

test.call() // "hello"
test.apply() // "hello"

```


```
/*
call 和 apply除了可以调用函数，还可以用来指定函数中的this
call和apply的第一个参数，将会成为函数的this
通过call方法调用函数，函数的实参直接在第一个参数后一个一个的列出来

*/
class  User{
    name = "l"
    age = 18
}




function test(a,b){
    console.log(this.name) // name
    console.log(this) // User { name: 'l', age: 18 }
    console.log(a) // 1
    console.log(b) // 2

}


let user = new User()
// 指定test函数的this是user对象
test.call(user,1,2)

```


```
// 通过apply方法调用函数，函数的实参需要通过一个数组传递
class  User{
    name = "l"
    age = 18
}




function test(a,b){
    console.log(this.name) // name
    console.log(this) // User { name: 'l', age: 18 }
    console.log(a) // 1
    console.log(b) // 2

}


let user = new User()
// 指定test函数的this是user对象
test.apply(user,[1,2])

```

#### bind



> bind() 是函数的方法，可以用来创建一个新的函数
> 
> 
> * bind可以为新函数绑定this
> * bind可以为新函数绑定参数
> 
> 
> 箭头函数没有自身的this，它的this由外层作用域决定
> 
> 
> * 无法通过call apply 和 bind修改它的this
> * 箭头函数中没有arguments



```
class  User{
    name = "l"
    age = 18
}




function test(a){
    console.log(a) // 10
    console.log(this.name) // l

}


const user = new  User()

// 指定新函数的this和参数，如果是原函数()调用，则走原函数的参数和this
const newFn = test.bind(user,10)
newFn()

```

 本博客参考[樱花宇宙官网](https://yzygzn.com)。转载请注明出处！
