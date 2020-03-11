- 閱讀[良葛格](https://openhome.cc/Gossip/ECMAScript/ArrowFunction.html)的文件後將筆記稍做簡短修正。

- 使用Node.js來做練習，如果沒有node.js先安裝完畢後再來開始往下閱讀。

***

- 箭頭函式 => 以及 Rest運算子 ... 是我主要來看的原因，這邊特別標註一下。

### 箭頭函式在function上的應用

我們可以先看一下尚未使用 => 之前的function：

```
> var arr = [1, 2, 5, 2, 5, 6, 9];
undefined
> arr.filter(function(elem) {
...     return elem % 2 === 0;
... }).map(function(elem) {
...     return elem * 10;
... });
[ 20, 20, 60 ]
```

而這是使用 => 過後的function：

```
> let arr = [1, 2, 5, 2, 5, 6, 9];
undefined
> arr.filter(elem => elem % 2 == 0).map(elem => elem * 10);
[ 20, 20, 60 ]
```

是不是簡短很多呢? 箭頭函式的目的性就是為了讓簡單的function可以簡略化，但並不建議在複雜的function上面使用。

如果有兩個以上的參數，箭頭函式的參數列必須使用()包含起來，沒有參數的話，寫一個()就行了。在只有一行的情況下，=>右邊的運算式自動return為箭頭函式的傳回值，如果要換行，使用{}，最回傳值使用return即可：

```
> let plus = (a, b) => a + b;
undefined
> plus(1, 2);
3
> let minus = (a, b) => {
...     return a - b;
... }
undefined
> minus(10, 5)
5
```

### 箭頭函式在this上的應用

箭頭函式不單單只是撰寫function 匿名函式，它在解析this方面，也並不是依照function的既有方式，例如：

```
this.x = 1;

var o = {
    x: 10,
    foo : function() {
        console.log(this.x);
    }
};

o.foo();  //10
```

換成 => ：

```
this.x = 1;

let o = {
    x: 10,
    foo : () => console.log(this.x)
};

o.foo(); //1
```

一般函式當中的this是以呼叫者來綁定的，而在箭頭函式中的this並不是以呼叫者來綁定，而是依照當時的語彙(Lexical)環境來綁定，說白了就是當時哪個環境包含{}this，就是哪個環境綁定this，一旦綁定了就不會改變，就算使用o.foo.call(o)也一樣。

上面的例子，就像下面這樣，也可以用這樣表達：

```
let who = this;

this.x = 1;

let o = {
    x: 10,
    foo : function() {
        console.log(who.x);
    }
};

o.foo();
```

再強化一次記憶，來看另外一個範例：

```
var o = {
    x   : 10,
    foo : function() {
        return {
            x : 20,
            doFoo : function() {
                console.log(this.x);
            }
        }
    }
};

o.foo().doFoo();
```

答案是20，那再看看下面這個：

```
let o = {
    x   : 10,
    foo : function() {
        return {
            x : 20,
            doFoo : () => console.log(this.x)
        }
    }
};

o.foo().doFoo();
```

答案就變成是10了，原因是因為在doFoo裡面環境是屬於o的，所以當使用箭頭函式裡的this時，就會以o為主。就像以下動作：

```
let o = {
    x   : 10,
    foo : function() {
        var who = this;
        return {
            x : 20,
            doFoo : function() {
                console.log(who.x);
            }
        }
    }
};

o.foo().doFoo();
```

###### super

在箭頭函式中出現super也要依當時的語彙環境決定，下面這個例子答案為10：

```
var o = {
    foo() {

        var o2 = {
            foo2() {
                console.log(super.x);
            }
        };

        o2.__proto__ = {x: 10};     

        o2.foo2();
    }
};

o.__proto__ = {x : 1};

o.foo();
```

而看看這個 => 的例子，答案為1：

```
var o = {
    foo() {

        var o2 = {
            foo2 : () => console.log(super.x)
        };

        o2.__proto__ = {x: 10};     

        o2.foo2();
    }
};

o.__proto__ = {x : 1};

o.foo();
```

***

來源參考良葛格。
