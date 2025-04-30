<!-- Script JS -->
<script>
  /* Importamos d3 para tenerlo disponible */
  import * as d3 from 'd3'

  /* Sprites */
  let p1 = "./images/personaje1.png";
  let p2 = "./images/personaje2.png";
  let p3 = "./images/personaje3.png";
  let p4 = "./images/personaje4.png";
  let p5 = "./images/personaje5.png";
  let p6 = "./images/personaje6.png";
  let p7 = "./images/personaje7.png";
  let p8 = "./images/personaje8.png";
  let p9 = "./images/personaje9.png";
  let p10 = "./images/personaje10.png";
  let p11 = "./images/personaje11.png";
  let p12 = "./images/personaje12.png";
  let p13 = "./images/personaje13.png";
  let p14 = "./images/personaje14.png";
  let p15 = "./images/personaje15.png";
  let p16 = "./images/personaje16.png";

  /* Avatares */
  let a1 = "./images/avatar1.png";
  let a2 = "./images/avatar2.png";  
  let a3 = "./images/avatar3.png";  
  let a4 = "./images/avatar4.png";  
  let a5 = "./images/avatar5.png";  
  let a6 = "./images/avatar6.png";  
  let a7 = "./images/avatar7.png";  
  let a8 = "./images/avatar8.png";  
  let a9 = "./images/avatar9.png";  
  let a10 = "./images/avatar10.png";  

  let altura = d3.scaleLinear()
    .domain([0, 100])
    .range([0, 19]);

  let players = [
    { sprite: p1, avatar: a1, vida: 24, nombre: "Brak", padding: 14.7 },
    { sprite: p14, avatar: a10, vida: 33, nombre: "Poki", padding: 14.5 },
    { sprite: p3, avatar: a9, vida: 42, nombre: "Bocón", padding: 14  },
    { sprite: p4, avatar: a4, vida: 54, nombre: "Hakon", padding: 13.4  },
    { sprite: p10, avatar: a5, vida: 63, nombre: "Viggo", padding: 12.4  },
    { sprite: p11, avatar: a6, vida: 71, nombre: "Kolska", padding: 10 },
    { sprite: p6, avatar: a2, vida: 77, nombre: "Ragnar", padding: 10 },
    { sprite: p2, avatar: a8, vida: 87, nombre: "Hargoth", padding: 8.5 },
    { sprite: p16, avatar: a3, vida: 92, nombre: "Torvald", padding: 8 },
    { sprite: p13, avatar: a7, vida: 98, nombre: "Zerak", padding: 4.8 }
  ]

  let player_actual = players[0];
  let player_actual_rival = players[7];  
  let espacio_padding = (15.2 - altura(player_actual_rival.vida) + 8.5).toString() + "rem";

  function spriteAnterior() {
    if (player_actual == players[1]) {
      player_actual = players[0];
    } else if (player_actual == players[2]) {
      player_actual = players[1];
    } else if (player_actual == players[3]) {
      player_actual = players[2];
    } else if (player_actual == players[4]) {
      player_actual = players[3];
    } 
  }

  function spriteSiguiente() {
    if (player_actual == players[0]) {
      player_actual = players[1];
    } else if (player_actual == players[1]) {
      player_actual = players[2];
    } else if (player_actual == players[2]) {
      player_actual = players[3];
    } else if (player_actual == players[3]) {
      player_actual = players[4];
    } 
  }

  function spriteAnterior_rival() {
    if (player_actual_rival == players[6]) {
      player_actual_rival = players[5];
    } else if (player_actual_rival == players[7]) {
      player_actual_rival = players[6];
    } else if (player_actual_rival == players[8]) {
      player_actual_rival = players[7];
    } else if (player_actual_rival == players[9]) {
      player_actual_rival = players[8];
    } 
    espacio_padding = (15.2 - altura(player_actual_rival.vida) + 8.5).toString() + "rem";
  }

  function spriteSiguiente_rival() {
    if (player_actual_rival == players[5]) {
      player_actual_rival = players[6];
    } else if (player_actual_rival == players[6]) {
      player_actual_rival = players[7];
    } else if (player_actual_rival == players[7]) {
      player_actual_rival = players[8];
    } else if (player_actual_rival == players[8]) {
      player_actual_rival = players[9];
    } 
    espacio_padding = (15.2 - altura(player_actual_rival.vida) + 8.5).toString() + "rem";
  }


</script>

<!-- Estructura contenido HTML -->
<main id="container">
  <h1 class="title blanco">The Last Battle</h1>
  
  <div class="linea">
    <hr style="width: 40em;">
  </div>

  <h3 class="subtitle blanco">¿Crees que tienes lo suficiente para ganar esta batalla?</h3>

  <div class="linea">
    <hr style="width: 40em;">
  </div>


  <div class="visualizacion1 fondo">

    <div class="barra_flex">
      <div class="avatar_flex">
        <img class="avatar" src={player_actual.avatar} alt="avatar1"/>
        <div class="barra1">
          {#if player_actual.vida > 70}
            <div style="height: 100%; width: {player_actual.vida}%; background-color: green;">
              <p class="tamaño_vidaN24 blanco">{player_actual.vida}%</p>
            </div>
          {:else if player_actual.vida > 35}
            <div style="height: 100%; width: {player_actual.vida}%; background-color: orange;">
              <p class="tamaño_vidaN24 blanco">{player_actual.vida}%</p>
            </div>
          {:else}
            <div style="height: 100%; width: {player_actual.vida}%; background-color: red;">
              <p class="tamaño_vidaN24 blanco">{player_actual.vida}%</p>
            </div>
          {/if}
        </div>
      </div>
      
      <div class="avatar_flex">
        <div class="barra2">
          {#if player_actual_rival.vida > 70}
          <div style="height: 100%; width: {player_actual_rival.vida}%; background-color: green;">
            <p class="tamaño_vidaN87 blanco">{player_actual_rival.vida}%</p>
          </div>
          {:else if player_actual_rival.vida > 35}
          <div style="height: 100%; width: {player_actual_rival.vida}%; background-color: orange;">
            <p class="tamaño_vidaN87 blanco">{player_actual_rival.vida}%</p>
          </div>
          {:else}
          <div style="height: 100%; width: {player_actual_rival.vida}%; background-color: red;">
            <p class="tamaño_vidaN87 blanco">{player_actual_rival.vida}%</p>
          </div>
          {/if}
        </div>
        <img class="avatar" src={player_actual_rival.avatar} alt="avatar2"/>
      </div>
        
    </div>

    <div class="player_flex" style="padding-top: {espacio_padding}">
      
      <div style="padding-left: {player_actual.padding}rem;">
        <img style="height: {altura(player_actual.vida)}rem;" src={player_actual.sprite} alt="person"/>
      </div>

      <div style="padding-right: {player_actual_rival.padding}rem;">
        <img style="height: {altura(player_actual_rival.vida)}rem;" class="player2" src={player_actual_rival.sprite} alt="person"/>
      </div>

    </div>

    <div class="flechas_container"> 

      <button class="boton1" on:click={spriteAnterior}>
        <img class="flecha" src="./images/flecha_izq.svg" alt="flecha_izq"/>
      </button>

      <button class="boton1" on:click={spriteSiguiente}>
        <img class="flecha" src="./images/flecha_der.svg" alt="flecha_izq"/>
      </button>

      <button class="boton2" on:click={spriteAnterior_rival}>
        <img class="flecha" src="./images/flecha_izq.svg" alt="flecha_izq"/>
      </button>

      <button class="boton1" on:click={spriteSiguiente_rival}>
        <img class="flecha" src="./images/flecha_der.svg" alt="flecha_izq"/>
      </button>

    </div>

  </div>

  
  <div class="catalogo">
    <div>
      <h2 style="color: white; text-align: center;"> ───────────────────────────  ❤️ Estadísticas de vida ❤️  ────────────────────────── </h2>
      <p style="text-align:center; font-size: 1.25rem;" class="blanco">Presione sobre cada personaje para visualizar su vida restante</p>
    </div>

    <div class="comparacion_alturas">
      <!-- Líneas horizontales -->
      <div class="linea_horizontal" style="top: 4.5rem;"></div>
      <div class="linea_horizontal" style="top: 6.5rem;"></div>
      <div class="linea_horizontal" style="top: 8.5rem;"></div>
      <div class="linea_horizontal" style="top: 10.5rem;"></div>
      <div class="linea_horizontal" style="top: 12.5rem;"></div>
      <div class="linea_horizontal" style="top: 14.5rem;"></div>


      <!-- Personajes -->
      <div class="catalogo_flex">
        {#each players as player} 
          <div class="datos_flex">
            {#if player.vida > 70 }
              <div class="vida_contenedor">
                <p style="font-size:0.9rem;" class="vida rojo3">{player.vida}</p>
                <img class="zoom" src={player.sprite} alt="catalogo" style="height: {altura(player.vida)*0.52}rem;"/>
              </div>
            {:else if player.vida > 35}
              <div class="vida_contenedor">
                <p style="font-size:0.9rem;" class="vida rojo3">{player.vida}</p>
                <img class="zoom" src={player.sprite} alt="catalogo" style="height: {altura(player.vida)*0.52}rem;"/>
              </div>
            {:else}
              <div class="vida_contenedor">
                <p style="font-size:0.9rem;" class="vida rojo3">{player.vida}</p>
                <img class="zoom" src={player.sprite} alt="catalogo" style="height: {altura(player.vida)*0.52}rem;"/>
              </div>
            {/if}
            <p style="font-size:1.05rem; color: white;">{player.nombre}</p>
          </div>
        {/each}
      </div>
    </div>

  </div>

  <div class="texto_flex visualizacion2">
    <div>
      <h2 class="blanco">Round final</h2>

      <hr>

      <p class="blanco tamaño_texto">
        En el reino de Valdranor, la Arena de los Campeones era el lugar donde solo los guerreros más valientes podían demostrar su honor. Durante siglos, grandes batallas se habían librado allí, pero ninguna como la que estaba por suceder. <br> <br>

        Un llamado ancestral ha reunido a los mejores 10 combatientes, quienes han crecido en fuerza con sus enfrentamientos y victorias pasados. Luego de una larga espera, la batalla ha dado su inicio. <br> <br>
        
        En esta visualización web, se representa a cada guerrero con un tamaño proporcional a su <span class="rojo3">vida restante</span>. A medida que reciben daño, su figura se reduce, reflejando no solo su desgaste físico, sino también la merma de su poder. <br> <br>

        No solo son combatientes. Son vikingos que cuentan historias. Brak el Gladiador, quien ha estado en constante ascenso, tendrá que enfrentarse ahora con leyendas como Hargoth el Imbatible, un guerrero temido incluso entre los más valientes. ¿Quién se alzará como el verdadero campeón de la Arena?
      </p>
    </div>
    
    <div>
      <img src="./images/trailer.png" alt="trailer" class="trailer"/>
    </div>

  </div>


  <div style="margin-top: 5rem;">
    <h2 style="color: white; text-align: center;"> ─────────────────────────  ⚔️ Estadísticas de combate ⚔️  ──────────────────────── </h2>
    
    <div style="margin-left: 3.3rem;">
      <div class="flourish-embed flourish-radar" data-src="visualisation/22656277" data-width="96%">
        <script src="https://public.flourish.studio/resources/embed.js"></script>
        <noscript>
          <img src="https://public.flourish.studio/visualisation/22656277/thumbnail" width="95%" alt="radar visualization" />
        </noscript>
      </div>
    </div>
  </div>
  

  
  <div style="margin-left: 1.5rem; display: flex; flex-direction: row;">
    <div style="width: 43rem;" class="flourish-embed flourish-chart" data-src="visualisation/22655516" data-width="100%">
      <script src="https://public.flourish.studio/resources/embed.js"></script>
      <noscript>
        <img src="https://public.flourish.studio/visualisation/22655516/thumbnail" width="100%" alt="chart visualization" />
      </noscript>
    </div>

    <div style="width: 31rem; color: white; padding-top: 6.4rem;">
      <p>
        En la Arena de los Campeones, cada guerrero ha estado perfeccionando su estilo de combate, equilibrando tres atributos clave: <span class="rojo2">ataque</span>, <span class="verde">resistencia</span> y <span class="azul">velocidad</span>. <br> <br>

        Las combinaciones varían notablemente entre ellos. Algunos como Hakon, destacan por su ofensiva y agilidad, aunque sacrifican resistencia en el campo de batalla. Otros como Ragnar, no sobresalen en ninguna categoría individual, pero han superado igualmente sus límites manteniéndose todavía con vida. <br> <br>

        Durante mucho tiempo, todas las apuestas apuntaban hacia una final entre los hermanos Viggo y Kolska, dado que superan en características al resto. Su rivalidad fraternal se convirtió en leyenda, y su enfrentamiento, en una de las batallas más esperadas. Sin embargo, los giros del destino han debilitado cada vez más sus fuerzas, y ahora su futuro es incierto. Pero... ¿y si todo lo que creías del combate… estaba por cambiar?
      </p>
    </div>
  </div>

</main>
  

<footer>
  <div class="footer_contenedor">
    <p class="gris" style="font-size: 14px; margin-bottom: 0">Denis Wu <br>
      Proyecto I: El lenguaje visual de los datos <br>
      Visualización de Datos - Licenciatura en Tecnología Digital 2025
    </p>
    <div class="redes_contenedor">
      <a href="https://github.com/Denis0827" target="_blank">
        <img style="width: 31px; height: 31px;" src="./images/github.png" alt="github">
      </a>
      <a href="https://www.linkedin.com/in/deniswu0827/" target="_blank">
        <img style="width: 43px; height: 43px; margin-left: 3px;" src="./images/linkedin.png" alt="linkedin">
      </a>
      <a href="https://www.instagram.com/denisito0827/" target="_blank">
        <img style="width: 33px; height: 33px; margin-left: 3px;" src="./images/instagram.png" alt="instagram">
      </a>
      <a href="https://www.facebook.com/profile.php?id=100075782354851&locale=es_LA" target="_blank">
        <img style="width: 35px; height: 35px; margin-left: 7px;" src="./images/facebook.png" alt="facebook">
      </a>
      <a href="https://x.com/Denis91547332" target="_blank">
        <img style="width: 55px; height: 55px;" src="./images/x.png" alt="x"> 
      </a>
    </div>
  </div>
</footer>

<!-- Estilos CSS -->
<style>
  
@import url('https://fonts.googleapis.com/css2?family=Bungee&family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&family=Ubuntu:ital,wght@0,300;0,400;0,500;0,700;1,300;1,400;1,500;1,700&display=swap');

  .title {
    font-size: 3rem;
    margin-top: 1.5rem;
    margin-bottom: 0.75rem;
    font-family: 'Bungee', sans-serif;
  }

</style>
