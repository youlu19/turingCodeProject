

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



## 1-6、循環

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

## (1)	for

~~~js
var array = [1, 4, 5];
  
  for(var index = 0; index < array.length; index++){
      result = array[index];
      alert(result);
  }
~~~

## (2)	while

~~~js
var array = [1, 4, 5];        
  var index = 0;
  
  while (index < array.length) {
      result = array[index];
      alert(result);
      index++;
  }
~~~



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











