<html>
<head>
  <title>MOTION DETECTOR</title>
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
  <script src="soundmanager2.js"></script>
  <script>
        
  
let a =0;
    let rising = 1;
    let k = 0;
   
  function player (freq) {
  audioCtx = new(window.AudioContext || window.webkitAudioContext)();
            
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
    
loadfiles();
   
// where to find flash SWFs, if needed...
    //soundManager.url = '';
    
    function loadfiles(){

    soundManager.onready(function() {
        soundManager.createSound({
            id: 'mySound1',
            url: 'croq1.wav'
        });
        
        soundManager.createSound({
            id: 'mySound2',
            url: 'croq2.wav'
        });
        
        soundManager.createSound({
            id: 'mySound3',
            url: 'croq3.wav'
        });
        
        soundManager.createSound({
            id: 'mySound4',
            url: 'croq4.wav'
        });
        
        soundManager.createSound({
            id: 'mySound5',
            url: 'croq5.wav'
        });
        });
    }
    function playfile(){
        // ...and play it
        k++;
        soundManager.play('mySound'+k);
        if(k==5){k=0;}
    }
    
    show();
        
  function show() {
  
  let sensor = new Accelerometer();
sensor.start();

  	sensor.onreading = () => {
  	
  	a= (Math.sqrt((sensor.x * sensor.x) + (sensor.y * sensor.y) + (sensor.z * sensor.z)));
  	
  	if (a>10 && rising){ document.getElementById("t4").innerHTML = 'BoOM = '+ a + 'm.s-2'; rising = 0; playfile(); }
    if (a<10){rising = 1;}
}

        

sensor.onerror = event => console.log(event.error.name, event.error.message);
}
       
        
    </script>

</head>



<body>
  <button onclick="player(600);">START</button>
  <button onclick="playfile();">file</button>
  <p id="t4"></p>
</body>
</html>
