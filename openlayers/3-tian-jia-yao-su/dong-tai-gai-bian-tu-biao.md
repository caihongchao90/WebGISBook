# 动态改变图标

正常添加要素，添加完成後，再添加click事件監控

```javascript
const layer = new ol.layer.Vector({
  source:new ol.source.Vector()
})
// 添加一个空心的五星
let star = new ol.Feature({
  geometry: new ol.geom.Point([104, 30])
});
star.setStyle(new ol.style.Style({
  image: new ol.style.RegularShape({
    points: 5,
    radius1: 20,
    radius2: 10,
    stroke: new ol.style.Stroke({
      color: 'red',
      size: 2
    })
  })
}));

layer.getSource().addFeature(star);
map.addLayer(layer)
// 监听地图点击事件
map.on('click', function (event) {
  let feature = map.forEachFeatureAtPixel(event.pixel, function (feature) {
    return feature;
  });
  
  if (feature) {
    // 将空心五星为红色实心五星
    let style = feature.getStyle().getImage();
    feature.setStyle(new ol.style.Style({
      image: new ol.style.RegularShape({
        points: 5,
        radius1: 20,
        radius2: 10,
        stroke: style.getStroke(),
        fill: new ol.style.Fill({
          color: 'red'
        })
      })
    }));
  }
});
```
