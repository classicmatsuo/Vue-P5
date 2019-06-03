<template>
  <div>
    
  </div>
</template>
<script>

export default {
  data: function () {
    return {
      script: null,
      // ps: null,
      // canvas: null,
      // pulse: null,
      osc: null
    }
  },
  mounted() {
    this.script = p => {
      p.setup = () => {

        // p.background(0);

        // Create and start the pulse wave oscillator
        // this.pulse = new p5.Pulse();
        // this.pulse.amp(0.2);
        // this.pulse.freq(50);
        // this.pulse.start();

        // var osc = new p5.Oscillator(300);
        // osc.start();
        // osc.freq(40, 10);

        p.createCanvas(710, 400);
        p.strokeWeight(10);
        p.stroke(255, 100);

        p.createCanvas(710, 400, p.WEBGL);

        // from examples/learningProcessingExamples/06_oscillator_frequency/
        // p.createCanvas(720, 200);

        // Instantiate a Sine Wave Oscillator
        this.osc = new p5.SinOsc();

        // Tell the Oscillator to start oscillating.
        // We hear the frequency of these oscillators as a pitch.
        this.osc.start();

        // Oscillator has an output amplitude of 0.5 by default.
        // We can make it louder.
        this.osc.amp(1);
      }

      p.draw = () => {
        // var w = p.map(p.mouseX, 0, p.width, 0, 1);
        // w = p.constrain(w, 0, 1);
        // this.pulse.width(w)
        p.background(250);
        p.rotateY(p.frameCount * (p.mouseX * 0.0001));

        for (let j = 0; j < 5; j++) {
          p.push();
          for (let i = 0; i < 10; i++) {
            p.translate(
              p.sin(p.frameCount * 0.001 + j) * 200,
              p.sin(p.frameCount * 0.001 + j) * 100,
              i * 0.25
            );
            p.rotateZ(p.frameCount * 0.002);
            p.push();
            p.sphere(5 + (p.mouseX / 100), 8, 6);
            p.pop();
          }
          p.pop();
        }
  
        // map the mouseX to set frequency of the between 40 and 880 Hz
        var freq = p.map(p.mouseX, 0, p.width, 20, 100);
        this.osc.freq(freq);
        // p.ellipse(p.mouseX, 100, 32, 32);
        // p.sphere(p.mouseX, 8, 6);
      }

    }
    const P5 = require('p5')
    this.ps = new P5(this.script)
    // console.log(this.ps)
  }
}
</script>