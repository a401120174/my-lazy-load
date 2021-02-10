# Image Lazy Loading implement

Lazy Loading 三種實現方式 <br>
參考資料: <br>
https://medium.com/@mingjunlu/lazy-loading-images-via-the-intersection-observer-api-72da50a884b7 <br>
https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API <br>

### Native Lazy Loading

在 HTML <img /> 標籤上加上 `loading="lazy"` 即可 <br>

```
<img src="image.jpg" alt="..." loading="lazy">
```

優點: 方便快速, 效能好 <br>
缺點: 目前許多瀏覽器尚未支援, Chrome 也得自行啟用功能 `Enable lazy image loading (#enable-lazy-image-loading)` 才會有效果 <br>

### Intersection Observer API

使用 `Intersection Observer API` 來實作, `Intersection Observer API` <br> 能方便地自動觀察目標元素是否進入或離開父層（或其外層）元素或瀏覽器的 viewport<br>

優點: 程式碼直覺, 效能好, 瀏覽器大多支援 <br>
缺點: IE 瀏覽器未支援, 得加上 polyfill https://github.com/w3c/IntersectionObserver/tree/main/polyfill <br>

### Listen scroll event

scroll 事件監聽搭配運用 `Element.getBoundingClientRect()` <br>
監聽圖片是否已出現在畫面中 <br>

優點: 瀏覽器幾乎完全支援 <br>
缺點: 效能差, 需搭配 passive event listeners 與 throttle 來減少效能損耗 <br>
