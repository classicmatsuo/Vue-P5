<template>
  <div id="osc"></div>
</template>

<script>
import p5 from 'p5'


var s = function( sketch ) {

  // var x = 100; 
  // var y = 100;
  
  // let x = 100,
  // y = 100,
  // angle1 = 0.0,
  // segLength = 50;

  sketch.setup = function() {
    // sketch.createCanvas(200, 200);

    // sketch.createCanvas(710, 400);
    // sketch.strokeWeight(20.0);
    // sketch.stroke(255, 100);

    sketch.createCanvas(710, 400, sketch.WEBGL);
  };

  sketch.draw = function() {
    // sketch.background(0);
    // sketch.fill(255);
    // sketch.rect(x,y,50,50);

    // sketch.background(0);

    // sketch.dx = sketch.mouseX - x;
    // sketch.dy = sketch.mouseY - y;
    // angle1 = sketch.atan2(sketch.dy, sketch.dx);
    // x = sketch.mouseX - sketch.cos(angle1) * segLength;
    // y = sketch.mouseY - sketch.sin(angle1) * segLength;

    // sketch.segment(x, y, sketch.angle1);
    // sketch.ellipse(x, y, 20, 20);

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
  };

  // sketch.segment = function(x, y, a) {
  //   sketch.push();
  //   sketch.translate(x, y);
  //   sketch.rotate(a);
  //   sketch.line(0, 0, segLength, 0);
  //   sketch.pop();
  // }
};

new p5(s);

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
