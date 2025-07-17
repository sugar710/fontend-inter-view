## 手写实现功能

### Q. 实现节流函数

```js
/**
 * 节流：动作绑定事件，动作发生后一段时间后触发事件，
 * 在这段时间内，如果动作有发生了，则无视该动作，直到时间执行完后，才能重新触发
 * 原理：在每次函数执行前先判断是否存在定时器，存在则跳过本次执行，否则设置定时器
 */
function throttle(func, delay) {
  let lastTime = 0;
  return function(...args) {
    const now = Date.now();
    if (now - lastTime >= delay) {
      func.apply(this, args);  // 如果距离上次执行的时间超过 delay，就执行函数
      lastTime = now;  // 更新 lastTime
    }
  };
}
```

### Q. 实现防抖函数

```js
/**
 * 动作绑定事件，
 * 动作发生后在一定时间内触发事件，
 * 在这段时间内，如果动作发生了，则重新等待一定时间在触发事件
 *
 * 原理：在每次函数执行前先清空上一次设置的定时器
 * */
function debounce(func, delay) {
  let timer;
  return function(...args) {
    clearTimeout(timer);  // 清除之前的定时器
    timer = setTimeout(() => {
      func.apply(this, args);  // 延迟执行传入的函数
    }, delay);
  };
}
```