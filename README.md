<html>
<head>
  <title>MOTION DETECTOR</title>
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
</head>

<body>

  <p id="t4"></p>
  <script>
        
    audioCtx = new(window.AudioContext || window.webkitAudioContext)();
let a =0;
    let rising = 1;
   
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
  	
  	a= (Math.sqrt((sensor.x * sensor.x) + (sensor.y * sensor.y) + (sensor.z * sensor.z)));
  	
  	if (a>10 && rising){ document.getElementById("t4").innerHTML = 'BoOM = '+ a + 'm.s-2'; rising = 0; player (800); }
    if (a<10){rising = 1;}
}

        

sensor.onerror = event => console.log(event.error.name, event.error.message);
}
       
        
    </script>
</body>
</html>
