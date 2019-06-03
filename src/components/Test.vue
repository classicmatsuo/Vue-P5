
<script>
import p5 from 'p5'
import {pulse} from 'p5'


var s = function( sketch ) {
  // Example: Oscillator Frequency

  // var osc;
  var pulse = null;

  sketch.setup = function() {
    sketch.background(0);

    // Create and start the pulse wave oscillator
    sketch.pulse = new p5.Pulse();
    sketch.pulse.amp(0.5);
    sketch.pulse.freq(220);
    sketch.pulse.start();
  }

  sketch.draw = function() {
    var w = sketch.map(sketch.mouseX, 0, sketch.width, 0, 1);
    w = sketch.constrain(w, 0, 1);
    pulse.width(w)
  }

  sketch.touchStarted = function() {
    sketch.getAudioContext().resume()
  }
  // var osc;
  // var playing;

  // sketch.setup = function() {
  //   sketch.backgroundColor = sketch.color(255,0,255);
  //   sketch.textAlign(sketch.CENTER);

  //   osc = new p5.Oscillator();
  //   osc.setType('sine');
  //   osc.freq(240);
  //   osc.amp(0);
  //   osc.start();
  // }

  // sketch.draw = function() {
  //   sketch.background(sketch.backgroundColor)
  //   sketch.text('click to play', sketch.width/2, sketch.height/2);
  // }

  // sketch.mouseClicked = function() {
  //   if (sketch.mouseX > 0 && sketch.mouseX < sketch.width && sketch.mouseY < sketch.height && sketch.mouseY > 0) {
  //     if (!playing) {
  //       // ramp amplitude to 0.5 over 0.05 seconds
  //       osc.amp(0.5, 0.05);
  //       sketch.playing = true;
  //       sketch.backgroundColor = sketch.color(0,255,255);
  //     } else {
  //       // ramp amplitude to 0 over 0.5 seconds
  //       osc.amp(0, 0.5);
  //       sketch.playing = false;
  //       sketch.backgroundColor = sketch.color(255,0,255);
  //     }
  //   }
  // }
}

new p5(s);

</script>