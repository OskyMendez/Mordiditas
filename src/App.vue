<template>
  <div class="app">
    <!-- Logo arriba -->
    <div class="logo-container">
      <img 
        src="/mordiditas2.jpg"
        alt="Logo Mordiditas" 
        class="logo-img" 
      />
    </div>
      <!-- Mensaje de bienvenida -->


    <!-- Menú horizontal debajo del logo -->
    <nav class="nav-horizontal">
      <ul>
        <li><a href="#" @click="playSound('ladrido')">Inicio</a></li>
        <li><a href="#" @click="playSound('maullido')">Productos</a></li>
        <li><a href="#" @click="playSound('pitido')">Contacto</a></li>
        <li><a href="#" @click="playSound('maullido')">Quienes somos</a></li>
      </ul>
    </nav>
    <div class="footer-img">
  <img src="/public/footer.png.png" alt="Imagen inferior Mordiditas" />
</div>


  
  </div>
</template>

<script setup>
// Pre-cargar sonidos
const sonidos = {
  ladrido: new Audio('/ladrido.mp3.mp3'),
  maullido: new Audio('/maullido.mp3.mp3'),
  pitido: new Audio('/pitido.mp3.mp3')
}

function playSound(tipo) {
  const audio = sonidos[tipo]
  audio.currentTime = 0
  audio.play().catch(err => console.error('Error al reproducir:', err))
}
</script>

<style scoped>
.app {
  font-family: 'Poppins', Arial, sans-serif;
  background: url('/fondo.jpg.jpg') no-repeat center center fixed;
  background-size: cover; /* hace que la imagen ocupe toda la pantalla */
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
}


/* Logo arriba */
.logo-container {
  margin-top: 2rem;
  width: 100%; /* que ocupe todo el ancho */
  display: flex;
  justify-content: center;
}

.logo-img {
  width: 90%; /* ocupa el 90% del ancho de la pantalla */
  max-width: 800px; /* límite máximo para que no se deforme en pantallas grandes */
  height: auto;
  border: 12px solid #000000; /* borde negro */
  transition: transform 0.3s ease;
}

.logo-img:hover {
  transform: scale(1.02) rotate(3deg);
}


/* Menú horizontal */
.nav-horizontal ul {
  list-style: none;
  margin: 2rem 0;
  padding: 0;
  display: flex;
  gap: 3rem; /* espacio entre secciones */
}
.nav-horizontal a {
  text-decoration: none;
  font-size: 2rem;
  font-weight: 700;
  color: #ed1c70; /* fucsia */
  transition: color 200ms ease;
}
.nav-horizontal a:hover {
  color: #8c52ff; /* violeta */
}

.main {
  margin: 3rem 0;
  text-align: center;
  background: #8c52ff; /* lila */
  color: #fff;
  padding: 2.5rem 2rem;
  border-radius: 12px; /* bordes suaves, no tan redondeados */
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.15); /* sombra más difusa */
  border: 1px solid rgba(255, 255, 255, 0.2); /* borde tenue tipo brillo */
  backdrop-filter: blur(2px); /* efecto de suavizado si hay fondo detrás */
  transition: all 0.3s ease;
}

.bienvenida {
  font-size: 2.5rem;
  font-weight: 700;
  color: #0e0e0e;
  margin-bottom: 1rem;
 
}
.footer-img {
  width: 200%;
  margin-top: auto;
}

.footer-img img {
  width: 100%;
  height: auto;
  display: block;
}


</style>
