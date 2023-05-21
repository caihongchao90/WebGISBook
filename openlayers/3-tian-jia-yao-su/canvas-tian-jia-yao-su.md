# canvas 添加要素

先用canvas绘制出图标后，再使用普通要素添加方法添加至地图上

```javascript
let layer = new ol.layer.Vector({
  source: new ol.source.Vector()
})

// 使用canvas绘制一个不规则几何图形
let canvas =document.createElement('canvas');
canvas.width = 20;
canvas.height = 20;
let context = canvas.getContext("2d");
context.strokeStyle = "red";  
context.lineWidth = 1;  
context.beginPath();   
context.moveTo(0, 0);
context.lineTo(20, 10);
context.lineTo(0, 20);
context.lineTo(10, 10);
context.lineTo(0, 0);  
context.stroke();

// 把绘制了的canvas设置到style里面
let style = new ol.style.Style({
    image: new ol.style.Icon({
      img: canvas,
      imgSize: [canvas.width, canvas.height],
      rotation: 90 * Math.PI / 180
    })
});

// 创建一个Feature
let shape = new ol.Feature({
  geometry: new ol.geom.Point([104, 30])
});

// 应用具有不规则几何图形的样式到Feature
shape.setStyle(style);
layer.getSource().addFeature(shape);
map.addLayer(layer)
```
