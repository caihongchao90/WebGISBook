# 3 添加要素

添加要素到地图有两种方法，传统的`overlay和`Feature + Style的方式，下面对两种方法进行讲解

### 1.`overlay`+`css方法`

`这种方法可以方便地将css样式应用到添加在地图上的要素上。`

&#x20;    1、创建锚点容器

```markup
<div id="anchor"><img src="./img/anchor.png" alt="示例锚点"/></div>
```

&#x20;    2、创建点，并添加到地图上

```javascript
// 下面把上面的图标附加到地图上，需要一个ol.Overlay
let anchor = new ol.Overlay({
  element: document.getElementById('anchor')
});
// 关键的一点，需要设置附加到地图上的位置
anchor.setPosition([104, 30]);
// 然后添加到map上
map.addOverlay(anchor);
```

&#x20;     可以通过监听事件，控制要素的大小

```javascript
 // 监听地图层级变化
map.getView().on('change:resolution', function(){
  let style = anchor.getStyle();
  // 重新设置图标的缩放率，基于层级10来做缩放
  style.getImage().setScale(this.getZoom() / 10);
  anchor.setStyle(style);
})
```

### 2.Feature + Style的方式

这种方法在要素比较多的时候比较方便构建要素

1. 构建要素
2. 将要素添加到矢量数据源
3. 将矢量数据源添加到矢量图层
4. 将矢量图层添加到地图容器

```javascript
/* 1、构建要素 */
let point = new ol.Feature({
  geometry: new ol.geom.Point([104, 30])
})
let style = new ol.style.Style({
  image: new ol.style.Circle({
    radius: 10,
    fill: new ol.style.Fill({
      color: "#ff2d51"
    }),
    stroke: new ol.style.Stroke({
      color: "#333",
      width: 2
    })
  })
})
point.setStyle(style);
/* 2、将要素添加到矢量数据源 */
const source = new ol.source.Vector({
  features: [point]
})
/* 3、将矢量数据源添加到矢量图层 */
const layer = new ol.layer.Vector({
  source
})
/* 4、将矢量图层添加到地图容器 */
map.addLayer(layer)
```

&#x20;    style中的image参数也可以修改为图片路径

```javascript
```



