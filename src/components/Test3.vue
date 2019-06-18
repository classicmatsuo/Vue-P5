<template>
  <div>
    
  </div>
</template>
<script>
var s = function( sketch ) {
  var freqSlider, freqLabel, ampLabel, ampSlider, button;
  var osc;
  var freq = 220;
  var amp = 0.2;

  var oscOn = false;

  sketch.setup = function() {

    // sketch.createCanvas(710, 400);
    // sketch.strokeWeight(10);
    // sketch.stroke(255, 100);

    sketch.createCanvas(710, 400, sketch.WEBGL);

    freqLabel = sketch.createP('Frequency: ');
    freqSlider = sketch.createSlider(1, 700, freq);

    ampLabel = sketch.createP('Amplitude: ' + amp);
    ampSlider = sketch.createSlider(0.0, 100.0, amp*100);

    button = sketch.createButton('start');
    button.mousePressed(sketch.toggleOsc);

    // Instantiate a Sine Wave Oscillator
    this.osc = new p5.SinOsc();
    this.osc.amp(amp);
    
  };

  sketch.draw = function() {

    sketch.background(250);

    sketch.rotateY(sketch.frameCount * (freq * 0.0001));

    // let locX = sketch.mouseX - sketch.height / 2;
    // let locY = sketch.mouseY - sketch.swidth / 2;

    // sketch.ambientLight(60, 60, 60);
    // sketch.pointLight(255, 255, 255, locX, locY, 100);
    sketch.ambientLight(200);
    sketch.directionalLight(200, 150, 150, 0.25, 0.25, 0);

    for (let j = 0; j < 5; j++) {
      sketch.push();
      for (let i = 0; i < (15 +(freq / 20)); i++) {
        sketch.translate(
          sketch.sin(sketch.frameCount * 0.001 + j) * 100,
          sketch.sin(sketch.frameCount * 0.001 + j) * 100,
          i * 0.25
        );
        sketch.rotateZ(sketch.frameCount * 0.002);
        sketch.push();
        // sketch.noStroke();
        // sketch.fill(66, 244, 244);
        sketch.normalMaterial();
        // sketch.sphere(5 + (amp * 10), 7, 6);
        // sketch.specularMaterial(250);
        sketch.torus(10 + (amp * 10), 5 + (amp * 4));
        sketch.pop();
      }
      sketch.pop();
    }
  
    // set frequency of the between 40 and 880 Hz
    freq = freqSlider.value();
    sketch.osc.freq(freq);
    freqLabel.html('Frequency: ' + freq + ' Hz');

    amp = ampSlider.value()/100;
    sketch.osc.amp(amp);
    ampLabel.html('Amplitude: ' + amp + '/ 1.0');
  };
  // Turn the oscillator on / off
  sketch.toggleOsc = function() {
    if (oscOn) {
      sketch.osc.stop();
      button.html('start');
    } else {
      sketch.osc.start();
      button.html('stop');
    }
    oscOn = !oscOn;
  }
}
new p5(s)
</script>