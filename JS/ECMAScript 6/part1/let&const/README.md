- 閱讀[良葛格](https://openhome.cc/Gossip/ECMAScript/LetConst.html)的文件後將筆記稍做簡短修正。

- 使用Node.js來做練習，如果沒有node.js先安裝完畢後再來開始往下閱讀。

***

- 在 ECMAScript 6 中，宣告變數的話建議使用 let，這可以讓變數在行為上看起來，比較像是其他程式語言中的變數該有的行為。例如，終於有區塊範圍了：

```
> if(true) {
...     let y = 10;
... }
undefined
> console.log(y);
ReferenceError: y is not defined
    at repl:1:13
    at ContextifyScript.Script.runInThisContext (vm.js:50:33)
    at REPLServer.defaultEval (repl.js:240:29)
    at bound (domain.js:301:14)
    at REPLServer.runBound [as eval] (domain.js:314:12)
    at REPLServer.onLine (repl.js:441:10)
    at emitOne (events.js:121:20)
    at REPLServer.emit (events.js:211:7)
    at REPLServer.Interface._onLine (readline.js:282:10)
    at REPLServer.Interface._line (readline.js:631:8)
```

let也不會有Hoisting，例如：

```
console.log(x);  // ReferenceError
let x = 10;
```

在全域範圍使用 let 宣告變數，變數並不會成為全域物件的特性：

```
> let x = 10;
undefined
> this.x;
undefined
```

你可以使用 {} 來定義區塊，而當中使用的 let 宣告的變數存在於該區塊範圍，例如：

```
let y = 10;
{
    let y = 20;
    console.log(y); // 20
}
console.log(y);     // 10
```

區塊內外都有設置相同名稱的變數，在其他語言來說可能會不行，如java會抱怨已經使用過此變數，但ECMAScript 6中則沒有這個限制，只要同名的變數不是在同一個區塊裡就行。

let 簡單來說，就是宣告區塊變數，然而這也就讓它還是有些地方與常見的程式語言變數不太一樣，例如，底下的程式會如何呢？

```
let y = 10;
{
    console.log(y); 
    let y = 20;
}
```

顯示出來的不是10，而是ReferenceError，因為y在區塊內外都有被宣告，而在這之間的區塊稱為暫時死區(Temporal dead zone)。

如果可以使用 let 宣告變數，我們可以直接這麼寫：

```
var openhome = openhome || {};
{
    let x = 10;
    function validate() { // validate 只在區塊中可見
        return x;
    }
    openhome.validate = validate;
    // 其他...
}
console.log(openhome.validate()); // 10
```

- const需要一個值指定給他，不能只宣告為const但沒有值。

***

來源參考良葛格。
