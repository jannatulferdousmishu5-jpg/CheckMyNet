<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CheckMyNet - IP & Speed Tool</title>

<style>
body {
  font-family: Arial, sans-serif;
  text-align: center;
  background: linear-gradient(to right, #007bff, #00c6ff);
  color: white;
  padding: 20px;
}

h1 {
  margin-bottom: 5px;
}

.container {
  max-width: 400px;
  margin: auto;
}

.box {
  background: white;
  color: black;
  padding: 20px;
  margin: 15px 0;
  border-radius: 12px;
  box-shadow: 0 5px 15px rgba(0,0,0,0.2);
}

.value {
  font-size: 18px;
  margin-top: 10px;
  color: green;
  word-wrap: break-word;
}

button {
  padding: 10px 15px;
  border: none;
  background: #007bff;
  color: white;
  border-radius: 5px;
  cursor: pointer;
  margin-top: 10px;
}

button:hover {
  background: #0056b3;
}
</style>
</head>

<body>

<h1>🌐 CheckMyNet</h1>
<p>Check Your IP, Speed & Network Info Instantly</p>

<div class="container">

<div class="box">
  <h3>Your IP Address</h3>
  <div id="ip" class="value">Loading...</div>
  <button onclick="copyIP()">Copy IP</button>
</div>

<div class="box">
  <h3>IP Location</h3>
  <div id="location" class="value">Loading...</div>
</div>

<div class="box">
  <h3>Browser Info</h3>
  <div id="browser" class="value"></div>
</div>

<div class="box">
  <h3>Internet Speed</h3>
  <button onclick="checkSpeed()">Check Speed</button>
  <div id="speed" class="value"></div>
</div>

</div>

<script>
// Fetch IP + Location
fetch("https://ipapi.co/json/")
.then(res => res.json())
.then(data => {
  document.getElementById("ip").innerText = data.ip;
  document.getElementById("location").innerText =
    data.city + ", " + data.country_name;
});

// Browser Info
document.getElementById("browser").innerText = navigator.userAgent;

// Copy IP
function copyIP() {
  const ip = document.getElementById("ip").innerText;
  navigator.clipboard.writeText(ip);
  alert("IP Copied: " + ip);
}

// Speed Test
function checkSpeed() {
  let start = new Date().getTime();
  let img = new Image();

  img.src = "https://via.placeholder.com/2000x2000?" + Math.random();

  img.onload = function () {
    let end = new Date().getTime();
    let duration = (end - start) / 1000;
    let speed = (2000 / duration).toFixed(2);
    document.getElementById("speed").innerText =
      speed + " Mbps (approx)";
  };
}
</script>

</body>
</html># CheckMyNet
CheckMyNet is a free online tool to check your IP address, internet speed, location, and browser information instantly.”
