# February 14th 

## *Assignment 3* ##

### * DOCUMENTATION * ###

Link to project [https://editor.p5js.org/hindahhmed/sketches/54RSwA2Ko]
 
The assignment assigned asked for a art work to be created. I was inspired by the Valentine's day holiday to create something which included hearts to fit the theme of the holiday. I initially started off my creating the background color, I decided to go with a soft but bright pink, using RGB, with the colors being (245, 186, 232). 

I drew inspiration from the code craeted in the previous class, Link [https://editor.p5js.org/itp42/sketches/aDRvuABPM], but implimented many changes to fit the image I had in mind. The amount of hearts showcased are 64 and the size of the hearts is 40. The speed of the hearts is 2, because I felt as though anything more would be too fast. Moreover, the color shifts as the mouse moves across the canvas. I did this by utilizing mouseX. 

Code: 
let hearts = [];
let noHearts = 64;
let size = 40;

function setup() {
  createCanvas(400, 400);
 
  for(let i =0; i<noHearts;i++) {
    let xPos = random(0,width);
    let yPos = random(0,height);
    hearts[i] = new Heart(xPos, yPos);
  }
  
}

function draw() {
  background(245, 186, 232);
  

  for(let i =0; i<noHearts;i++) {
    hearts[i].drawHearts();
    hearts[i].moveHearts();
  }
}



class Heart {
  //attributes
  constructor(xPos, yPos) {
    this.x = xPos;
    this.y = yPos;
    this.speed = 2;
  }
  
  //methods or functions
  drawHearts() {
    strokeWeight(1.5)
  fill(224*mouseX/width, 117, 165);
  beginShape();
  vertex(this.x, this.y);
  bezierVertex(this.x - size / 2, this.y - size / 2, this.x - size, this.y + size / 3, this.x, this.y + size );
  bezierVertex(this.x + size, this.y + size / 3, this.x + size/ 2, this.y - size / 2, this.x, this.y );
  endShape(CLOSE);
 
  }
  
  moveHearts() {
    this.x = this.x +this.speed;
    if(this.x > width) {
      this.x = -40;
    }
  }
  
}

