<html>
<head>
  <title>MOTION DETECTOR</title>
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
</head>

<body>

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
  	
  	let a = sqrt(sensor.x^2+sensor.y^2+sensor.z^2);

        document.getElementById("t1").innerHTML = 'ax = '+ sensor.x + 'm.s-2';
        document.getElementById("t2").innerHTML = 'ay = '+ sensor.y + 'm.s-2';
        document.getElementById("t3").innerHTML = 'az = '+ sensor.z + 'm.s-2';
        document.getElementById("t4").innerHTML = 'a = '+ a + 'm.s-2';
}
sensor.onerror = event => console.log(event.error.name, event.error.message);
}
       
        
    </script>
</body>
</html>
