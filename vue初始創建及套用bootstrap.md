- 這邊從頭創建vuecli開始，後續安裝Bootstarp

---

# 安裝vueCli

1. 首先執行：

```
npm install -g @vue/cli
npm install -g @vue/cli-init
```

2. 輸入`vue init webpack project-name`來建造vue專案資料夾及環境
3. 輸入基本設置資料，完成專案創建。
4. 可執行 npm run dev 確認有無成功創建。
5. 執行 npm install 將大部分需要用到的模組包下載至專案中

# 在VueCli上使用bootstarp

- 套用bootstarp的部分，cli2套用相對簡單些

- vue的bootstarp需要安裝jquery、popper.js及bootstarp本體

1. 輸入：

```
npm install --save popper.js //建立popper.js依賴
npm install jquery --save-dev //建立jquery依賴
```

2. 下載完成後，在webpack.config.js裡：
設置 `const webpack = require("webpack");`

3. 在module.exports末尾加上：

```
  plugins: [new webpack.ProvidePlugin({
    jQuery: 'jquery',
    $: 'jquery',
    jquery: 'jquery'
  })]
```

4. 安裝bootstarp

```
npm install bootstrap 下載bootstarp
```

5. 下載完成之後，依照index.js與bootstarp.css及bootstarp.js之間的相對路徑
在index.js做import

```
import '../../node_modules/bootstrap/dist/css/bootstrap.min.css';
import '../../node_modules/bootstrap/dist/js/bootstrap.min.js';
```

6. 至此可以測試bootstarp的navbar能否正常顯示，且下拉式選單有無正常。

`npm run dev`
