# canvas结合openlayers

<figure><img src="../.gitbook/assets/openlayers&#x26;canvas.gif" alt=""><figcaption></figcaption></figure>

在canvas绘制完毕后，用新绘制的图形作为参数传给openlayers的样式，完成标注点的动态更新

```javascript
// 创建一个Feature
let shape = new ol.Feature({
    geometry: new ol.geom.Point([104, 30])
  });
// 使用canvas绘制一个不规则几何图形
let canvas =document.createElement('canvas');
canvas.width = 50;
canvas.height = 50;
const ctx = canvas.getContext("2d")
let radius = 15;
let increase = true;
function draw(){
    ctx.clearRect(0,0,canvas.width,canvas.height)
    ctx.beginPath();
    ctx.arc(25,25,radius,0,Math.PI*2)
    ctx.closePath();
    ctx.fillStyle = "#ff2d51"
    ctx.fill();
    //绘制第二个⚪
    ctx.beginPath();
    ctx.arc(25,25,10,0,Math.PI*2)
    ctx.closePath();
    ctx.fillStyle = "#0088ff"
    ctx.fill();

    if(radius<15){
        increase=true
    }else if(radius>25){
        increase=false
    }
    if(increase){
        radius++
    }else{
        radius--
    }
    // 把绘制了的canvas设置到style里面
  let style = new ol.style.Style({
      image: new ol.style.Icon({
        img: canvas,
        imgSize: [canvas.width, canvas.height],
        rotation: 90 * Math.PI / 180
      })
  });
  // 应用具有不规则几何图形的样式到Feature
  shape.setStyle(style);  
  setTimeout(draw, 20)
}
draw()
var layer = new ol.layer.Vector({
  source: new ol.source.Vector()
})
layer.getSource().addFeature(shape);
map.addLayer(layer)
```
