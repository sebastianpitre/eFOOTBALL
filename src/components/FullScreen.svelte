<script>
    import { onMount } from 'svelte';
    import { onDestroy } from 'svelte';
  
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
  
    // Función para salir del modo pantalla completa
    function exitFullScreen() {
      if (document.exitFullscreen) {
        document.exitFullscreen();
      } else if (document.mozCancelFullScreen) { // Firefox
        document.mozCancelFullScreen();
      } else if (document.webkitExitFullscreen) { // Chrome, Safari y Opera
        document.webkitExitFullscreen();
      } else if (document.msExitFullscreen) { // IE/Edge
        document.msExitFullscreen();
      }
    }
  
    // Función que se activa con el toque del usuario para poner la pantalla en modo completo
    function handleTap() {
      enterFullScreen(); // Activa el modo pantalla completa
    }
  
    onMount(() => {
      // Agrega un evento de toque para activar la pantalla completa
      document.addEventListener('click', handleTap);
    });
  
    // Limpia el evento cuando el componente se destruye
    onDestroy(() => {
      document.removeEventListener('click', handleTap);
    });
  </script>
  
  <style>
    /* Puedes agregar un estilo opcional, como una indicación visual de que el toque activará la pantalla completa */
    body {
      cursor: pointer;
    }
  </style>
  