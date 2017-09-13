## 图片懒加载

自己写了一个throtte函数来节流，

```
function throtte (fn, delay, least) {
  var startTime = new Date()
  return function () {
    var currentTime = new Date()
    if (currentTime - startTime <= least) {
      fn()
      startTime = currentTime
    } else {
      setTimeout(fn, delay)
    }
  }
}
```
监听scroll事件，比较图片位置距页面顶端的距离（offsetTop）以及视窗高度(document.documentElement.clientHeight)＋页面滚动距离(document.documentElement.scrollTop)来判断图片是否进入可视区域，加载是先用一个加载动效的gif，图片链接保存在data-src中，之后通过替换图片的src属性控制加载