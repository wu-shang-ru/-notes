- 閱讀[良葛格](https://openhome.cc/Gossip/ECMAScript/EnhancedFunction.html)的文件後將筆記稍做簡短修正。

- 使用Node.js來做練習，如果沒有node.js先安裝完畢後再來開始往下閱讀。

***

- 我覺得主要內容僅一小段，大部分內容還請至良葛格的網站上看。

函式實例有個 length 特性，可以用來取得定義函式時參數的個數，不過，在使用了 ... Rest 運算，或者是指定了預設值的參數，是不會計入 length 的：

```
> function f(a, b) {}
undefined
> f.length;
2
> function f2(a, b = 10) {}
undefined
> f2.length;
1
> function f3(a, ...b) {}
undefined
> f3.length;
1
```

***

來源參考良葛格。
