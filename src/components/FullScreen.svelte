<script>
    import { onMount } from 'svelte';
  
    // Función para activar el modo pantalla completa
    function enterFullScreen() {
      const element = document.documentElement; // Selecciona el <html> para hacer que toda la página se ponga en pantalla completa.
  
      if (element.requestFullscreen) {
        element.requestFullscreen();
      } else if (element.mozRequestFullScreen) { // Firefox
        element.mozRequestFullScreen();
      } else if (element.webkitRequestFullscreen) { // Chrome, Safari y Opera
        element.webkitRequestFullscreen();
      } else if (element.msRequestFullscreen) { // IE/Edge
        element.msRequestFullscreen();
      }
    }
  
    // Verificar si el dispositivo es móvil
    let isMobile = false;
  
    onMount(() => {
      if (window.innerWidth <= 768) { // Verifica si la pantalla tiene un ancho menor o igual a 768px (típico de dispositivos móviles)
        isMobile = true;
        // Activar pantalla completa al hacer clic en la página
        document.body.addEventListener('click', enterFullScreen);
      }
    });
  
    // Limpieza del evento cuando el componente se desmonta
    import { onDestroy } from 'svelte';
    onDestroy(() => {
      document.body.removeEventListener('click', enterFullScreen);
    });
  </script>
  
  <style>
    /* No es necesario agregar estilos, pero puedes personalizarlo si lo deseas */
  </style>
  