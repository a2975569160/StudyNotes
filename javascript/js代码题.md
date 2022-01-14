### 扁平化数组转树形结构数据

最少两种实现方式

~~~js
const arrData = [
    { id: 2, name: '部门B', parentid: null },
    { id: 3, name: '部门C', parentid: 1 },
    { id: 1, name: '部门A', parentid: 2 },
    { id: 4, name: '部门D', parentid: 1 },
    { id: 5, name: '部门E', parentid: 2 },
    { id: 6, name: '部门F', parentid: 3 },
    { id: 7, name: '部门G', parentid: 2 },
    { id: 8, name: '部门H', parentid: 4 },
];

/** start: code */

function listTree(list,pid) {
const temp =[]
    list.forEach(item => {
    if(item.parentid === pid) {
        temp.push(item)
        item.children = listTree(item,item.id)
    }
})
    return temp
}
undefined
listTree(arrData,null)

/** end: code */
~~~



### 数组去重

最少三种实现方式

~~~js
const arr = [45, 78, 45 ,22, 78, 46]

/** start: code */

/** end: code */
~~~



### 求值

输出结果

1.

~~~js
var x; 
for(var i = 0, j = 0; i < 6, j < 10; i++, j++) {
	x = i + j
}
x ?
~~~



2.

~~~js
var bar = 1
console.log(bar)
function test() {
    console.log(bar)
    var bar = 2
    console.log(bar)
}
test()
~~~



### this指向

1.

~~~js
var obj={
    num:1,
    counter:()=>this.num++
}
obj.counter()
console.log(obj.num)
~~~



2.

~~~js
function test() {
  console.log(this.x);
}
var obj = {
    x: 1,
    m: test
};
obj.m()
~~~



3.

~~~js
var point = { 
         x : 0, 
         y : 0, 
         moveTo : function(x, y) { 
             this.x = x;
             console.log(this.x); 　　　　// ？
             console.log(this);　　　　// ？

             // 内部函数
             var moveX = function(x) { 
                this.x = x;
             }; 
             // 内部函数
             var moveY = function(y) { 
                this.y = y;
             } 
             moveX(x);
             moveY(y); 
         } 
    }; 
    point.moveTo(1, 1); 
    console.log(point.x);　　　　// ？
    console.log(point.y);　　　　// ？
    console.log(x);　　　　// ？
    console.log(y);　　　　// ？
~~~



4.

~~~js
var flag = '996'
function person1(fg) {
	let o = new Object()
    o.flag = fg
    o.getVal = () => {
		console.log(this)
	}
    return o
}
function person2(fg) {
	let o = new Object()
    o.flag = fg
    o.getVal = function() {
		console.log(this)
	}
    return o
}
let p1 = new person1('251')
let p2 = new person2('251')
p1.getVal()
p2.getVal()
~~~



5.

~~~js
var name = 1
function test() {
	var name = 2
	console.log(this.name)
	return function inner() {
		console.log(name)
	}
}
test()
test()()

var b = {
	name: 3
}
b.test = test
b.test()

var c = b.test
c()

new test()
~~~

