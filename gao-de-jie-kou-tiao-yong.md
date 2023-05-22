# 高德接口调用

请求数据，得到所在位置的adcode 区域代号，然后将该区域的边界加载到地图上

```javascript
// IP定位
axios.get("https://restapi.amap.com/v3/ip", {
  params: {
    key: "39bfea35586997e21b7598082011c3d0"
  }
}).then(response => {
  const { city, rectangle, adcode } = response.data;
  var positions = rectangle.split(";");
  var arr = [];
  positions.forEach(item => {
    arr.push(item.split(","))
  })

  let adJson = 'https://geo.datav.aliyun.com/areas_v3/bound/' + adcode + '.json'
  var geoLayer = new ol.layer.Vector({
    source: new ol.source.Vector({
      url: adJson, // 
      format: new ol.format.GeoJSON() // 
    })
  });
  map.addLayer(geoLayer)
})
```
