# 教科書
```
HTML5、CSS3、JavaScript、jQuery、jQuery UI、Ajax、RWD 網頁程式設計, 7/e
陳惠貞   碁峰資訊   2020-10-21
http://books.gotop.com.tw/download/AEL024100

https://drive.google.com/drive/folders/16ym-3wB2RzKeKpJGdCmkFwx2UmP3cO9k

Part 1 HTML5
第1章　網頁設計簡介
第2章　文件結構
第3章　資料編輯與格式化
第4章　圖片與表格(Table)
第5章　影音多媒體
第6章　表單(Form) ==> 使用者註冊表單  
```
# 第2章　文件結構
```
HTML 文件的根元素－<html> 元素 
HTML 文件的標頭－<head> 元素 
2-2-1 <title> 元素( 文件標題)
2-2-2  <meta> 元素( 文件相關資訊)
2-2-3　<link> 元素 (文件之間的關聯)   ????
2-2-4　<style> 元素 (嵌入CSS樣式表)

HTML 文件的主體－<body> 元素
2-3-1  <h1>~<h6>元素(標題1~6)
2-3-2  <p>元素(段落)
2-3-3　<div> 元素 (群組成一個區塊)
2-3-4　<!-- --> 元素 (註解)

HTML5 新增的結構元素 
<article>
<section>
<nav>
<header>
<footer>
<aside>
<main>
```
# 第3章　資料編輯與格式化
```
區塊格式
文字格式
插入或刪除資料－ <ins>、<del> 元素
項目符號與編號－ <ul>、<ol>、<li> 元素
定義清單－ <dl>、<dt>、<dd> 元素
超連結
相對URL 的路徑資訊－ <base> 元素
```
# 第4章　圖片與表格(Table)
```
嵌入圖片－ <img> 元素
4-1 嵌入圖片－ <img> 元素
4-1-1 圖片的寬度與高度
4-1-2 圖片的替代顯示文字


標註－ <figure>、<figcaption> 元素
4-2 標註－ <figure>、<figcaption> 元素


建立表格－ <table>、<tr>、<td>、<th> 元素
4-3 建立表格－<table>、<tr>、<td>、<th> 元素
4-3-1 跨列合併儲存格
4-3-2 跨行合併儲存格

表格標題－ <caption> 元素
4-4 表格標題－ <caption> 元素

表格的表頭、主體與表尾－<thead>、<tbody>、<tfoot> 元素
4-5  表格的表頭、主體與表尾－<thead>、<tbody>、<tfoot> 元素

直行式表格－ <colgroup>、<col> 元素
  4-6 直行式表格－<colgroup>、<col> 元素
```
# 第5章　影音多媒體
```
嵌入影片－ <video> 元素 ==> 上網找範例   學習底下屬性 有何用處?
    src、preload、autoplay、loop、muted、controls、crossorigin
嵌入聲音－ <audio> 元素 ==> 上網找範例   學習底下屬性 有何用處?
   src、preload、autoplay、loop、muted、controls、crossorigin

嵌入物件－ <object> 元素
嵌入Script － <script>、<noscript> 元素
   <noscript> 元素 ==> 用來針對不支援Script 的瀏覽器設定顯示內容
```
```
嵌入浮動框架－ <iframe> 元素 ==> 駭客最愛   網頁掛馬
   https://kknews.cc/zh-tw/tech/lzpxyoz.html
   https://codertw.com/%E5%89%8D%E7%AB%AF%E9%96%8B%E7%99%BC/253296/

   插入google map
     	<iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3615.002890183714!2d121.56235021471375!3d25.033975983972297!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x3442abb6da9c9e1f%3A0x1206bcf082fd10a6!2zMTEw5Y-w5YyX5biC5L-h576p5Y2A5L-h576p6Lev5LqU5q61N-iZnw!5e0!3m2!1szh-TW!2stw!4v1587956752277!5m2!1szh-TW!2stw" width="600" height="450" frameborder="0" style="border:0;" allowfullscreen="" aria-hidden="false" tabindex="0"></iframe>

      https://www.google.com.tw/maps/@23.546162,120.6402133,8z?hl=zh-TW
```
```
網頁自動導向==>在頭部head插入
    <meta http-equiv="refresh" content="5; url=https://www.google.com.tw/">
```
# 第6章　表單(Form) ==> 使用者註冊表單 
```
常見案例1:使用者註冊表單 
常見案例2:線上問卷調查網
```
```
建立表單－ <form>、<input> 元素
   表單與各種輸入欄位設計
   <form> 元素 屬性的各種設定 ==>method=“{get,post}”
   <input> 元素 屬性的各種設定 ==> type=“state”

HTML4.01 提供的輸入類型

6-2-1 submit、reset ( 提交與重設按鈕)
6-2-2 text ( 單行文字方塊)
6-2-3 radio( 選擇鈕 )
6-2-4 checkbox ( 核取方塊)
6-2-5 <textarea> ( 多行文字方塊 )
6-2-6 <select>、<option> ( 下拉式清單 )
6-2-7 password ( 密碼欄位)
6-2-8 hidden ( 隱藏欄位) ==> 作業:這有甚麼用?


HTML5 新增的輸入類型

6-3-1 email ( 電子郵件地址) ==> 如何驗證email格式的正確性 ?
6-3-2 url ( 網址)
6-3-3 search ( 搜尋欄位)
6-3-4 number ( 數字)
6-3-5 range ( 指定範圍的數字 )
6-3-6 color ( 色彩)
6-3-7 tel ( 電話號碼 )==> 如何驗證手機電話號碼格式?如何顯示預設格式
6-3-8 日期時間的顯示技術 ==> date、time、month、week、datetime-local 

按鈕－ <button> 元素
    type=“{submit,reset,button}” 屬性的用處

標籤－ <label> 元素
群組標籤－ <optgroup> 元素

將表單欄位框起來－<fieldset>、<legend> 元素



```
