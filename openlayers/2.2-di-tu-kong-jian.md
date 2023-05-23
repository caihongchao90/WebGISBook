# 2 地图控件



```javascript
/* 视图跳转控件 */
const ZoomToExtent = new ol.control.ZoomToExtent({
      extent: [110, 30, 160, 30],
})
map.addControl(ZoomToExtent)
/* 放大缩小控件 */
const zoomslider = new ol.control.ZoomSlider();
map.addControl(zoomslider)
//全屏控件
const fullScreen = new ol.control.FullScreen();
map.addControl(fullScreen)
```
