# [Canvas与SVG与CSS画图对比](https://shanyue.tech/post/canvas-and-svg-shapes.html)

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
