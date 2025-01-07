# 211H10011
file:///C:/Users/nishi/OneDrive/kadai11.html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Step1.Leafletで地理院地図を表示する最も基本的なコード|Lefletの基本|埼玉大学谷謙二研究室</title>
  <link rel="stylesheet" href="https://unpkg.com/leaflet@1.3.0/dist/leaflet.css" />
  <script src="https://unpkg.com/leaflet@1.3.0/dist/leaflet.js"></script>
  <script>
    function init() {
      //地図を表示するdiv要素のidを設定
      var map = L.map('mapcontainer');
      //地図の中心とズームレベルを指定
      map.setView([35.40, 136], 5);
      //表示するタイルレイヤのURLとAttributionコントロールの記述を設定して、地図に追加する
      L.tileLayer('https://cyberjapandata.gsi.go.jp/xyz/std/{z}/{x}/{y}.png', {
          attribution: "<a href='https://maps.gsi.go.jp/development/ichiran.html' target='_blank'>地理院タイル</a>"
      }).addTo(map);
    }
  </script>
</head>
<body onload="init()">
  <div id="mapcontainer" style="width:600px;height:600px"></div>
</body>
</html>
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Step3.画面サイズに合わせる|Lefletの基本|埼玉大学谷謙二研究室</title>
  <link rel="stylesheet" href="https://unpkg.com/leaflet@1.3.0/dist/leaflet.css" />
  <script src="https://unpkg.com/leaflet@1.3.0/dist/leaflet.js"></script>
  <script>
    function init() {
      var map = L.map('mapcontainer', { zoomControl: false });
      map.setView([35.40, 136], 5);
      L.tileLayer('https://cyberjapandata.gsi.go.jp/xyz/std/{z}/{x}/{y}.png', {
          attribution: "<a href='https://maps.gsi.go.jp/development/ichiran.html' target='_blank'>地理院タイル</a>"
      }).addTo(map);
      L.control.scale({ maxWidth: 200, position: 'bottomright', imperial: false }).addTo(map);
      L.control.zoom({ position: 'bottomleft' }).addTo(map);
    }
  </script>
</head>
<body onload="init()">
  <!-- style属性に次のように設定するとブラウザの画面全体に表示される -->
  <div id="mapcontainer" style="position:absolute;top:0;left:0;right:0;bottom:0;"></div>
</body>
</html>
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Step5.マーカーの表示|Lefletの基本|埼玉大学谷謙二研究室</title>
  <link rel="stylesheet" href="https://unpkg.com/leaflet@1.3.0/dist/leaflet.css" />
  <script src="https://unpkg.com/leaflet@1.3.0/dist/leaflet.js"></script>
  <script>
    function init(){
      var map = L.map('mapcontainer',{zoomControl:false});
      //座標の指定
      var mpoint = [36.107538, 139.364083];
      map.setView(mpoint, 15);
      L.tileLayer('https://cyberjapandata.gsi.go.jp/xyz/std/{z}/{x}/{y}.png', {
        attribution: "<a href='https://maps.gsi.go.jp/development/ichiran.html' target='_blank'>地理院タイル</a>"
      }).addTo(map);
      //立正大学の位置にドラッグ可能なマーカーを地図に追加
      L.marker(mpoint,{title:"立正大学",draggable:true}).addTo(map);
      //熊谷市役所のマーカーを追加
      L.marker([36.147247,139.388888],{title:"熊谷市役所"}).addTo(map);
    }
  </script>   
</head>
<body onload="init()">
  <div id="mapcontainer" style="position:absolute;top:0;left:0;right:0;bottom:0;"></div>
</body>
</html>
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Step4.ベースレイヤの切り替え|Lefletの基本|埼玉大学谷謙二研究室</title>
  <link rel="stylesheet" href="https://unpkg.com/leaflet@1.3.0/dist/leaflet.css" />
  <script src="https://unpkg.com/leaflet@1.3.0/dist/leaflet.js"></script>
  <script>
    function init(){
      var map = L.map('mapcontainer',{zoomControl:false});
      map.setView([35.40, 136], 5);
      L.control.scale({maxWidth:200,position:'bottomright',imperial:false}).addTo(map);
      L.control.zoom({position:'bottomleft'}).addTo(map);
      //地理院地図の標準地図タイル
      var gsi =L.tileLayer('https://cyberjapandata.gsi.go.jp/xyz/std/{z}/{x}/{y}.png', 
        {attribution: "<a href='https://maps.gsi.go.jp/development/ichiran.html' target='_blank'>地理院タイル</a>"});
      //地理院地図の淡色地図タイル
      var gsipale = L.tileLayer('http://cyberjapandata.gsi.go.jp/xyz/pale/{z}/{x}/{y}.png',
        {attribution: "<a href='http://portal.cyberjapan.jp/help/termsofuse.html' target='_blank'>地理院タイル</a>"});
      //オープンストリートマップのタイル
      var osm = L.tileLayer('http://tile.openstreetmap.jp/{z}/{x}/{y}.png',
        {  attribution: "<a href='http://osm.org/copyright' target='_blank'>OpenStreetMap</a> contributors" });
      //baseMapsオブジェクトのプロパティに3つのタイルを設定
      var baseMaps = {
        "地理院地図" : gsi,
        "淡色地図" : gsipale,
        "オープンストリートマップ"  : osm
      };
      //layersコントロールにbaseMapsオブジェクトを設定して地図に追加
      //コントロール内にプロパティ名が表示される
      L.control.layers(baseMaps).addTo(map);
      gsi.addTo(map);
    }
  </script>   
</head>
<body onload="init()">
  <div id="mapcontainer" style="position:absolute;top:0;left:0;right:0;bottom:0;"></div>
</body>
</html>
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Step5.マーカーの表示|Lefletの基本|埼玉大学谷謙二研究室</title>
  <link rel="stylesheet" href="https://unpkg.com/leaflet@1.3.0/dist/leaflet.css" />
  <script src="https://unpkg.com/leaflet@1.3.0/dist/leaflet.js"></script>
  <script>
    function init(){
      var map = L.map('mapcontainer',{zoomControl:false});
      //座標の指定
      var mpoint = [36.107538, 139.364083];
      map.setView(mpoint, 15);
      L.tileLayer('https://cyberjapandata.gsi.go.jp/xyz/std/{z}/{x}/{y}.png', {
        attribution: "<a href='https://maps.gsi.go.jp/development/ichiran.html' target='_blank'>地理院タイル</a>"
      }).addTo(map);
      //立正大学の位置にドラッグ可能なマーカーを地図に追加
      L.marker(mpoint,{title:"立正大学",draggable:true}).addTo(map);
      //熊谷市役所のマーカーを追加
      L.marker([36.147247,139.388888],{title:"熊谷市役所"}).addTo(map);
    }
  </script>   
</head>
<body onload="init()">
  <div id="mapcontainer" style="position:absolute;top:0;left:0;right:0;bottom:0;"></div>
</body>
</html>
