<script>
  import { onMount } from 'svelte';
  let isLandscape = false; // Variable para controlar la orientación

  // Función para verificar la orientación y redirigir
  function checkOrientation() {
    if (window.innerWidth > window.innerHeight) {
      isLandscape = true; // Modo horizontal
      // Redirigir automáticamente a /home si está en modo horizontal
      window.location.href = '/login'; 
    } else {
      isLandscape = false; // Modo vertical
    }
  }

  // Verificar la orientación al montar el componente y cuando se cambia el tamaño de la ventana
  onMount(() => {
    checkOrientation(); // Verifica la orientación al cargar
    window.addEventListener('resize', checkOrientation); // Detecta el cambio de orientación
  });

  // Limpiar el evento de resize cuando el componente se destruye
  import { onDestroy } from 'svelte';
    import FullScreen from './components/FullScreen.svelte';
  onDestroy(() => {
    window.removeEventListener('resize', checkOrientation);
  });
</script>

{#if !isLandscape}
  <!-- Mensaje pidiendo al usuario girar el teléfono -->
  <div class="orientation-message">
    <h3 class="mt-12">Por favor, gira tu teléfono a modo horizontal para continuar.</h3>
    <p>Se recomienda subir el volumen para disfrutar de los efectos de sonido</p>
    <img src="/img/horiente.png" class="w-50" alt="">
  </div>
{/if}
<FullScreen />
{#if isLandscape}
  <!-- Aquí va el contenido de la página si el teléfono está en modo horizontal -->
  <div class="content">
    <h1>Contenido de la página</h1>
    <p>El contenido está listo para ser visto en modo horizontal.</p>
  </div>
{/if}

<style>
  /* Estilo para el mensaje de orientación */
  .orientation-message {
    text-align: center;
    padding: 20px;
  }

  /* Estilo para el contenido cuando está en modo horizontal */
  .content {
    text-align: center;
    padding: 20px;
  }
</style>
