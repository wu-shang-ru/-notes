- 閱讀[良葛格](https://openhome.cc/Gossip/ECMAScript/Destructuring.html)的文件後將筆記稍做簡短修正。

- 使用Node.js來做練習，如果沒有node.js先安裝完畢後再來開始往下閱讀。

***

ES6 支援 Destructuring 的語法，它的概念像是模式比對（Pattern match）（然而不完全是），當你將某個結構拆解並分別指定給變數時，經常出現某種模式時，就可以使用這類語法。例如：

```
var scores = [80, 90, 99];
var score0 = scores[0];
var score1 = scores[1];
var score2 = scores[2];
```

scores的結果來自某個函式的回傳值，在ES6中這樣的例子可以這樣寫：

```
let scores = [80, 90, 99];
let [score0, score1, score2] = scores;
```

只要是可以迭代的物件(具有可傳回迭代器的特性)，都可以運用這種語法，例如：

```
> let [a, b, c] = 'XYZ';
undefined
> a;
'X'
> b;
'Y'
> c;
'Z'
```

變數可以少於可迭代的數量，多餘的元素只是不會被理會而已，或者可以使用Rest運算：

```
> let lt = [10, 9, 8, 7, 6];
undefined
> let [head, ...tail] = lt;
undefined
> head;
10
> tail;
[ 9, 8, 7, 6 ]
```

- Rest運算... 會把剩餘的元素迭代給tail，也因為如此，寫函數式的程式碼會簡單許多：

```
function sum(numbers) {
    let [head, ...tail] = numbers;
    if(head) {
        return head + sum(tail);
    } else {
        return 0;
    }
}
console.log(sum([1, 2, 3, 4, 5])); // 15
```

就我觀察下來，這樣非常的方便，不用一一給所有變數指定名稱，只需要使用Rest運算就可以輕鬆解決。

而如果可迭代的數量少於變數的數量，則多餘的變數會以undefined呈現。

如果可迭代的數量少於變數，變數可以給予預設值，例如下面的c為3：

```
let [a, b, c = 3] = [1, 2];
```

如果只對某幾個元素有興趣呢？空下來就好了：

```
> let [x, ,y, , z] = [1, 2, 3, 4, 5];
undefined
> x;
1
> y;
3
> z;
5
```

但我想來想去也不知道這樣做的意義是什麼，文中良葛格也提到這樣的做法他並不建議，可見不是一個良好的風格。

不過如果只對尾元素有興趣的話，倒是可以這樣用：

```
> let [, ...tail] = [1, 2, 3, 4, 5];
undefined
> tail;
[ 2, 3, 4, 5 ]
```

- 在ES6中，若是指定的場合，...可以用來當作Rest運算，但若是在某個可迭代的物件之前，則它可以用來散佈(Spread)變數，如：

```
> let arr = [1, 2, 3];
undefined
> let arr2 = [...arr, 4, 5];
undefined
> arr2;
[ 1, 2, 3, 4, 5 ]
> function plus(a, b) {
...     return a + b;
... }
undefined
> plus(...[1, 2]);
3
```

過去在ES5你可能會這樣寫：

```
var o = {x : 10, y : 10};
var a = o.x;
var b = o.y;
```

但在ES6，你可以更直接的：

```
let o = {x : 10, y : 10};
let {x : a, y : b} = o;
```

如果變數與迭代元素名稱一樣，則可以這樣寫：

```
//不建議這樣寫，常常會搞混哪個是元素哪個是變數。
let o = {x : 10, y : 10};
let {x : x, y : y} = o;

//更建議這樣
let o = {x : 10, y : 10};
let {x, y} = o;
//第二行是變數，第一行是元素。

//也可以直接給予預設值
let {x, y, z = 10} = o;
```

當然也可以寫成巢狀結構，如：

```
let [[x, y, z], b, c] = [[1, 2, 3], 4, 5];

let {a: {x, y, z}, b, c} = {a: {x: 10, y: 20, z: 30}, b: 40, c: 50};
```

但這樣相對的複雜，不建議這樣使用，除非你真的用的到這種設計。

***

來源參考良葛格。
