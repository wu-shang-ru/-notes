# 稍微記錄一下免得自己忘記

兩種方式可以選擇

### 一、以link為撰寫方式，寫在html裡面

//for 手機裝置(螢幕尺寸<768px)
<link href="style_mobile.css" rel="stylesheet" type="text/css" media="screen and (max-width:767px)">

//for 平板裝置(768px<螢幕尺寸<1024px)
<link href="style_pad.css" rel="stylesheet" type="text/css" media="screen and (min-width:768px) and (max-width:1024px)">

//for 一般電腦裝置(螢幕尺寸>1025px)
<link href="style_desktop.css" rel="stylesheet" type="text/css" media="screen and (min-width:1025px)">

### 二、以@media為撰寫方式，寫在CSS裡面

//共用區 此區會最快載入
body{...}
html{...}
//for 手機裝置(螢幕尺寸<768px)
@media screen and (max-width:767px){
   css for mobile .......
}

//for 平板裝置(768px<螢幕尺寸<1024px)
@media screen and (min-width:768px) and (max-width:1024px){   
   css for pad .......
}

//for 一般電腦裝置(螢幕尺寸>1025px)
@media screen and (min-width:1025px){   
   css for desktop .......
}

//for 手機裝置或平板裝置(裝置直擺的時候)
 @media screen and (orientation:portrait) { 
   …
 }

//for 手機裝置或平板裝置(裝置橫擺的時候)
 @media screen and (orientation:landscape){ 
   …
 }


-------------------------------------------------------
參考：https://yuci119.blogspot.com/2017/12/rwdcssmedia-queries.html
