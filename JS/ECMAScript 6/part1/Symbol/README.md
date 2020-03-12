- 閱讀[良葛格](https://openhome.cc/Gossip/ECMAScript/Symbol.html)的文件後將筆記稍做簡短修正。

- 使用Node.js來做練習，如果沒有node.js先安裝完畢後再來開始往下閱讀。

***

在ES6中，比過去ES5多了一個symbol值。

symbol主要代表一個獨一無二的符號，如果在ES6中需要，就可以使用symbol，如：

```
> let x = Symbol()
undefined
> let y = Symbol('The description of this symbol')
undefined
```

使用Symbol時後面的字串只是描述，並不代表Symbol本身的值。

如果在A場合定義了Symbol'x'，那這個x就是獨一無二的，如果在B場合也定義了一個'x'，兩者也不會相等：

```
> Symbol('x') === Symbol('x')
false
```

可以理解成每個獨一無二的Symbol都有一個x描述。

而如果對Symbol使用toString則會傳回當時設定的字串描述：

```
> Symbol('for each method of xxx').toString()
'Symbol(for each method of xxx)'
```

###### Symbol.for

這是另外一種建立Symbol的方法，當你給定一個字串描述，它會在全域的符號註冊表（Symbol Registry）查找，如果有相同描述的字串就傳回，如果沒有就依指定的字串建立一個Symbol。

```
> let s1 = Symbol.for('symbol 1 for testing');
undefined
> let s = Symbol.for('symbol 1 for testing');
undefined
> s1 === s;
true
> let s2 = Symbol.for('symbol 2 for testing');
undefined
> s1 === s2;
false
```

本來是字串描述不代表Symbol本身，但現在卻用描述查找Symbol，確實頗怪，但目前階段就只能先這樣記。也應該盡可能避免使用此方法，畢竟符號註冊表建立在全域上，除非真的有很好的理由。

######　Symbol.iterator

ES6 也有一些 Symbol 上的內建特性儲存著符號，像是 Symbol.iterator 代表著迭代器符號：

```
> Symbol.iterator
Symbol(Symbol.iterator)
```

ES6中如果物件有函式(方法)可傳回迭代器，該函式會以 Symbol.iterator 符號作為特性儲存。想取得就可以透過 Symbol.iterator 符號取得：

```
> let arr = [1, 2, 3];
undefined
> let iterator = arr[Symbol.iterator]();
undefined
> iterator.next();
{ value: 1, done: false }
> iterator.next();
{ value: 2, done: false }
> iterator.next();
{ value: 3, done: false }
> iterator.next();
{ value: undefined, done: true }
```

###### Symbol.keyFor

可以當作查找Symbol有無存在全域符號註冊表中的方法，如果有就會傳回Symbol字串描述，沒有就會回傳undefined：

```
> let s1 = Symbol.for('s1 symbol');
undefined
> Symbol.keyFor(s1);
's1 symbol'
> Symbol.keyFor(Symbol.iterator);
undefined
```

***

來源參考良葛格。
