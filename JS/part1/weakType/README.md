- 閱讀[良葛格](https://openhome.cc/Gossip/ECMAScript/WeakType.html)的文件後將筆記稍做簡短修正。

- 使用Node.js來做練習，如果沒有node.js先安裝完畢後再來開始往下閱讀。

***

- JavaScript是屬於弱型別語言，在語法上較java來的簡潔，但需要確認型別是否是自己想要的。

以Java為例，Java是屬於強型別的程式語言，對於宣告的物件需要指定型別給他，且少有自動轉換之情況：

```
String number1 = "3";
String number2 = "2";
int result = number1 - number2;
```

而JavaScript則不需要宣告物件型別，所有物件只需使用`var`就可以完成宣告，直譯時會依照程式碼需求而有不同的物件型別。

```
var result = '3' - '2';
console.log(result);        // 1
console.log(typeof result); // number
```

JavaScript的基本型態有三種，`number`、`string `與`boolean`，必要時會自動轉型態為對應的包裹物件`Number`、`String `與`Boolean`：

```
> var number = 10;
undefined
> number.toString(2);
'1010'
> (10).toString(2);
'1010'
```

- 在JavaScript裡有一些字串轉數值的函式：

```
> parseInt('10 years old...XD');
10
> parseFloat('3.14159......');
3.14159
> parseInt('0x10');
16
> parseInt('010');
10
> parseInt('010', 10);
10
> parseInt('010', 8);
8
> 
```

可以特別注意一下，在JavaScript裡16進制使用0x，而如果是8進制則宣告為8進制。

而在JavaScript中，字串的內容若是數字，則+ - * /會有不同的優先選擇：

```
> '6' + '2';
'62'
> '6' - '2';
4
> '6' * '2';
12
> '6' / '2';
3 
```

可以觀察出來若是字串的 + 法會優先執行字串的串接

而在JavaScript中，布林可以拿來被運算，ture=1、fales=0

- 在JavaScript中有一個 False Family 成員，分別是0、NaN、''、null、undefinied

***

來源參考良葛格。
