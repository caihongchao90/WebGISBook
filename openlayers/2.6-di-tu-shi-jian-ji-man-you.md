# 地图事件及漫游

## 一、地图事件

在地图上点击添加要素点

```javascript
let  source = new ol.source.Vector({
});
let layer = new ol.layer.Vector({
  source
})
map.addLayer(layer);
map.on("click", (evt) => {
  let position = evt.coordinate;
  let ar point = new ol.Feature({
    geometry: new ol.geom.Point(position)
  })
  source.addFeature(point)
})
```

## 二、漫游

漫游核心接口，下面代码实现，点击什么地方飞行到什么地方&#x20;

* map.getView().animate()

```javascript
map.on("click", (evt) => {
  let position = evt.coordinate;
  map.getView().animate({
    center: position,
    zoom: 10
  })
})
```
