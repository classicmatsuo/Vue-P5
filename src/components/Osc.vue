<template>
  <div id="osc"></div>
</template>

<script>
import p5 from 'p5'


var s = function( sketch ) {

  sketch.setup = function() {
    sketch.createCanvas(710, 400);
    sketch.strokeWeight(20.0);
    sketch.stroke(255, 100);

    sketch.createCanvas(710, 400, sketch.WEBGL);
  };

  sketch.draw = function() {
    sketch.background(250);
    sketch.rotateY(sketch.frameCount * 0.01);

    for (let j = 0; j < 5; j++) {
      sketch.push();
      for (let i = 0; i < 80; i++) {
        sketch.translate(
          sketch.sin(sketch.frameCount * 0.001 + j) * 100,
          sketch.sin(sketch.frameCount * 0.001 + j) * 100,
          i * 0.1
        );
        sketch.rotateZ(sketch.frameCount * 0.002);
        sketch.push();
        sketch.sphere(8, 6, 4);
        sketch.pop();
      }
      sketch.pop();
    }
  }
};

new p5(s);

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
