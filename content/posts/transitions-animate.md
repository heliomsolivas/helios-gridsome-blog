---
title: Animações simples com CSS3 Transitions + Waypoints.js
date: 2018-07-23
published: true
tags: ['CSS3','Animations', 'Waypoints.js']
cover_image: ./images/waypoints.gif
canonical_url: false
description: "Vamos falar sobre animações, quem nunca precisou fazer um fadeIn / fadeOut com algum texto/imagem, vou mostrar um maneira relativamente simples de se criar pequenas animações que são ativadas de acordo..."
---
Vamos falar sobre animações, quem nunca precisou fazer um fadeIn / fadeOut com algum texto/imagem, vou mostrar um maneira relativamente simples de se criar pequenas animações que são ativadas de acordo com os objetos que vão aparecendo na tela, com esse combo: <strong>transitions</strong> + <strong>waypoints.js</strong>. Bora pro código:

Um html simples com dois blocos, onde um texto será animado quando o usuário visualizar completamente o segundo bloco.

```html
<section class="destaque"></section>
<section class="detalhes">
    <h1>Meu texto</h1>
</section>
```

Não vou entrar em detalhes sobre o CSS, porque não tem nada de diferente por enquanto, dois blocos com 100% e estou alinhando o texto no centro do bloco detalhes.

```css
*{
  box-sizing:border-box;
}
html,body{
  height:100%;
}
section{
  height:100%;
}
.detalhes{
  background:#1abc9c;
  display:flex;
  align-items:center;
}
.detalhes h1{
  display:inline-block;
  width:100%;
  text-align:center;
}
.destaque{
  background:#95a5a6;
}
```

Agora vamos ao [waypoints.js](https://github.com/imakewebthings/waypoints), não esqueça que é preciso o <strong>jquery</strong> para que ele funcione, importe no seu projeto e crie o seu <strong>.js</strong>:

```javascript
var waypoint = new Waypoint({
  element: $('.detalhes'),
  handler: function() {
    $('.detalhes h1').toggleClass('animated fadeIn delay');
  },
  offset:'100%',
});
```

No arquivo acima, estou "setando" um novo Waypoint, que no caso é a section detalhes, e disparando a função toggleClass do Jquery. O parâmetro offset com o valor 100% faz a função disparar somente quando 100% do elemento esteja visível na tela.

Você pode testar ao invés de chamar o toggleClass, chamar um console.log alguma coisa para ver que já estará funcionando. Tá, mas cadê a animação? Como visto no .js, dei um toggle em algumas classes, são as seguintes que vou adicionar no css:

```css
.animated {
//Faz a animação tanto na ida quanto na volta
  animation-fill-mode: both;
//Duração da animação em segundos
  animation-duration: 1s;
}
@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

.delay {
//Quando a animação irá iniciar
  animation-delay: 1s;
}
.fadeIn {
//Nome da animação
  animation-name: fadeIn;
}
```

Quem faz a mágica ali é o @keyframes que controla a animação de 0 a 100, Quando a animação se inicia a opacidade está 0 e conforme ela vai indo ao 100 ela vai aumentando chegando ao valor final de 1. Por fim eu adiciono a animação na classe <strong>fadeIn</strong>. E chamo utilizando o meu <strong>.js</strong>

Caso queiram ver na prática, fiz um codepen com esse código do post. A animação fadeIn é só um exemplo, você pode criar qualquer coisa e passar no @keyframes. Acho que é isso, qualquer coisa só perguntar, flvvv :]

Segue o link do codepen: [https://codepen.io/haykou/pen/YVpExN](https://codepen.io/haykou/pen/YVpExN)