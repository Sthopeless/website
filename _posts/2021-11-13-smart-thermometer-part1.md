---
layout: post
title: "Smart Fever Thermometer (Part #1)"
author: sthope
image: 
categories: [ MQTT, Tasmota, Sthope Projects, Thermometer ]
comments: true

---

<html>
<head>

<meta name="viewport" content="width=device-width, initial-scale=1.0">
<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
}

.header {
  text-align: center;
  padding: 32px;
}

.row {
  display: -ms-flexbox;
  display: flex;
  -ms-flex-wrap: wrap;
  flex-wrap: wrap;
  padding: 0 4px;
}

.column {
  -ms-flex: 50%;
  flex: 50%;
  padding: 0 4px;
}

</style>
</head>
<body>

<div class="header" id="myHeader">
  <h1>Smart Thermometer</h1>
  <p><img src="https://cloud.sthope.dev/apps/files_sharing/publicpreview/oqc3rNmkdjGCgrS?x=1196&y=481&a=true&file=sthope_smart_thermometer.png" style="width:50%"></p>

</div>

Hardware:<br>
- <a href="https://bit.ly/3FmXdcl">ESP32</a><br>
- <a href="https://bit.ly/3kXADz5">Display i2c</a><br>
- <a href="https://bit.ly/30ruJPq">Battery Charger w/Protection</a><br>
- 18650 Battery<br>
- <a href="https://bit.ly/3Fq0SG6">Red Laser Diode</a><br>
- <a href="https://bit.ly/30wRDEX">IR Temperature Sensor</a><br>
- <a href="https://bit.ly/3cw0k5r">MicroSwitch</a><br>
- <a href="https://bit.ly/3xavOaH">Buttons 6*6*4.3mm</a><br>

<div class="row"> 
  <div class="column">
    <img src="https://cloud.sthope.dev/apps/files_sharing/publicpreview/yAAHN8LZnse4S3T?x=1196&y=481&a=true&file=ESP32_board.png" style="width:80%">
    <img src="https://cloud.sthope.dev/apps/files_sharing/publicpreview/NPfrMbSXjYC9MDg?x=1196&y=481&a=true&file=MLX90614%2520Non-contact%2520Infrared%2520Temperature.png" style="width:71%">
    <img src="https://cloud.sthope.dev/apps/files_sharing/publicpreview/ESmF22ngpSXMZHF?x=1196&y=481&a=true&file=sideA.png" style="width:100%">
  </div>
  <div class="column">
    <img src="https://cloud.sthope.dev/apps/files_sharing/publicpreview/soGPdW6sLa3s7Dx?x=1196&y=481&a=true&file=Red%2520Laser%2520Diode.png" style="width:100%">
    <img src="https://cloud.sthope.dev/apps/files_sharing/publicpreview/e3gBtTKAMZTEHDp?x=1196&y=481&a=true&file=batery_charger.png" style="width:100%">
    <img src="https://cloud.sthope.dev/apps/files_sharing/publicpreview/A9xc7bbmXzZ4SBi?x=1196&y=481&a=true&file=sideB.png" style="width:100%">
  </div>  
</div>

<script>
var elements = document.getElementsByClassName("column");

var i;

function two() {
  for (i = 0; i < elements.length; i++) {
    elements[i].style.msFlex = "50%";
    elements[i].style.flex = "50%";
  }
}
</script>

</body>
</html>
