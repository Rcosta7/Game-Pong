//variáveis da bolinha
let xBolinha = 300;
let yBolinha = 200;
let diametro = 14;
let raio = diametro / 2;
let chanceDeErrar = 0;

//velocidade da bolinha
let velocidadeXBolinha = 6 ;
let velocidadeYBolinha = 6;

// variavéis da raquete
let xRaquete = 5;
let yRaquete = 150;
let raqueteComprimento = 10;
let raqueteAltura = 90;

//variaveis do oponenente
let xRaqueteoponente = 585;
let yRaqueteoponente = 150;
let raqueteComprimentooponente = 10;
let raqueteAlturaoponente = 90;
let velocidadeYOponente;

let colidiu = false;

//placar do jogo
let meuspontos=0;
let pontosdoOponente=0;

//sons do jogo
let raquetada;
let ponto;
let trilha;

function preload(){
  trilha = loadSound("trilha.mp3");
  ponto= loadSound ("ponto.mp3");
  raquetada= loadSound ("raquetada.mp3");
}

function setup() {
  createCanvas(600, 400);
  trilha.loop();
}

function draw() {
  background(0);
  mostraBolinha();
  movimentaBolinha();
  verificaColisaoBorda();
  mostraraquete(xRaquete,yRaquete);
  movimentaraquete();
  //verificacolisaoRaquete();
  colisaoraquete(xRaquete,yRaquete);
  mostraraquete(xRaqueteoponente,yRaqueteoponente);
  movimentaRaqueteoponente();
  colisaoraquete(xRaqueteoponente,yRaqueteoponente);
  incluiplacar();
  marcaPonto();
}

function mostraBolinha(){
circle(xBolinha, yBolinha, diametro);
}


function bolinhaNaoFicaPresa(){
    if (XBolinha - raio < 0){
    XBolinha = 23
    }
}

function movimentaBolinha(){
  xBolinha += velocidadeXBolinha;
  yBolinha += velocidadeYBolinha;
}

function verificaColisaoBorda(){
  if(xBolinha + raio > width ||
    xBolinha - raio < 0){
    velocidadeXBolinha *= -1;
  }
  
  if(yBolinha + raio > height ||
    yBolinha - raio < 0){
    velocidadeYBolinha *= -1;
  }
}

function mostraraquete(x,y){
  rect(x,y,raqueteComprimento,raqueteAltura);
}


function movimentaraquete(){
  if(keyIsDown(UP_ARROW)){
    yRaquete -= 10;
  }

  if(keyIsDown(DOWN_ARROW)){
    yRaquete += 10;
  }
//limita a movimentação da raquete para que ela não ultrapasse as bordas:
  yRaquete = constrain(yRaquete, 10, 310);

}

function verificacolisaoRaquete(){
  
  if(xBolinha - raio < xRaquete + raqueteComprimento && 
     yBolinha - raio < yRaquete + raqueteAltura &&
     yBolinha + raio > yRaquete ){
     velocidadeXBolinha *= -1;
     raquetada.play();
  }
}

function colisaoraquete(x,y){
  colidiu = collideRectCircle(x, y,raqueteComprimento,raqueteAltura, xBolinha, yBolinha,raio);
  
      if(colidiu) {
      velocidadeXBolinha *= -1;
      raquetada.play();

  }
}

function calculaChanceDeErrar() {
  if (pontosdoOponente >= meuspontos) {
    chanceDeErrar += 1
    if (chanceDeErrar >= 39){
    chanceDeErrar = 40
    }
  } else {
    chanceDeErrar -= 1
    if (chanceDeErrar <= 35){
    chanceDeErrar = 35
    }
  }
}

 function movimentaRaqueteoponente(){
   
  velocidadeYOponente = yBolinha -yRaqueteoponente - raqueteComprimento / 2 - 30;
  yRaqueteoponente += velocidadeYOponente + chanceDeErrar
  calculaChanceDeErrar()
     
//limita a movimentação da raquete para que ela não ultrapasse as bordas:
  yRaqueteoponente = constrain(yRaqueteoponente, 10, 310);
 }

function incluiplacar (){
  stroke(255);
  textAlign(CENTER);
  textSize(16);
  fill(color(255, 140, 0));
  rect(150, 10, 40, 20);
  fill(255);
  text(meuspontos, 170, 26);
  fill(color(255, 140, 0));
  rect(450, 10, 40, 20);
  fill(255);
  text(pontosdoOponente, 470, 26);
  
}

function marcaPonto(){
  if(xBolinha > 590){
    meuspontos +=1;
    ponto.play();
  }
  if(xBolinha <10){
    pontosdoOponente += 1;
    ponto.play();
  }
}
