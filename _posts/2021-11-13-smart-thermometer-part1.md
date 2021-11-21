---
layout: post
title: "Smart Fever Thermometer (Part #1)"
description: ""
author: sthope
image: 
categories: [ MQTT, Tasmota, Sthope Projects, Thermometer ]
comments: true
logo: "https://cloud.sthope.dev/apps/files_sharing/publicpreview/oqc3rNmkdjGCgrS?x=1196&y=481&a=true&file=sthope_smart_thermometer.png"
sideA: "https://cloud.sthope.dev/apps/files_sharing/publicpreview/ESmF22ngpSXMZHF?x=1196&y=481&a=true&file=sideA.png"
sideB: "https://cloud.sthope.dev/apps/files_sharing/publicpreview/A9xc7bbmXzZ4SBi?x=1196&y=481&a=true&file=sideB.png"
redlaser: "https://cloud.sthope.dev/apps/files_sharing/publicpreview/soGPdW6sLa3s7Dx?x=1196&y=481&a=true&file=Red%2520Laser%2520Diode.png"
ESP32_board: "https://cloud.sthope.dev/apps/files_sharing/publicpreview/yAAHN8LZnse4S3T?x=1196&y=481&a=true&file=ESP32_board.png"
ir_sensor: "https://cloud.sthope.dev/apps/files_sharing/publicpreview/NPfrMbSXjYC9MDg?x=1196&y=481&a=true&file=MLX90614%2520Non-contact%2520Infrared%2520Temperature.png"
battery_charger: "https://cloud.sthope.dev/apps/files_sharing/publicpreview/e3gBtTKAMZTEHDp?x=1196&y=481&a=true&file=batery_charger.png"

---

![logo]({{page.logo}})  

Hardware:

- <a href="https://bit.ly/3FmXdcl">ESP32</a>
- <a href="https://bit.ly/3kXADz5">Display i2c</a>
- <a href="https://bit.ly/30ruJPq">Battery Charger w/Protection</a>
- 18650 Battery
- <a href="https://bit.ly/3Fq0SG6">Red Laser Diode</a>
- <a href="https://bit.ly/30wRDEX">IR Temperature Sensor</a>

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
  display: -ms-flexbox; /* IE 10 */
  display: flex;
  -ms-flex-wrap: wrap; /* IE 10 */
  flex-wrap: wrap;
  padding: 0 4px;
}

/* Create two equal columns that sits next to each other */
.column {
  -ms-flex: 50%; /* IE 10 */
  flex: 50%;
  padding: 0 4px;
}

.column img {
  margin-top: 8px;
  vertical-align: middle;
}

/* Style the buttons */
.btn {
  border: none;
  outline: none;
  padding: 10px 16px;
  background-color: #f1f1f1;
  cursor: pointer;
  font-size: 18px;
}

.btn:hover {
  background-color: #ddd;
}

.btn.active {
  background-color: #666;
  color: white;
}
</style>
</head>
<body>

<!-- Header -->
<div class="header" id="myHeader">
  <h1>Smart Thermometer</h1>
</div>

<!-- Photo Grid -->
<div class="row"> 
  <div class="column">
    <img src="https://cloud.sthope.dev/apps/files_sharing/publicpreview/ESmF22ngpSXMZHF?x=1196&y=481&a=true&file=sideA.png" style="width:100%">
    <img src="https://cloud.sthope.dev/apps/files_sharing/publicpreview/A9xc7bbmXzZ4SBi?x=1196&y=481&a=true&file=sideB.png" style="width:100%">
    <img src="https://cloud.sthope.dev/apps/files_sharing/publicpreview/NPfrMbSXjYC9MDg?x=1196&y=481&a=true&file=MLX90614%2520Non-contact%2520Infrared%2520Temperature.png" style="width:100%">
  </div>
  <div class="column">
    <img src="https://cloud.sthope.dev/apps/files_sharing/publicpreview/soGPdW6sLa3s7Dx?x=1196&y=481&a=true&file=Red%2520Laser%2520Diode.png" style="width:100%">
    <img src="https://cloud.sthope.dev/apps/files_sharing/publicpreview/yAAHN8LZnse4S3T?x=1196&y=481&a=true&file=ESP32_board.png" style="width:100%">
    <img src="https://cloud.sthope.dev/apps/files_sharing/publicpreview/e3gBtTKAMZTEHDp?x=1196&y=481&a=true&file=batery_charger.png" style="width:100%">

  </div>  
</div>

<script>
// Get the elements with class="column"
var elements = document.getElementsByClassName("column");

// Declare a loop variable
var i;

// Full-width images
function one() {
    for (i = 0; i < elements.length; i++) {
    elements[i].style.msFlex = "100%";  // IE10
    elements[i].style.flex = "100%";
  }
}

// Two images side by side
function two() {
  for (i = 0; i < elements.length; i++) {
    elements[i].style.msFlex = "50%";  // IE10
    elements[i].style.flex = "50%";
  }
}

// Four images side by side
function four() {
  for (i = 0; i < elements.length; i++) {
    elements[i].style.msFlex = "25%";  // IE10
    elements[i].style.flex = "25%";
  }
}

// Add active class to the current button (highlight it)
var header = document.getElementById("myHeader");
var btns = header.getElementsByClassName("btn");
for (var i = 0; i < btns.length; i++) {
  btns[i].addEventListener("click", function() {
    var current = document.getElementsByClassName("active");
    current[0].className = current[0].className.replace(" active", "");
    this.className += " active";
  });
}
</script>

</body>
</html>


