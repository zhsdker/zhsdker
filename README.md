<SCRIPT LANGUAGE="JavaScript1.2">
<!--
var no = 15; // количество снежинок
var speed = 1; // скорость снежинок
var snowflake = "sneg.gif";

var ns4up = (document.layers) ? 1 : 0;
var ie4up = (document.all) ? 1 : 0;
var dx, xp, yp;
var am, stx, sty;
var i, doc_width = 800, doc_height = 600;
if (ns4up) {
doc_width = self.innerWidth;
doc_height = self.innerHeight;
} else if (ie4up) {
doc_width = document.body.clientWidth;
doc_height = document.body.clientHeight;
}
dx = new Array();
xp = new Array();
yp = new Array();
am = new Array();
stx = new Array();
sty = new Array();
for (i = 0; i < no; ++ i) {
dx[i] = 0;
xp[i] = Math.random()*(doc_width-50);
yp[i] = Math.random()*doc_height;
am[i] = Math.random()*20;
stx[i] = 0.02 + Math.random()/10;
sty[i] = 0.7 + Math.random();
if (ns4up) document.write("<layer name=\"dot"+ i +"\" left=\"15\" top=\"15\" visibility=\"show\"><img src=\""+snowflake+"\" border=\"0\" alt=\"Снежинка\"></layer>");
else if (ie4up) document.write("<div id=\"dot"+ i +"\" style=\"position:absolute; z-index: "+ i +"; visibility:visible; top: 15px; left: 15px;\"><img src=\""+snowflake+"\" border=\"0\" alt=\"Снежинка\"></div>");
}
function snowNS() {
for (i = 0; i < no; ++ i) {
yp[i] += sty[i];
if (yp[i] > doc_height-50) {
xp[i] = Math.random()*(doc_width-am[i]-30);
yp[i] = 0;
stx[i] = 0.02 + Math.random()/10;
sty[i] = 0.7 + Math.random();
doc_width = self.innerWidth;
doc_height = self.innerHeight;
}
dx[i] += stx[i];
document.layers["dot"+i].top = yp[i];
document.layers["dot"+i].left = xp[i] + am[i]*Math.sin(dx[i]);
}
setTimeout("snowNS()", speed);
}
function snowIE() {
for (i = 0; i < no; ++ i) {
yp[i] += sty[i];
if (yp[i] > doc_height-50) {
xp[i] = Math.random()*(doc_width-am[i]-30);
yp[i] = 0;
stx[i] = 0.02 + Math.random()/10;
sty[i] = 0.7 + Math.random();
doc_width = document.body.clientWidth;
doc_height = document.body.clientHeight;
}
dx[i] += stx[i];
document.all["dot"+i].style.pixelTop = yp[i];
document.all["dot"+i].style.pixelLeft = xp[i] + am[i]*Math.sin(dx[i]);
}
setTimeout("snowIE()", speed);
}
if (ns4up) snowNS();
else if (ie4up) snowIE();
for(i=0;i<24;i++)document.write("Снег на странице<br>");
// -->
</script>
