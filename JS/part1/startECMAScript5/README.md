- 閱讀[良葛格](https://openhome.cc/Gossip/ECMAScript/GettingStartedECMAScript5.html)的文件後將筆記稍做簡短修正。

- 使用Node.js來做練習，如果沒有node.js先安裝完畢後再來開始往下閱讀。

***

```
  //可以使用node -v確認版本
  C:\workspace>node -v
  v8.9.1
```

- 直接輸入node可以進入互動模式，Ctel+D可以直接退出
  
  我們首先創建一個.js檔，名稱隨興取就好，這是等等給我們練習跑程式用。

  - 首先我們先輸入一段：

  ```
  console.log('Hello, World');
  ```

  然後我們就可以利用node執行。

  ```
  node helloworld.js
  Hello, World
  ```

  如果需要引數也可以調入：

  ```
  process.argv.forEach(function(arg, index) {
    console.log(arg + ', ' + index);
  });
  ```

  得出：

  ```
  C:\workspace>node helloworld.js arg1 arg2
  C:\Program Files\nodejs\node.exe, 0
  C:\workspace\helloworld.js, 1
  arg1, 2
  arg2, 3
  ```

  - 在ECMAScript 5的嚴格模式下，不可替未宣告的變數賦予值。

  ```
  'use strict';

  x = 10;
  console.log(x);
  ReferenceError: x is not defined
  ```

***

來源參考良葛格。