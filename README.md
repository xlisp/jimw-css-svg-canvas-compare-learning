# [Canvas与SVG与CSS画图对比](https://shanyue.tech/post/canvas-and-svg-shapes.html)

### 矩形
```css
.rect {
  width: 100px;
  height: 100px;
  border-radius: 15px;
}
```
```svg
<svg>
  <rect width="100" height="100" rx="15" ry="15"></rect>
</svg>
```
```js
const canvas = document.getElementById('rect')
const ctx = canvas.getContext('2d')
ctx.fillRect(0, 0, 100, 100)
ctx.fillRect(115, 0, 100, 100)
```
