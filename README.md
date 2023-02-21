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
        
 

show();
        
  function show() {
  
  let sensor = new Accelerometer();
sensor.start();

  	sensor.onreading = () => {
    console.log("Acceleration along X-axis: " + sensor.x);
    console.log("Acceleration along Y-axis: " + sensor.y);
    console.log("Acceleration along Z-axis: " + sensor.z);

        document.getElementById("t1").innerHTML = 'ax = '+ sensor.x + 'm.s-2';
        document.getElementById("t2").innerHTML = 'ay = '+ sensor.y + 'm.s-2';
        document.getElementById("t3").innerHTML = 'az = '+ sensor.z + 'm.s-2';
}
sensor.onerror = event => console.log(event.error.name, event.error.message);
}
       
        
    </script>
</body>
</html>
