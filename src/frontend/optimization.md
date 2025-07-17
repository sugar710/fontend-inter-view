
## 前端性能优化

### Q. 前端常见的性能优化有哪些？

前端性能优化是为了提高用户体验和页面响应速度的一种手段。以下是一些常见的前端性能优化方法：

1. 优化图片：对图片进行压缩、使用合适的格式（例如，WebP）和尺寸，以及利用图片懒加载技术。
2. 使用CDN（内容分发网络）：将静态资源分发到全球各地的服务器，减少用户加载资源的延迟。
3. 缓存策略：利用浏览器缓存策略，如Cache-Control和ETag，减少重复请求。
4. 代码压缩与优化：通过压缩和移除不必要的代码，减小文件大小。同时优化代码逻辑，提高代码执行效率。
5. 异步加载：使用异步加载技术（如，async和defer属性）减少阻塞渲染的脚本。
6. 利用浏览器渲染优化：避免强制同步布局，减少重排和重绘。
  - 重排：当 DOM 的变化影响了元素的几何信息（DOM 对象的位置和尺寸大小），浏览器需要重新计算元素的几何属性，将其安放在界面中的正确位置，这个过程叫做重排。
  - 重绘：当一个元素更改了非几何属性（e.g. 背景、文本或阴影），但没有改变布局，重新把元素外观绘制出来的过程，叫做重绘
7. 使用CSS3硬件加速：利用GPU加速，提高动画和页面渲染性能。
8. 优化CSS选择器：使用简洁、高效的CSS选择器，提高渲染速度。
9. 代码分割与按需加载：通过代码分割和按需加载技术，降低首次页面加载时间。
10. 使用Web Workers：利用Web Workers进行后台处理，避免阻塞主线程。
11. 服务端渲染（SSR）与预渲染：利用服务端渲染和预渲染技术，加快首屏渲染速度。
12. 优化字体加载：减少字体文件大小，使用字体加载策略避免阻塞渲染。
13. 使用HTTP/2：使用HTTP/2协议，实现多路复用，降低网络延迟。
14. 优化资源优先级：利用`<link rel="preload">` 和 `<link rel="prefetch">` 标签，优化资源加载顺序。
15. 使用事件委托，利用冒泡机制处理事件。
16. 使用防抖、节流处理频繁触发的事件。
17. js动画使用requestAnimationFrame

以上只是一部分常见的前端性能优化方法，实际应用时还需要根据项目具体需求和场景来选择合适的优化策略。


### Q. 前端如何做错误监控？

前端错误监控是指捕获、记录和上报用户在实际使用过程中遇到的错误。错误监控有助于开发者发现和修复潜在的问题，提高应用的稳定性。以下是前端错误监控的一些建议：

1. 监控JavaScript运行时错误：可以使用`window.onerror` 或 `window.addEventListener('error')`来捕获JavaScript运行时错误。

   ```js
   window.onerror = function(message, source, lineno, colno, error) {
     // 处理错误信息
   };
   
   window.addEventListener('error', function(event) {
     // 处理错误信息
   });
   ```

2. 捕获Promise异常：使用`window.addEventListener('unhandledrejection')`来捕获未处理的Promise异常。

   ```js
   window.addEventListener('unhandledrejection', function(event) {
     // 处理错误信息
   });
   ```

3. 捕获资源加载错误：通过监听`error`事件，捕获例如图片、样式表、脚本等资源加载失败的错误。

   ```js
   document.addEventListener('error', function(event) {
     if (event.target.tagName === 'IMG' || event.target.tagName === 'LINK' || event.target.tagName === 'SCRIPT') {
       // 处理错误信息
     }
   }, true);
   ```

4. AJAX请求错误：当使用XMLHttpRequest或Fetch API进行AJAX请求时，可能会遇到网络错误或服务器错误。可以在请求的错误回调或catch方法中捕获：

   ```js
   fetch('https://example.com/data').then(response => {
     if (!response.ok) {
       throw new Error('Network response was not ok');
     }
     return response.json();
   }).catch(error => {
     // 处理错误信息
   });
   ```

--- 