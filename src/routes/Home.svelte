<script>

</script>

<div class="fullscreen-container">

  <div>
    <div class="background"></div>
  </div>

  <audio controls autoplay loop>
    <source src="/audios/gemidos.mp3" type="audio/mpeg">
  </audio>
</div>

<style>
  /* Contenedor principal que ocupa toda la pantalla */
.fullscreen-container {
    position: relative;
    width: 100vw;
    height: 100vh;
    overflow: hidden;
    display: flex;
    justify-content: center;
    align-items: center;
}

/* Imagen de fondo */
.background {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: url('/img/Home.png') no-repeat center center;
    background-size: cover;
    z-index: 1;
}

</style>