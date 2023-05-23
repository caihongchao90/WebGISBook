# 🤿 添加geojson数据

## 一、添加点

* 添加geojson数据只需要使用 ol.format.GeoJSON().readFeatures() 方法
* 可以对geojson数据的图层样式进行修改 layer.setStyle(style);

```javascript
let data = {
  type: "FeatureCollection",
  features: [
    {
      type: "Feature",
      geometry: {
        type: "Point",
        coordinates: [104, 30]
      }
    }
  ]
}
let source = new ol.source.Vector({
  /* 将geojson数据设置给实例数据源 */
  features: new ol.format.GeoJSON().readFeatures(data),
})

let layer = new ol.layer.Vector({
  source
})
const style = new ol.style.Style({
  image: new ol.style.Circle({
    radius: 8,
    fill: new ol.style.Fill({
      color: "#ff2d51"
    }),
    stroke: new ol.style.Stroke({
      color: '#333',
      width: 2
    })
  }),
})
layer.setStyle(style);
map.addLayer(layer);
```

## 二、添加线

跟点一样，只是geojson数据和样式设置不一样

```javascript
var data = {
  type: "FeatureCollection",
  features: [
    {
      type: "Feature",
      geometry: {
        type: "LineString",
        coordinates: [[114.30, 30.50], [116, 30.50]]
      }
    }
  ]
}
var source = new ol.source.Vector({
  /* 将geojson数据设置给实例数据源 */
  features: new ol.format.GeoJSON().readFeatures(data),
})

var layer = new ol.layer.Vector({
  source
})
const style = new ol.style.Style({
  //边线颜色
  stroke: new ol.style.Stroke({
    color: '#ff2d51',
    width: 4
  })
})
layer.setStyle(style);
map.addLayer(layer);
```

## &#x20;三、添加面

```javascript
var data = {
  type: "FeatureCollection",
  features: [
    {
      type: "Feature",
      geometry: {
        type: "Polygon",
        coordinates: [[[114.30, 30.50], [116, 30.50], [116, 30]],[[115.30, 31.50], [117, 31.50], [117, 31]]]
      }
    }
  ]
}
var source = new ol.source.Vector({
  /* 将geojson数据设置给实例数据源 */
  features: new ol.format.GeoJSON().readFeatures(data),
})
var layer = new ol.layer.Vector({
  source
})
const style = new ol.style.Style({
  //边线颜色
  stroke: new ol.style.Stroke({
    color: '#ff2d51',
    width: 2
  }),
  //设置填充色
  fill: new ol.style.Fill({
    color: "rgba(50, 50, 50, 0.3)"
  })
})
layer.setStyle(style);
map.addLayer(layer);
```

## 四、添加本地geojson数据

```javascript

var source = new ol.source.Vector({
  url: './map.geojson',
  format: new ol.format.GeoJSON()
})
console.log(source)
var layer = new ol.layer.Vector({
  source
})
const style = new ol.style.Style({
  image: new ol.style.Circle({
    radius: 8,
    fill: new ol.style.Fill({
      color: '#ff2d51'
    }),
    stroke: new ol.style.Stroke({
      color: '#333',
      width: 2
    })
  })
})
layer.setStyle(style)
map.addLayer(layer);

```

## 五、加载在线geojson数据

```javascript
var source = new ol.source.Vector({
  url: 'https://geo.datav.aliyun.com/areas_v3/bound/geojson?code=420100',
  format: new ol.format.GeoJSON()
})

//设置面图层样式
const style = new ol.style.Style({
  //填充色
  fill: new ol.style.Fill({
    color: 'rgba(50,50,50,0.4)'
  }),
  //边线颜色
  stroke: new ol.style.Stroke({
    color: '#ff2d5180',
    width: 2
  })
})
layer.setStyle(style)

```

