- 閱讀[良葛格](https://openhome.cc/Gossip/ECMAScript/NumberString.html)的文件後將筆記稍做簡短修正。

- 使用Node.js來做練習，如果沒有node.js先安裝完畢後再來開始往下閱讀。

***

在ES6中，可以使用 Number.MAX_SAFE_INTEGER 與 Number.MIN_SAFE_INTEGER 來取得可表達的最大整數與最小整數，而 Number.isSafeInteger 可用來檢查一個整數是否在安全範圍內：

```
> Number.MAX_SAFE_INTEGER;
9007199254740991
> Number.MIN_SAFE_INTEGER;
-9007199254740991
> Number.isSafeInteger(9007199254740992);
false
> Number.isSafeInteger(9007199254740991);
true
> Number.isInteger(9007199254740992)
true
```

兩個符點數之間，最小的差距，可以使用 Number.EPSILON 來取得：

```
> Number.EPSILON;
2.220446049250313e-16
```

可以使用0b(或0B)撰寫二進制，使用0o(或0O)撰寫八進制，如：

```
> 0b0100
4
> 0o77
63
```

可以使用Number來轉換成10進位數字，如：

```
> Number('0b0100')
4
> Number('0o77')
63
```

Number 的 toString()：

```
> (4).toString(2)
'100'
> (63).toString(8)
'77'
> parseInt('100', 2)
4
> parseInt('77', 8)
63
```

Number.isNaN只會判斷是否為NaN，其餘一律回傳false

Number.isFinite只會判斷若非number就會是false

從ES6開始可以使用兩個\`包覆一段文字，且可以將文字內含有$()的邏輯運算執行後回傳相同位置：

```
`1 + 2 = ${1 + 2}`
'1 + 2 = 3'
> let a = 1;
undefined
> let b = 2;
undefined
> `${a} + ${b} == ${a + b}`
'1 + 2 == 3'
> let o = {p : 10};
undefined
> `${o.p}`;
'10'
> let arr = [1, 2, 3];
undefined
> `Double arr: ${arr.map(n => n * 2)}`;
'Double arr: 2,4,6'
```

一般我們是使用：

```
let a = 10;
let b = 20;

f(`${a} + ${b} = ${a + b}`);
```

然而你也可以使用：

```
f`${a} + ${b} = ${a + b}`
```

就會將 ${} 外的字串分割出來，使用陣列儲存，然後運算出 ${a}、${b}、${a + b} 的值，最後再用陣列與運算出來的值來呼叫函式，也就是相當於：

```
f(['', ' + ', ' = ', ''], 10, 20, 30);
```

接下來，就看你的函式中怎麼處理這些值了，例如：

```
function f(strings, value1, value2, value3) {
    // 函式處理
}
```

如果你的標記模版中 ${} 數量是固定的，這樣就夠了，不過，若是事先無法決定個數，那麼可以定義以下這樣的函式：

```
function f(strings, ...values) {
    // 函式處理
}
```

- ...是ES6的Rest運算子，當它出現在參數的時候，會將呼叫的函式其餘的引數收集在一個陣列當中，當成函式引數傳入。

如果你想要 console.log 能顯示 '\n' 字樣，基本上在字串中要 escape：

```
> console.log('ABC\nEFG');
ABC
EFG
undefined
> console.log('ABC\\nEFG');
ABC\nEFG
undefined
> console.log(`ABC\nEFG`);
ABC
EFG
undefined
> console.log(`ABC\\nEFG`);
ABC\nEFG
undefined
```

在 ES6 中，有個 String.raw 函式，搭配標記模版，可以直接 escape，讓 \n 這類的字元，不會被轉譯為換行：

```
> String.raw`ABC\nEFG`
'ABC\\nEFG'
> console.log(String.raw`ABC\nEFG`)
ABC\nEFG
undefined
```

***

來源參考良葛格。
