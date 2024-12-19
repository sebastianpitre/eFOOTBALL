
<div>
    <!-- Animación de carga -->
    <div class="loading-overlay">
        <div class="spinner"></div>
    </div>
</div>
<style>
    /* Superposición de carga */
.loading-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background: rgba(0, 0, 0, 0.8); /* Fondo oscuro translúcido */
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 9999;
}

/* Estilo del spinner */
.spinner {
    width: 50px;
    height: 50px;
    border: 5px solid rgba(255, 255, 255, 0.3); /* Borde translúcido */
    border-top: 5px solid white; /* Borde superior */
    border-radius: 50%;
    animation: spin 1s linear infinite; /* Animación */
}

@keyframes spin {
    from {
        transform: rotate(0deg);
    }
    to {
        transform: rotate(360deg);
    }
}

</style>