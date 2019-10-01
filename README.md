# [Canvas与SVG与CSS画图对比学习](https://shanyue.tech/post/canvas-and-svg-shapes.html)

### 矩形
```css
.rect {
  width: 100px;
  height: 100px;
  border-radius: 15px;
}
```
```html
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

## 多个图片合成
* canvas(用函数来描述css"herb",不断复用它,是学习css最快的方式 => canvas的λ化,用无穷多个小的函数来描述canvas,最后组合演算)
```clojure
;; <img id="scream" style="display: none;" src="./img/guoqi_background2.gif" alt="The Scream">

[:canvas#myCanvas {:width "300" :height "300"
                           :style {:border "1px solid #d3d3d3"}}
         "您的浏览器不支持canvas"]

(defn get-canvas []
  (let [c (.getElementById js/document "myCanvas")]
    (.getContext c "2d")))

(defn add-background []
  (let [ctx (get-canvas)
        img (.getElementById js/document "scream")]
    ;; 0,0代表插入的位置坐标,在左上角开始算
    (.drawImage ctx img 0 0)))

(let [ctx (get-canvas)
     img (.getElementById js/document "coverimage")]
 (.drawImage ctx img 0 0))

(add-background)
```

## 任意路径或者多边形

```js
  Facebook: {
    type: 'custom', customClassName: 'IT-Facebook', dataBboxX: 0, dataBboxY: 0, dataBboxW: 55, dataBboxH: 55, dataCX: 56/2, dataCY: 56/2,
    components: [
      {tag: 'path', attributes: {d: "M48.13 0H6.88A6.88 6.88 0 0 0 0 6.88v41.25A6.88 6.88 0 0 0 6.88 55h41.25A6.88 6.88 0 0 0 55 48.13V6.88A6.88 6.88 0 0 0 48.13 0z", fill:"#1976d2"}},
      {tag: 'path', attributes: {d: "M46.41 27.5h-8.6v-6.87c0-1.9 1.54-1.72 3.44-1.72h3.44v-8.6h-6.88A10.31 10.31 0 0 0 27.5 20.63v6.87h-6.87v8.59h6.87V55h10.31V36.09H43z", fill: "#fafafa"}},
    ]
  },
```
