<html>
<head>
  <title>MOTION DETECTOR</title>
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
</head>

<body>

  <p id="t4"></p>
  <script>
        
    audioCtx = new(window.AudioContext || window.webkitAudioContext)();

   
  function player (freq) {

            
  var osc = audioCtx.createOscillator();
  var gainNode = audioCtx.createGain();

  osc.connect(gainNode);
  gainNode.connect(audioCtx.destination);

  gainNode.gain.value = 0.1;
  osc.frequency.value = freq;
  osc.type = "sine";

  osc.start();

  setTimeout(
    function() {
      osc.stop();
    },
    2000
  );
  };

show();
        
  function show() {
  
  let sensor = new Accelerometer();
sensor.start();

  	sensor.onreading = () => {
  	
  	let a = (Math.sqrt((sensor.x * sensor.x) + (sensor.y * sensor.y) + (sensor.z * sensor.z)));
  	
  	if (a>10){ document.getElementById("t4").innerHTML = 'BOOOM = '+ a + 'm.s-2'; player (600);}

}
sensor.onerror = event => console.log(event.error.name, event.error.message);
}
       
        
    </script>
</body>
</html>
