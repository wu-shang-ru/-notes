- 閱讀[良葛格](https://openhome.cc/Gossip/ECMAScript/JSON.html)的文件後將筆記稍做簡短修正。

- 使用Node.js來做練習，如果沒有node.js先安裝完畢後再來開始往下閱讀。

***

覺得JSON蠻重要的所以這邊特別先筆記起來。

JSON有一些規則需要注意：

- 名稱為字串，必須用 "" 雙引號包括。
- 值可以是"雙引號包括的字串，或者是數字、true、false、null、物件或陣列。
- 不支援 JavaScript 的 Date、Error、規則表示式或函式表示。

舉個例子：

```
var obj = {
    name : 'Justin',
    age : 35,
    childs : [ {name : 'hamimi', age : 3} ]
};
```

而換成JSON表示則為：

```
{
    "name":"Justin",
    "age":35,
    "childs":[
        {
            "name":"hamimi",
            "age":3
        }
    ]
}
```

### JSON.stringify

ECMAScript 5 規範中，如果要從物件建立 JSON 字串，只要使用 JSON.stringify。例如：

```
var obj = {
    name : 'Justin',
    age : 35,
    childs : [ {name : 'hamimi', age : 3} ]
};

var json = JSON.stringify(obj);

// {"name":"Justin","age":35,"childs":[{"name":"hamimi","age":3}]}
console.log(json);

//{"name":"Justin","age":35}
console.log(JSON.stringify(obj, ['name', 'age']));
```

JSON可以接受第二引數，若指定陣列則依陣列中列出的名稱，依序取得物件的鍵值來轉回JSON。

若傳回的值為undefined，則不會加入JSON字串。

上頭的 obj 轉換為 JSON 字串時，不想要有 age 特性的話，可以如下：

```
console.log(JSON.stringify(obj, function(key, value) {
    if(key === 'age'){
        return undefined;
    } 
    return value;
})); 
```

JSON可以接受第三引數，若是數字1到10，會自動換行並以指定數字做為縮排層次。指定字元，就會以指定的字元進行縮排。例如：

`console.log(JSON.stringify(obj, replacer, 2));`

顯示結果為兩個空格縮排：

```
{
  "name": "Justin",
  "childs": [
    {
      "name": "hamimi"
    }
  ]
}
```

如果物件本身有定義toJSON方法，則JSON.stringify會使用此方法進行JSON轉換。

```
var obj = {
    name : 'Justin',
    age : 35,
    toJSON : function() {
        return {
            name : this.name.toUpperCase(), 
            age  : this.age
        };
    }
};
```

### JSON.parse

如果想將JSON轉回JavaScript，可以使用JSON.parse，例如：

```
var json = '{"name":"Justin","age":35,"childs":[{"name":"hamimi","age":3}]}';
var obj = JSON.parse(json);

console.log(obj.name); // Justin
```

若是傳回的物件為undefined則不會被包含該特性。

***

來源參考良葛格。
