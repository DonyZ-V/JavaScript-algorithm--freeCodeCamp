# JavaScript-algorithm--freeCodeCamp
###小练习的答案，仅供参考
1.翻转字符串
先把字符串转化成数组，再借助数组的reverse方法翻转数组顺序，最后把数组转化成字符串。
你的结果必须得是一个字符串
```js
function reverseString(str) {
  var arr = str.split("");
  arr.reverse();
  str = arr.join("");
  return str;
}

reverseString("hello");
//olleh
```
2.计算一个整数的阶乘
如果用字母n来代表一个整数，阶乘代表着所有小于或等于n的整数的乘积。
阶乘通常简写成 n!
例如: 5! = 1 * 2 * 3 * 4 * 5 = 120
```js
function factorialize(num) {
  if(num<1){
    return 1;    
  }else{
    return factorialize(num-1)*num;
  }
}

factorialize(5);
//120
```
3.如果给定的字符串是回文，返回true，反之，返回false。
如果一个字符串忽略标点符号、大小写和空格，正着读和反着读一模一样，那么这个字符串就是palindrome(回文)。
注意你需要去掉字符串多余的标点符号和空格，然后把字符串转化成小写来验证此字符串是否为回文。
函数参数的值可以为"racecar"，"RaceCar"和"race CAR"。
```js
function palindrome(str) {
  var reg=/[^0-9a-z]/gi;
  var prestr = str.replace(reg,"").toLowerCase();
  var currstr=prestr.split("").reverse().join("");
  return currstr==prestr?true:false;
}

palindrome("eye");
//true
```
4.找到提供的句子中最长的单词，并计算它的长度。
函数的返回值应该是一个数字。
```js
function findLongestWord(str) {
  var strArr = str.split(" ").map(function(e){return e.length;}).sort(function(a,b){
    return a-b;
  });
  var strNum=strArr[strArr.length-1];
  return strNum;
}

findLongestWord("The quick brown fox jumped over the lazy dog");
//6
```
5.确保字符串的每个单词首字母都大写，其余部分小写。
像'the'和'of'这样的连接符同理。
```js
function titleCase(str) {
  var upStr=str.split(" ").map(function(e){
    var a=e.toLowerCase().split("");
    a[0]=a[0].toUpperCase();
    return a.join("");
  }).join(" ");
  return upStr;
}

titleCase("I'm a little tea pot");
//I'm A Little Tea Pot
```
6.右边大数组中包含了4个小数组，分别找到每个小数组中的最大值，然后把它们串联起来，形成一个新数组。
提示：你可以用for循环来迭代数组，并通过arr[i]的方式来访问数组的每个元素。
```js
function largestOfFour(arr) {
  var arr1=[];
  for(var i=0;i<arr.length;i++){
    arr1[i]=arr[i].sort(function(a,b){return a-b;}).pop();
  }
  return arr1;
}

largestOfFour([[4, 5, 1, 3], [13, 27, 18, 26], [32, 35, 37, 39], [1000, 1001, 857, 1]]);
//[5,27,39,1001]
```

7.检查一个字符串(str)是否以指定的字符串(target)结尾。
如果是，返回true;如果不是，返回false

```js
function confirmEnding(str, target) {
  return str.substr(-target.length) == target;
}

confirmEnding("Bastian", "n");
//true
```

8.重要的事情说3遍！
重复一个指定的字符串 num次，如果num是一个负数则返回一个空字符串。
```js
function repeat(str, num) {
  var str1=str;
  if(num>0){
    for(var i=1;i<num;i++){
      str+=str1;
    }
    return str;
  }else{
    return "";
  }
}

repeat("abc", 3);
//abcabcabc
```
9.用瑞兹来截断对面的退路!
截断一个字符串！
如果字符串的长度比指定的参数num长，则把多余的部分用...来表示。
切记，插入到字符串尾部的三个点号也会计入字符串的长度。
但是，如果指定的参数num小于或等于3，则添加的三个点号不会计入字符串的长度。
```js
function truncate(str, num) {
  if(num>=str.length){
    return str;
  }
  if(num>3){
    return str.slice(0,num-3)+'...';
  }else{
    return str.slice(0,num)+'...';
  }
}

truncate("Absolutely Longer", 2);
//Ab...
```

10.猴子吃香蕉可是掰成好几段来吃哦！
把一个数组arr按照指定的数组大小size分割成若干个数组块。
例如:chunk([1,2,3,4],2)=[[1,2],[3,4]];
chunk([1,2,3,4,5],2)=[[1,2],[3,4],[5]];
```js
function chunk(arr, size) {
  var len=0;
  var arr1=[];
  while(len<arr.length){
    arr1.push(arr.slice(len,len+=size));
  }
  return arr1;
}

chunk([0, 1, 2, 3, 4, 5], 4);
//[[0,1,2,3],[4,5]]
```
11.打不死的小强！
返回一个数组被截断n个元素后还剩余的元素，截断从索引0开始。
```js
function slasher(arr, howMany) {
  return arr.slice(howMany);
}

slasher([1, 2, 3], 2);
//[3]
```
12.蛤蟆可以吃队友，也可以吃对手。
如果数组第一个字符串元素包含了第二个字符串元素的所有字符，函数返回true。
举例，["hello", "Hello"]应该返回true，因为在忽略大小写的情况下，第二个字符串的所有字符都可以在第一个字符串找到
["hello", "hey"]应该返回false，因为字符串"hello"并不包含字符"y"。
["Alien", "line"]应该返回true，因为"line"中所有字符都可以在"Alien"找到。
```js
function mutation(arr) {
  var lowerStr1 = arr[0].toLowerCase();
  var lowerStr2 = arr[1].toLowerCase();
  var str2Arr = lowerStr2.split("");
  for(var i=0; i<lowerStr2.length; i++){
    if(lowerStr1.indexOf(str2Arr[i])==-1){
      return false;
    }
  }
  return true;
}

mutation(["hello", "Hello"]);
//true
```

13.真假美猴王！
删除数组中的所有假值。
在JavaScript中，假值有false、null、0、""、undefined 和 NaN。
```js
function bouncer(arr) {
  return arr.filter(function(e){
    return e;
  });
}

bouncer([false, null, 0, NaN, undefined, ""]);
//[]
```

14.金克斯的迫击炮！
实现一个摧毁(destroyer)函数，第一个参数是待摧毁的数组，其余的参数是待摧毁的值。
```js
function destroyer(arr) {
  var argument=arguments;//这里必须把arguments的值复制下来
  for(var i=1;i<argument.length;i++){
    argument[0] = argument[0].filter(function(e){
      return argument[i]!==e;
    });
  }
  return argument[0];
}

destroyer([1, 2, 3, 1, 2, 3], 2, 3);
//[1,1]
```

15.我身在何处？
先给数组排序，然后找到指定的值在数组的位置，最后返回位置对应的索引。
举例：where([1,2,3,4], 1.5) 应该返回 1。因为1.5插入到数组[1,2,3,4]后变成[1,1.5,2,3,4]，而1.5对应的索引值就是1。
同理，where([20,3,5], 19) 应该返回 2。因为数组会先排序为 [3,5,20]，19插入到数组[3,5,20]后变成[3,5,19,20]，而19对应的索引值就是2。
```js
function where(arr, num) {
  arr.push(num);
  var arr1 = arr.sort(function(a,b){return a-b;});
  for(var i=0; i<arr1.length; i++){
    if(arr1[i]==num){return i;}
  }
}
//虽然写出来了，但是我觉得写的很臭

where([40, 60], 50);
//1
```
