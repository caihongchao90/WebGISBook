# 添加文字标注

```javascript
const layer = new ol.layer.Vector({
  source: new ol.source.Vector()
})
var anchor = new ol.Feature({
  geometry: new ol.geom.Point([104.06, 30.67])
});
// 设置文字style
anchor.setStyle(new ol.style.Style({
  text: new ol.style.Text({
    // font: '10px sans-serif' 默认这个字体，可以修改成其他的，格式和css的字体设置一样
    text: '小菜小菜',
    fill: new ol.style.Fill({
      color: 'red'
    })
  })
}));
layer.getSource().addFeature(anchor);
map.addLayer(layer)
```
