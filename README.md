<!DOCTYPE html>

<html>
<head>
  <title>MOTION DETECTOR</title>
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
</head>

<body>

  <p id="t1"></p>
  <p id="t2"></p>
  <p id="t3"></p>
  <script>
        
 
let sensor = new Accelerometer();
sensor.start();

show();
        
  function show() {
  	sensor.onreading = () => {
    console.log("Acceleration along X-axis: " + sensor.x);
    console.log("Acceleration along Y-axis: " + sensor.y);
    console.log("Acceleration along Z-axis: " + sensor.z);
}

sensor.onerror = event => console.log(event.error.name, event.error.message);
        document.getElementById("t1").innerHTML = 'x = '+ sensor.x + ' m.s-2';
        document.getElementById("t2").innerHTML = 'y = '+ sensor.y + ' m.s-2';
        document.getElementById("t3").innerHTML = 'z = '+ sensor.z + ' m.s-2';
}
       
        
    </script>
</body>
</html>
