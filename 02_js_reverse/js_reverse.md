

[TOC]



# 1、	JS語法基礎

课件地址：https://www.yuque.com/tuling_python/js_reverse
密码：lxfe

js逆向语雀链接：https://www.yuque.com/buziran/cbopse?# 
码：ghzd

## 1-1、	安裝node

​			https://github.com/coreybutler/nvm-windows/releases

`	nvm`基础指令：

- nvm list`：列出所有已安装的`node`

- `nvm install 16`：安装指定版本的`node`，`16`指的是`node`版本

- `nvm use 16`：切换到指定的`node`版本，`16`指的是`node`版本，若需要切换到其他版本则修改版本号

  

## 1-2、	變數與數據類型+

~~~javascript
var number = 123;
let string = 'hello';  // 也是声明变量的一种

// const bool = true;  // 声明的是常量


// 这是单行注释
/*
这是多行注释
*/


/* 在js中连续声明多个变量 */
var a = 1, b = 2, c = 3;  // ;代表一段语句的结束 sql语句是一样的

/* 在js中输出变量的值 */
console.log(a, b, c);


/* 数据类型一共有六种: 数字, 字符串, 布尔值, null, undefined, 对象) */
// 数字类型
var int_data = 123;
var float_data = 123.456;

// 字符串类型
var text = 'hello';

// 布尔类型
var bool_data_1 = true;
var bool_data_2 = false;

// null (表示一个空值或不存在的对象, 它是一个明确的赋值, 表示 '没有值')
var null_data = null;

// undefined (表示一个未定义的值, 它是一个未赋值的对象, 默认值)
var undefined_data = undefined;

// 对象 (复合类型, 可以包含多个值, 也被称之为引用类型)
var obj_data = {
    "name": "hello",
    "age": 13
}


/* 输出变量类型 */
console.log(
    typeof int_data,
    typeof float_data,
    typeof text,
    typeof bool_data_1,
    typeof bool_data_2,
    typeof null_data,  // null_data 的类型是 object
    typeof undefined_data,
    typeof obj_data
);

~~~



## 1-3、	函數的定義與調用

~~~javascript
// 函数定义
function run_func() {
    console.log('hello world');  // 如果对于语法比较严谨的同学可以写完一段带分号, 分号不带其实不影响程序的执行
}

// 函数调用
run_func();

/* 带有返回值的函数 */
function return_data() {
    return '你好';
}

console.log(return_data());


/* 特殊的返回情况 */
function return_numbers() {
    return 1, 2, 3;  // 函数返回多个值, 最后一个值作为返回值
}

console.log(return_numbers())

/* 带有参数的返回值 */
function add_number(num_1, num_2) {
    return num_1 + num_2;
}

console.log(add_number(11, 22));

/* 向没有形式参数的函数传递参数 */
function not_attr_func() {
    // console.log(number);
    console.log(arguments);  // arguments 是一个对象, 函数调用时传递的参数会保存在 arguments 中
}

not_attr_func(1, 2, 3, 4);

/* 自执行函数 匿名函数 */
!function () {
    console.log('自执行函数 - 1');
}();

(function () {
    console.log('自执行函数 - 2');
})();


/* 使用自执行函数模拟python中的装饰器 */
var inner_func;
!function () {
    function _inner_func() {
        console.log('这是一个内部函数...')
    }
    inner_func = _inner_func;
}();


inner_func();
~~~

​		

### (3)	向沒有形式參數的函數傳遞參數

~~~js
function not_attr_func() {
    // console.log(number);
    console.log(arguments);  // arguments 是一个对象, 函数调用时传递的参数会保存在 arguments 中
}
~~~



### (4)	自執行函數

~~~js
//方式一
!function () {
    console.log('自执行函数 - 1');
}();

// 方式二
(function () {
    console.log('自执行函数 - 2');
})();
~~~



## 1-4、	判斷語句

~~~js
var num_1 = 1;
var num_2 = '1';

// == 默认将数据转为同一类型后比较大小
if (num_1 == num_2) {
    console.log('相等...');
} else {
    console.log('不相等...');
}

// === 严格比较，数据类型也必须相同
if (num_1 === num_2) {
    console.log('相等...');
} else {
    console.log('不相等...');
}


/* 三目运算 */
var num_3 = 1;
var num_4 = 2;
var max_num = num_3 > num_4 ? num_3 : num_4;
console.log(max_num);


// 如果发现一段比较恶心的三目运算直接丢给AI
/*
    1.先判断 num_3 < num_4 （1 < 2），结果为真
    2.继续判断 1 < num_4 （1 < 2），结果为真
    3.再判断 3 < num_3 （3 < 1），结果为假
    4.因此返回值 'b'
*/
var result = num_3 < num_4 ? 1 < num_4 ? 3 < num_3 ? 'a' : 'b' : 'c' : 'd';
console.log(result);


/* 逻辑运算 && || ! */
var x = 1;
var y = 2;
result = x > y && x < y;
console.log(result);
result = x > y || x < y;
console.log(result);
result = !(x > y);
console.log(result);


/* 控制流 */
var day = new Date().getDay();
switch (day) {
    case 0:
        console.log('星期日');
        break;
    case 1:
        console.log('星期一');
        break;
    case 2:
        console.log('星期二');
        break;
    case 3:
        console.log('星期三');
        break;
    case 4:
        console.log('星期四');
        break;
    case 5:
        console.log('星期五');
        break;
    case 6:
        console.log('星期六');
}
~~~



## 1-5、	數組

~~~js
/* 在js中创建数组的方式有两种 */

// 使用对象创建数组
var my_array_1 = new Array(1, 2, 3, 4, '5');
console.log('实例化对象创建的数组:', my_array_1);


// 使用字面量的方式创建数组
var my_array_2 = [11, 22, 33, '44', 55.55];
console.log('使用字面量的方式创建的数组:', my_array_2);


// 使用元素下标取值
console.log('使用元素下标取值:', my_array_2[0], my_array_2[1], my_array_2[2], my_array_2[3], my_array_2[4]);
// 获取数组长度
console.log(my_array_2.length);
// 修改数组元素
my_array_2[0] = '11';
console.log(my_array_2);
// 在数组结尾添加一个新的元素
my_array_2.push(66);
console.log(my_array_2);
// 取出数组末尾最后一个元素
console.log(my_array_2.pop());
console.log(my_array_2);
// 在数组开头添加新元素
my_array_2.unshift(0);
console.log(my_array_2);
// 获取数组开头第一个元素
console.log(my_array_2.shift());
console.log(my_array_2);

// splice: 第一个参数是删除元素的索引, 第二个参数是删除的个数, 第三个参数是在删除的元素位置上添加的元素
my_array_2.splice(1, 2, 'a', 'b', 'c');
console.log(my_array_2);
~~~



## 1-6、	循環

~~~js
/* for while */
var my_array = [1, 2, 3, 4, 5];

for (var i = 0; i < my_array.length; i++) {
    console.log(my_array[i]);
}

console.log('-'.repeat(30))

var i = 0;
while (i < my_array.length) {
    console.log(my_array[i]);
    i++;
}

~~~

### (1)	for

~~~js
var array = [1, 4, 5];
  
  for(var index = 0; index < array.length; index++){
      result = array[index];
      alert(result);
  }
~~~

### (2)	while

~~~js
var array = [1, 4, 5];        
  var index = 0;
  
  while (index < array.length) {
      result = array[index];
      alert(result);
      index++;
  }
~~~

## 1-7、	創建對象

~~~js
/* 字面量创建对象 */
var obj_1 = {
    "name": "admin-1",
    "age": 18,
    "print_info": function () {
        console.log(this.name, this.age); // this: 类似于python中的self
    }
};


console.log(obj_1);
console.log(obj_1.name);
obj_1.print_info();


console.log('-'.repeat(30));

/* 构造函数创建对象 */
function Person_1(name, age) {
    this.name = name;
    this.age = age;
    this.print_info = function () {
        // console.log(this.name, this.age);
        console.log(`my name is ${this.name}, age is ${this.age}`);
    }
}

var obj_2 = new Person_1('admin-2', 13);
console.log(obj_2);
console.log(obj_2.age);
obj_2.print_info();

console.log('-'.repeat(30));

/* new 创建对象 */
var obj_3 = new Object();
obj_3.name = 'admin-3';
obj_3.run_function = function () {
    console.log('obj_3的方法被执行...');
}


console.log(obj_3);
console.log(obj_3.name);
obj_3.run_function();
~~~

## 1-8、	定時器

~~~js
/* setTimeout: 延迟执行一次 */
function run_test() {
    console.log('这是一个测试函数...');
}

// timeout: 单位是毫秒
// setTimeout(run_test, 3000);


/* setInterval: 周期执行 */
// setInterval(run_test, 1000);

// 关闭定时器
// var handler = setInterval(run_test, 1000);  // 当前已经在执行了
// clearInterval(handler);

// 方法置空
setInterval = function () {
    console.log('setInterval被关闭了...');
    console.log(arguments);
}
setInterval(run_test, 1000);

~~~

### (1)	setTimeout   延遲執行一次

### (2)	setInterval     週期執行

## 1-9、	異步

### (1)	setTimeout

~~~js
// 1.同步代码示例
// console.log('第一行...');
// console.log('第二行...');
// console.log('第三行...');


// 2.异步代码示例
// console.log('开始...');
// function printMessage() {
//     console.log('我是两秒后才被执行的函数...');
// }
// setTimeout(printMessage, 2000);
//
// console.log('结束...');


// 3.多个定时器的执行顺序
console.log('开始...');
function print_1() {
    console.log('第一个定时器: 等待一秒');
}

function print_2() {
    console.log('第二个定时器: 等待两秒');
}

setTimeout(print_1, 1000);
setTimeout(print_2, 2000);
console.log('结束...');


// 回调地狱
console.log('\n=== 回调地狱示例 ===');
setTimeout(() => {
    console.log('第一层');
    setTimeout(() => {
        console.log('第二层');
        setTimeout(() => {
            console.log('第三层');
        }, 1000);
    }, 1000);
}, 1000);
~~~



### (2)	Promise

~~~js
/*
    1. Promise的基本概念：处理异步操作的一种方式
    2. Promise的三种状态：pending（进行中）、fulfilled（成功）、rejected（失败）
    3. Promise的基本用法
*/

/* 简单的Promise代码示例 */
// function simplePromise() {
//     var promise = new Promise(function (resolve, reject) {
//         // 模拟异步操作
//         var success = false;
//
//         if (success) {
//             resolve('操作成功...');
//         } else {
//             reject('操作失败...');
//         }
//     });
//     return promise;
// }
//
//
// var obj = simplePromise();
// obj.then(function (result) {
//     console.log(result);
// }).catch(function (error) {  // catch方法用于捕获错误, 类似python中的except
//     console.log(error);
// })


/* 带延迟的Promise示例 */
// function delayPromise() {
//     var promise = new Promise(function (resolve, reject) {
//         console.log('promise开始执行...');
//
//         // 模拟延迟操作
//         setTimeout(function () {
//             resolve('延迟1秒后操作成功...');
//         }, 1000);
//     });
//     return promise;
// }
//
// console.log('调用延迟promise任务之前...');
// delayPromise().then(function (result) {
//     console.log('成功:', result);
// })
// console.log('调用延迟promise任务之后...');


/* Promise链式调用案例 */
function step_1() {
    return new Promise(function (resolve, reject) {
        setTimeout(function () {
            console.log('第一步完成...');
            resolve('result: step_1...');
        }, 1000)
    })
}

function step_2(step_1_result) {
    return new Promise(function (resolve, reject) {
        setTimeout(function () {
            console.log('第二步完成, 第一步的结果为:', step_1_result);
            resolve('result: step_2...');
        }, 1000)
    })
}

function step_3(step_2_result) {
    return new Promise(function (resolve, reject) {
        setTimeout(function () {
            console.log('第三步完成, 第二步的结果为:', step_2_result);
            resolve('result: step_3...');
        }, 1000)
    })
}

// 链式调用示例
step_1().then(step_2).then(step_3).then(function (result) {
    console.log('最终结果为:', result);
});


~~~



### (3)	使用python

~~~python
# -*- coding: utf-8 -*-
# @Time    : 2025/5/12 20:54
# @Author  : 顾安
# @File    : 5.python中的异步任务.py

import asyncio


def callback(future):
    print(future)
    print(future.result)


async def worker():
    data_list = list()
    for _ in range(5):
        await asyncio.sleep(1)
        data_list.append(_)
    return data_list


async def main():
    task = asyncio.create_task(worker())
    # result = await task
    # print(result)
    # task.add_done_callback(callback)  # 回调

    # result = await asyncio.wait([task])
    # print(result)

    result = await asyncio.gather(task)
    print(result)

asyncio.run(main())

~~~



### (4)	async

~~~js
/* async/await */

function run_async() {
    return new Promise(function (resolve) {
        var async_data = 'async data';
        resolve(async_data);
    });
}


async function get_async_result() {
    var result = await run_async();
    console.log(result)
}

// get_async_result();

// 使用箭头函数获取任务信息
// get_async_result().then(function () {
//     console.log('任务执行完毕...');
// })

get_async_result().then(() => {
    console.log('任务执行完毕...')
})
~~~



## 1-10、	json對象

~~~js
var json_str = '{"name": "admin", "age": 18}';
var json_data = JSON.parse(json_str);  // 将字符串转为对象

console.log(typeof json_data);
console.log(json_data);
console.log(json_data.name);

console.log('-'.repeat(30));

var json_string = JSON.stringify(json_data);
console.log(typeof json_string);
console.log(json_string);
~~~



## 1-11、	ajax請求

~~~js
    function getPosts() {
        $.ajax({
            // 请求的url
            url: 'https://jsonplaceholder.typicode.com/posts',
            // 请求方法
            method: 'GET',
            // 指定数据类型为json
            dataType: 'json',
            // 是否为异步请求
            async: true,
            // 请求参数, 一般发送post请求时使用
            data: {},
            // 请求成功之后的回调函数
            success: function (response) {
                console.log('请求成功:', response);
                displayPosts(response);
            },
            error: function (error) {
                console.log('请求失败:', error);
                handleError(error);
            }

        })
    }

    function displayPosts(posts) {
        const postList = document.getElementById('postList');
        if (postList) {
            postList.innerHTML = posts
                .slice(0, 10) // 只显示前10篇文章
                .map(post => `
                        <div class="post">
                            <h3>${post.title}</h3>
                            <p>${post.body}</p>
                        </div>
                    `)
                .join('');
        }
    }

    function handleError(error) {
        const errorDiv = document.getElementById('error');
        if (errorDiv) {
            errorDiv.textContent = `获取数据失败：${error}`;
        }
    }
~~~



## 1-12、	瀏覽器對象

~~~js
// console.log(window);
console.log(global);  //node全局对象

/*
* 在window对象中比较重要的几个方法
*   1.document: 文档对象, 用于操作HTML元素
*   2.navigator: 导航对象, 用于获取浏览器信息
*   3.location: 位置对象, 用于获取当前页面的URL信息
*   3.frames: 框架对象, 用于操作框架和查询框架
*   4.history: 历史对象, 用于操作浏览器的历史记录
*   5.screen: 屏幕对象, 用于获取屏幕信息
*
* 以上几个对象需要在浏览器控制台执行
* */
~~~





---

# 2、	瀏覽器調試技巧

# 3、	HOOK技術



# 4、	JS調用和扣代碼



# 5、	摘要算法



# 6、	對稱加密



# 7、	非對稱加密





# 8、	webpack打包方式



# 9、	SM國密系列



# 10、	wasm專題



# 11、	微信小程序逆 向



# 12、	JS混淆技術



# 13、	AST技術專題



# 14、	RPC技術



# 15、	字體反爬



# 16、	補環境系列



# 17、	補環境框架學習



# 18、	COOKIE反爬



# 19、	瑞數安全產品



# 20、	reese84系列產品



# 21、	驗證碼











