# 3 提示窗口

有两种方法创建提示窗口

* 传统的overlay方法（该方法的是用html方式显示图片，元素太多时，性能会严重受到影响。）
* Feature + Style的方式

1、写好html布局，并设置好其对应的css样式

```javascript
<div id="popup" class="ol-popup">
    <a href="#" id="popup-closer" class="ol-popup-closer"></a>
    <div id="popup-content"></div>
</div>
```

2、创建overlay，并绑定html元素

```javascript
import Overlay from 'ol/Overlay.js';
import * as olProj from 'ol/proj';
import {toStringHDMS} from 'ol/coordinate.js';
let container = document.getElementById('popup');
let content = document.getElementById('popup-content');
let overlay = new Overlay({
    element: container,
    autoPan: true,
    autoPanAnimation: {
        duration: 250
    }
});
```

3、监听地图点击事件

```javascript
map.on('singleclick', function(evt) {
    var coordinate = evt.coordinate;
    var hdms = toStringHDMS(olProj.transform(
        coordinate, 'EPSG:4326''EPSG:3857'));
    content.innerHTML = '<p>You clicked here:</p><code>' + hdms +
        '</code>';
    overlay.setPosition(coordinate);
    map.addOverlay(overlay);
});
```









