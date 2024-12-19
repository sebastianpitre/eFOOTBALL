<script>
  import { onMount } from 'svelte';
  import Carga from './components/Carga.svelte';

  let showOverlay = true;

  onMount(() => {
      setTimeout(() => {
          showOverlay = false;
      }, 16500); // 8 segundos
  });

  let videoElement;

    function playWithAudio() {
        videoElement.play(); // Asegura que el video se reproduzca
    }

    //Carga de la página

    let isLoading = false;

    // Función para manejar el clic en el enlace
    function handleClick(event, url) {
        event.preventDefault(); // Evita la navegación inmediata
        isLoading = true; // Muestra la animación de carga

        // Espera 2 segundos antes de redirigir
        setTimeout(() => {
            window.location.href = url; // Redirige a la nueva dirección
        }, 2000);
    }
</script>
<main>

  {#if isLoading}
    <Carga/>
  {/if}
  

  <div class="fullscreen-container">
    {#if showOverlay}
        <!-- Div superpuesto -->
        <div class="overlay">
          <h6 class="loading-text text-white" style="z-index: 9999;">Create by Sebastian pitre</h6>
          <!-- svelte-ignore a11y-media-has-caption -->
          <video autoplay loop id="myVideo" bind:this={videoElement}>
            <source src="/video/go.mp4" type="video/mp4">
          </video>
          <button class="unmute-button" on:click={playWithAudio}>Activar sonido</button>
        </div>
    {/if}
  
    <a href="/home" on:click={(event) => handleClick(event, '/home')}>
      <div class="background"></div>
    </a>
  </div>

</main>

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
    background: url('/img/login.png') no-repeat center center;
    background-size: cover;
    z-index: 1;
}

video{
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
}

/* Div superpuesto */
.overlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.8); /* Fondo negro translúcido */
    z-index: 2;
    display: flex;
    justify-content: center;
    align-items: center;
    color: white;
    font-size: 2rem;
}

/* Texto de carga */
.loading-text {
  position: absolute;
  left: 10px;
  bottom: 10px;
    animation: blink 1.5s infinite; /* Animación de parpadeo */
}

@keyframes blink {
    0%, 100% {
        opacity: 1;
    }
    50% {
        opacity: 0.5;
    }
}

</style>