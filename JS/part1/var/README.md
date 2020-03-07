- 閱讀[良葛格](https://openhome.cc/Gossip/ECMAScript/GettingStartedECMAScript5.html)的文件後將筆記稍做簡短修正。

- 使用Node.js來做練習，如果沒有node.js先安裝完畢後再來開始往下閱讀。

***

- js是動態定型語言，變數無須宣告屬性，執行時期會因內容物的不同而有不同屬性。

  ```
  var some = 10; //int
  some = 'caterpillar'; //string
  ```

  - 動態定型語言與靜態定型語言相比，好處是能夠減少程式碼的撰寫，壞處是可能需要常常注意是否為預期的型態。

  - 以下為使用靜態語言與動態語言的差別：
  ```
  //此為java寫法
  Object[] objects = {"caterpillar", new Integer(100), new Date()};
  String name = (String) objects[0];
  Integer score = (Integer) objects[1];
  Data time = (Date) objects[2];

  //此為js寫法
  var objects = ['caterpillar', 100, new Date()];
  var name = objects[0];
  var score = objects[1];
  var time = objects[2];
  ```

  相同的目的，js就用比較少的程式碼解決了。

  - 包在function裡的是區域變數，其餘的是全域變數：

  ```
  function func() {
    var y = 20;
  }
  func();
  console.log(y); //錯誤
  ```

  - 全域及區域有相同變數名稱，區域暫時覆蓋全域：

  ```
  var x = 10;
  function func() {
    var x = 20;
    console.log(x); // 顯示 20
  }

  func();
  console.log(x);  // 顯示 10
  ```

  - 可以使用delete來刪除屬性：

  ```
  //區域
  > var o = {o.x = 10};
  > delete o.x;
  true
  
  //全域
  > this.x = 10;
  > delete this.x;
  true
  ```

  - 非可組態屬性不可刪，例如`arr.length`。

  - 用var宣告的變數，在嚴格模式無法刪除。
***

來源參考良葛格。