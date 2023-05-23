# 2 创建地图

创建容器，将地图放入容器

```markup
<div id="mapDiv"></div>
```

可以将下面的样式给到页面，以便地图可以充满整个页面

```css
* {
  padding: 0;
  margin: 0;  
}
html,body{
  height: 100%;
  width: 100%;
}
#app{
  height: 100%;
}
#mapDiv {
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
  overflow: hidden;
}
```

引入必要的模块，并在目标容器mapDiv中创建OSM地图或者高德地图

```javascript
const gaode = new ol.layer.Tile({
  title: "高德地图",
  source: new ol.source.XYZ({
    url: 'http://wprd0{1-4}.is.autonavi.com/appmaptile?lang=zh_cn&size=1&style=7&x={x}&y={y}&z={z}',
    wrapX: false
  })
});
let map = new ol.Map({
  target: "mapDiv",
  layers: [
    //gaode,
    new ol.layer.Tile({
      source: new ol.source.OSM()
    })
  ],
  view: new ol.View({
    center: [104, 30],
    projection: 'EPSG:4326',
    zoom: 17,
  }),
});

```

