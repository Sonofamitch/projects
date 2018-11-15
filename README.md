# projects

Paint splatter:

var generator = new Random(1); 
        var paintNum = 1; 
        var paint = []; 
        var colorGen = function() {
            var color1 = floor(random(222));
            var color2 = floor(random(289));
            var color3 = floor(random(192));
            if (color2 > color3) {
                if (color1 > color2) {
                    color1 = 255;
                }
                else {
                    color2 = 255;
                }
                color3 = 0;
            }
            else if (color3 > color1) {
                if (color2 > color3) {
                    color2 = 255;
                }
                else {
                    color3 = 255;
                }
                color1 = 0;
            }
            else {
                if (color1 > color3) {
                    color1 = 255;
                }
                else {
                    color3 = 255;
                }
                color2 = 0;
            }
            
            return color(color1, color2, color3);
        };
    
    
        var Splatter = function() {
            this.x = random(width); 
            this.y = random(height); 
            this.size = random(165, 66); 
            this.color = color(floor(random(256)), floor(random(256)), floor(random(256)));
        };
        
        // Draw method
        Splatter.prototype.draw = function() {
            
            var num; 
            var circleX; 
            var circleY; 
            var circleSizeMean; 
            var circleSizeStdev; 
            var circleSize; 
            
            noStroke();
            fill(colorGen());
            
         
            for (var j = 0; j < 1 * this.size * this.size; j++) {
                
              
                num = generator.nextGaussian();
                circleX = num * this.size + this.x;
                
                
                num = generator.nextGaussian();
                circleY = num * this.size + this.y;
                
                if (abs(circleX - this.x) < this.size && abs(circleY - this.y) < this.size) {
                    circleSizeMean = 10;
                    circleSizeStdev = 10;
                }
                else if (abs(circleX - this.x) < 2*this.size && abs(circleY - this.y) < 2*this.size) {
                    circleSizeMean = 10;
                    circleSizeStdev = 10;
                }
                else {
                    circleSizeMean = 16;
                    circleSizeStdev = 19;
                }
                
             
                circleSize = 10;
                
                
                ellipse(circleX, circleY, circleSize, circleSize);
            }
        };


    for (var i = 0; i < paintNum; i++) {
        paint[i] = new Splatter();
        paint[i].draw();
    }


Mountain Range:

var drawRange = function() {
    var incAmount = 0.01;
    for (var t = 0; t < incAmount*width; t += incAmount) {
        var n = noise(t);
        var y = map(n, 0, 1, 0, height/2);
        rect(t*100, height-y, 1, y);
    }
};

drawRange();


background(0, 255, 255);
var drawRange = function() {
    var incAmount = 0.01;
    stroke(0, 0, 0);
    for (var t = 0; t < incAmount*width; t += incAmount) {
        var n = noise(t);
        var y = map(n, 0, 3, 0, height/2);
        rect(t*100, height-y, 1, y);
    }
};
var drawRange2 = function() {
    stroke(46, 45, 46);
    var incAmount = 0.01;
    for (var t = 0; t < incAmount*width; t += incAmount) {
        var n = noise(t);
        var y = map(n, 0, 1, 58, height/2);
        rect(t*173, height-y, 1, y);
    }
};
var drawClouds = function(x, y){
    noStroke();
    fill(255, 255, 255);
    ellipse(x, y, 82, 60);
    ellipse(x + 30, y + 19, 43, 45);
    ellipse(x + -35, y + 18, 41, 42);
};
stroke(0, 0, 0);
drawClouds(random(50, 350), random(200, 50));
drawClouds(random(50, 350), random(200, 50));
drawClouds(random(50, 350), random(200, 50));
drawRange2();
drawRange();
