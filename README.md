<!DOCTYPE html>
<html>
<head>
  <title>MOTION DETECTOR</title>
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
</head>

<body>


<h1>TEST</h1>
  <p id="t1"></p>
  <p id="t2"></p>
  <p id="t3"></p>
  <p id="t4"></p>
  <script>
        
 

show();
        
  function show() {
  
  let sensor = new Accelerometer();
sensor.start();

    sensor.onreading = () => {
    
        document.getElementById("t1").innerHTML = 'ax = '+ sensor.x + 'm.s-2';
        document.getElementById("t2").innerHTML = 'ay = '+ sensor.y + 'm.s-2';
        document.getElementById("t3").innerHTML = 'az = '+ sensor.z + 'm.s-2';
}
sensor.onerror = event => console.log(event.error.name, event.error.message);
}
       
        
    </script>
</body>
</html>
