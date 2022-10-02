var run = document.getElementById('run'),
    output = document.getElementById('output'),
    header = document.getElementById('header'),
    downhill1 = document.getElementById('downhill'),
    flat1 = document.getElementById('flat'),
    climb1 = document.getElementById('climb'),
    custom1 = document.getElementById('custom'),
    lineinput = document.getElementById('lineinput'),
    shadeinput = document.getElementById('shadeinput'),
    canvas = document.getElementsByTagName('canvas')[0],
    minX = document.getElementById('minX'),
    maxX = document.getElementById('maxX'),
    minY = document.getElementById('minY'),
    maxY = document.getElementById('maxY'),
    h2 = document.getElementById('h2'),
    link = document.getElementById('link'),
    physic = '',
    scenery = '',
    powerups = '',
    cXX = canvas.getContext('2d'),
    sXX = canvas.width = canvas.height = 600,
    mXX = sXX/2,
    copyenable = false,
    boldmode = false,
    downhill,climb,flat,custom,
    x1 = 40,
    y1 = 50,
    xA = [],
    yA = [];
background();
dhXX();
setTimeout(function() {
  background();
},100);
output.innerHTML = physic.slice(0,-1) + "#" + scenery.slice(0,-1) + "#" + powerups.slice(0,-1);
run.addEventListener('click',execXX);
function execXX() {
  physic = '';
  scenery = '';
  powerups = '';
  copyenable = true;
  xA = [];
  yA = [];
  x1 = 40;
  y1 = 50;
  background();
  lines(parseInt(lineinput.value));
  goal();
  checkpoint();
  document.getElementById('copycode').addEventListener('click',copy);
  output.innerHTML = physic.slice(0,-1) + "#" + scenery.slice(0,-1) + "#" + powerups.slice(0,-1);
}
function background() {
  var img = new Image();
      img.src = 'https://www.freeriderhd.com/u/copyrighted';
  cXX.beginPath();
  cXX.clearRect(0,0,sXX,sXX);
  cXX.drawImage(img,mXX-35,mXX-19);
}
function lines(n) {
  var i;
  for (i = 2; i < n;i++) {
    if (downhill === true) {
     line(10,100,10,100);
    } else if (climb === true) {
      line(40,100,-10,-100);
    } else if (custom === true) {
      line(parseInt(minX.value),parseInt(maxX.value),0-parseInt(minY.value),0-parseInt(maxY.value));
    }
  }
  if (flat === true) {
    for(i = 2;i < n*2;i++) {
      line(10,50,-30,30);
    }
  }
}
function encode(str) {
  return parseInt(str,10).toString(32);
}
function line(minx,maxx,miny,maxy) {
  var x2 = rand(minx+x1,maxx+x1),
      y2 = rand(miny+y1,maxy+y1),
      shade = parseInt(shadeinput.value);
  xA.push(x2);
  yA.push(y2);
  physic += encode(x1) + " " + encode(y1) + " " + encode(x2) + " " + encode(y2) + ",";
  if ((shade <= 0) === false) {
  for(var i = 0; i <= shade;i++) {
    if(boldmode === false) {
      scenery += encode(x1) + " " + encode(y1+i) + " " + encode(x2) + " " + encode(y2+i) + ",";
    } else {
      physic += encode(x1) + " " + encode(y1+i) + " " + encode(x2) + " " + encode(y2+i) + ",";
    }
    }
    cXX.beginPath();
    if(boldmode === false) {
      cXX.fillStyle = 'gray';
    } else {
      cXX.fillStyle = 'black';
    }
    cXX.lineWidth = 3;
    cXX.moveTo(x1+mXX,y1+mXX);
    cXX.lineTo(x1+mXX,y1+shade+mXX);
    cXX.lineTo(x2+mXX,y2+shade+mXX);
    cXX.lineTo(x2+mXX,y2+mXX);
    cXX.closePath();
    cXX.fill();
  }
  cXX.beginPath();
  cXX.strokeStyle = 'black';
  cXX.lineWidth = 3;
  cXX.moveTo(x1+mXX,y1+mXX);
  cXX.lineTo(x2+mXX,y2+mXX);
  cXX.stroke();
  x1 = x2;
  y1 = y2;
}
function goal() {
  var shade = parseInt(shadeinput.value),
      x = 120,
      y = -50,
      d = 2;
  powerups += "T " + encode(x1+120) + " " + encode(y1-50) + ",";
  cXX.beginPath();
  cXX.fillStyle = 'yellow';
  cXX.strokeStyle = 'black';
  cXX.moveTo(x1+x+mXX,y1+y-(d*4)+mXX);
  cXX.lineTo(x1+x+(d*2)+mXX,y1+y+mXX);
  cXX.lineTo(x1+x+(d*6)+mXX,y1+y+mXX);
  cXX.lineTo(x1+x+(d*3)+mXX,y1+y+(d*3)+mXX);
  cXX.lineTo(x1+x+(d*4)+mXX,y1+y+(d*7)+mXX);
  cXX.lineTo(x1+x+mXX,y1+y+(d*5)+mXX);
  cXX.lineTo(x1+x-(d*4)+mXX,y1+y+(d*7)+mXX);
  cXX.lineTo(x1+x-(d*3)+mXX,y1+y+(d*3)+mXX);
  cXX.lineTo(x1+x-(d*6)+mXX,y1+y+mXX);
  cXX.lineTo(x1+x-(d*2)+mXX,y1+y+mXX);
  cXX.lineTo(x1+x+mXX,y1+y-(d*4)+mXX);
  cXX.closePath();
  cXX.fill();
  cXX.stroke();
  physic += encode(x1) + " " + encode(y1) + " " + encode(x1+120) + " " + encode(y1) + ",";
  physic += encode(-40) + " " + encode(50) + " " + encode(40) + " " + encode(50) + ",";
  if (shade !== 0) {
  for(var i = 0; i <= shade;i++) {
    if(boldmode === false) {
  scenery += encode(x1) + " " + encode(y1+i) + " " + encode(x1+120) + " " + encode(y1+i) + ",";
  scenery += encode(-40) + " " + encode(50+i) + " " + encode(40) + " " + encode(50+i) + ",";
    } else {
  physic += encode(x1) + " " + encode(y1+i) + " " + encode(x1+120) + " " + encode(y1+i) + ",";
  physic += encode(-40) + " " + encode(50+i) + " " + encode(40) + " " + encode(50+i) + ",";
    }
    }
    cXX.beginPath();
    if(boldmode === false) {
    cXX.fillStyle = 'gray';
    } else {
      cXX.fillStyle = 'black';
    }
    cXX.fillRect(-40+mXX,50+mXX,80,shade);
    cXX.fillRect(x1+mXX,y1+mXX,120,shade);
  }
  cXX.beginPath();
  cXX.strokeStyle = 'black';
  cXX.moveTo(-40+mXX,50+mXX);
  cXX.lineTo(40+mXX,50+mXX);
  cXX.moveTo(x1+mXX,y1+mXX);
  cXX.lineTo(x1+120+mXX,y1+mXX);
  cXX.stroke();
}
function checkpoint() {
  var length,v = 20;
  if (flat === true) {
    length = parseInt(lineinput.value)*2;
  } else {
    length = parseInt(lineinput.value);
  }
  if (length > v) {
  for(var i = v;i < length;i += v) {
  powerups += "C " + encode(xA[i]+9) + " " + encode(yA[i]-11) + ",";
  cXX.beginPath();
  cXX.strokeStyle = 'black';
  cXX.fillStyle = 'rgb(100,0,200)';
  cXX.moveTo(xA[i]+mXX,yA[i]-25+mXX);
  cXX.lineTo(xA[i]+mXX,yA[i]+mXX);
  cXX.rect(xA[i]+mXX,yA[i]-25+mXX,15,12);
  cXX.fill();
  cXX.stroke();
  }
  }
}
function rand(min,max) {
  max = Math.floor(max)+1;
  min = Math.ceil(min);
  return Math.floor(Math.random()*(max-min))+min;
}
function copy() {
  output.select();
  document.execCommand('copy');
  if (document.queryCommandEnabled("copy") === true || document.queryCommandSupported("copy") === true) {
    output.innerHTML = 'Code copied.';
  } else {
    output.innerHTML = 'Code failed to copy.';
  }
  document.getElementById('copycode').removeEventListener('click',copy);
  copyenable = false;
  setTimeout(function() {
    output.innerHTML = physic.slice(0,-1) + "#" + scenery.slice(0,-1) + "#" + powerups.slice(0,-1);
    document.getElementById('copycode').addEventListener('click',copy);
    copyenable = true;
  },500);
}
output.addEventListener('click',function() {
  output.select();
});
window.addEventListener('keydown',function(e) {
  var key = e.keyCode || e.which;
  if (key == 13) {
    execXX();
  }
  if (key == 67) {
    if (copyenable === true) {
     copy();
    }
  }
});
downhill1.addEventListener('click',dhXX); 
function dhXX() {
  downhill = true;
  climb = false;
  flat = false;
  downhill1.style.backgroundColor = 'rgb(100,100,100)';
  climb1.style.backgroundColor = 'rgb(200,200,200)';
  flat1.style.backgroundColor = 'rgb(200,200,200)';
  downhill1.style.cursor = 'default';
  climb1.style.cursor = 'pointer';
  flat1.style.cursor = 'pointer';
  custom = false;
  custom1.style.backgroundColor = 'rgb(200,200,200)';
  custom1.style.cursor = 'pointer';
  minX.style.display = 'none';
  maxX.style.display = 'none';
  minY.style.display = 'none';
  maxY.style.display = 'none';
}
climb1.addEventListener('click',climbXX);
function climbXX() {
  climb = true;
  downhill = false;
  flat = false;
  climb1.style.backgroundColor = 'rgb(100,100,100)';
  downhill1.style.backgroundColor = 'rgb(200,200,200)';
  flat1.style.backgroundColor = 'rgb(200,200,200)';
  climb1.style.cursor = 'default';
  downhill1.style.cursor = 'pointer';
  flat1.style.cursor = 'pointer';
  custom = false;
  custom1.style.backgroundColor = 'rgb(200,200,200)';
  custom1.style.cursor = 'pointer';
  minX.style.display = 'none';
  maxX.style.display = 'none';
  minY.style.display = 'none';
  maxY.style.display = 'none';
}
flat1.addEventListener('click',flatXX);
function flatXX() {
  flat = true;
  downhill = false;
  climb = false;
  flat1.style.backgroundColor = 'rgb(100,100,100)';
  downhill1.style.backgroundColor = 'rgb(200,200,200)';
  climb1.style.backgroundColor = 'rgb(200,200,200)';
  flat1.style.cursor = 'default';
  downhill1.style.cursor = 'pointer';
  climb1.style.cursor = 'pointer';
  custom = false;
  custom1.style.backgroundColor = 'rgb(200,200,200)';
  custom1.style.cursor = 'pointer';
  minX.style.display = 'none';
  maxX.style.display = 'none';
  minY.style.display = 'none';
  maxY.style.display = 'none';
}
custom1.addEventListener('click',customXX);
function customXX() {
  flat = false;
  downhill = false;
  climb = false;
  flat1.style.backgroundColor = 'rgb(200,200,200)';
  downhill1.style.backgroundColor = 'rgb(200,200,200)';
  climb1.style.backgroundColor = 'rgb(200,200,200)';
  flat1.style.cursor = 'pointer';
  downhill1.style.cursor = 'pointer';
  climb1.style.cursor = 'pointer';
  custom = true;
  custom1.style.backgroundColor = 'rgb(100,100,100)';
  custom1.style.cursor = 'default';
  minX.style.display = 'inline-block';
  maxX.style.display = 'inline-block';
  minY.style.display = 'inline-block';
  maxY.style.display = 'inline-block';
}
lineinput.addEventListener('input',function() {
  if(lineinput.value > 10000) {
    lineinput.value = 10000;
  }
  if(Math.sign(lineinput.value) == -1) {
    lineinput.value = Math.abs(lineinput.value);
  }
});
lineinput.addEventListener('focusout',function() {
  if(lineinput.value < 10) {
    lineinput.value = 10;
  }
});
shadeinput.addEventListener('input',function() {
  if(shadeinput.value > 1000) {
    shadeinput.value = 1000;
  }
  if(Math.sign(shadeinput.value) == -1) {
    shadeinput.value = Math.abs(shadeinput.value);
  }
});
shadeinput.addEventListener('focusout',function() {
  if(shadeinput.value === '') {
    shadeinput.value = 0;
  }
});
minX.addEventListener('input',function() {
  if(minX.value > 200) {
    minX.value = 200;
  }
  if(Math.sign(minX.value) == -1) {
    minX.value = Math.abs(minX.value);
  }
});
minX.addEventListener('focusout',function() {
  if(minX.value === '') {
    minX.value = 0;
  }
});
maxX.addEventListener('input',function() {
  if(maxX.value > 200) {
    maxX.value = 200;
  }
  if(Math.sign(maxX.value) == -1) {
    maxX.value = Math.abs(maxX.value);
  }
});
maxX.addEventListener('focusout',function() {
  if(maxX.value === '' || maxX.value < 10) {
    maxX.value = 10;
  }
});
minY.addEventListener('input',function() {
  if(minY.value > 200) {
    minY.value = 200;
  }
  if(minY.value < -200) {
    minY.value = -200;
  }
});
minY.addEventListener('focusout',function() {
  if(minY.value === '') {
    minY.value = 0;
  }
});
maxY.addEventListener('input',function() {
  if(maxY.value > 200) {
    maxY.value = 200;
  }
  if(maxY.value < -200) {
    maxY.value = -200;
  }
});
maxY.addEventListener('focusout',function() {
  if(maxY.value === '') {
    maxY.value = 0;
  }
});
lineinput.addEventListener('dblclick',function() {
  lineinput.select();
});
shadeinput.addEventListener('dblclick',function() {
  shadeinput.select();
});
minX.addEventListener('dblclick',function() {
  minX.select();
});
maxX.addEventListener('dblclick',function() {
  maxX.select();
});
minY.addEventListener('dblclick',function() {
  minY.select();
});
maxY.addEventListener('dblclick',function() {
  maxY.select();
});
lineinput.addEventListener('mouseover',function() {
  h2.innerHTML = 'Number of Lines';
});
shadeinput.addEventListener('mouseover',function() {
  if(boldmode === false) {
  h2.innerHTML = 'Shading Width';
  } else {
    h2.innerHTML = 'Bold Line Width';
  }
});
minX.addEventListener('mouseover',function() {
  h2.innerHTML = 'Minimum Horizontal Length';
});
maxX.addEventListener('mouseover',function() {
  h2.innerHTML = 'Maximum Horizontal Length';
});
minY.addEventListener('mouseover',function() {
  h2.innerHTML = 'Minimum Vertical Length';
});
maxY.addEventListener('mouseover',function() {
  h2.innerHTML = 'Maximum Vertical Length';
});
h1.addEventListener('mouseover',function() {
  if(boldmode === false) {
  h2.innerHTML = 'Click to activate Bold Mode';
  } else {
    h2.innerHTML = 'Click to deactivate Bold Mode';
  }
});
lineinput.addEventListener('mouseout',h2def);
shadeinput.addEventListener('mouseout',h2def);
minX.addEventListener('mouseout',h2def);
maxX.addEventListener('mouseout',h2def);
minY.addEventListener('mouseout',h2def);
maxY.addEventListener('mouseout',h2def);
h1.addEventListener('mouseout',h2def);
function h2def() {
  h2.innerHTML = 'Created by <span id=link>Johnny</span>';
  link = document.getElementById('link');
  linkenable();
}
linkenable();
function linkenable() {
  link.addEventListener('click',function() {
    window.open('https://www.freeriderhd.com/u/neutralized/created');
  });
}
h1.addEventListener('click',boldmode1XXX);
function boldmode1XXX() {
  boldmode = true;
  h1.removeEventListener('click',boldmode1XXX);
  h1.addEventListener('click',boldmode2XXX);
  h2.innerHTML = 'Bold Mode : On';
  setTimeout(h2def,500);
}
function boldmode2XXX() {
  boldmode = false;
  h1.removeEventListener('click',boldmode2XXX);
  h1.addEventListener('click',boldmode1XXX);
  h2.innerHTML = 'Bold Mode : Off';
  setTimeout(h2def,500);
}

