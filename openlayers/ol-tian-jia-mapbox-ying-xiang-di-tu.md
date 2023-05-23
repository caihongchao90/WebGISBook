# ol添加mapbox影像地图

## 加载自定义地图

url地址[https://api.mapbox.com/styles/v1/{id}/tiles/{z}/{x}/{y}?access\_token={accessToken}](https://api.mapbox.com/styles/v1/%7Bid%7D/tiles/%7Bz%7D/%7Bx%7D/%7By%7D?access\_token={accessToken}%27)

* {id} 是地图的MapID，需要

```javascript
<div id="mapDiv"></div>

let map = new ol.Map({
  target: "mapDiv",
  layers: [
    new ol.layer.Tile({ 
      source: new ol.source.XYZ({
        url: 'https://api.mapbox.com/styles/v1/mapbox/satellite-v9/tiles/{z}/{x}/{y}?access_token=pk.eyJ1IjoiY2FpaG9uZ2NoYW8iLCJhIjoiY2xmcTkzZ3oyMWQ3ZjQycXp3dnJ3cnlyZSJ9.xAE7egcnXDHWU2hdbgShpQ',
        attributions: '© <a href="https://www.mapbox.com/about/maps/">Mapbox</a>',
        tileSize: 512,
        maxZoom: 18,
        projection: 'EPSG:3857',
        id: 'mapbox/streets-v11', // Mapbox样式ID
        accessToken: 'pk.eyJ1IjoiY2FpaG9uZ2NoYW8iLCJhIjoiY2xmcWRjdWg5MDdqZjQybzN2Mm1zZHltcyJ9.yJNjKMXDtt2y-dyOnhEUow' // Mapbox访问令牌
      })
    })
  ]
});
```

## 加载mapbox提供的公用图
