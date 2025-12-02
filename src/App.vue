<template>
  <div class="app">
    <!-- Contenedor superior con logo y menú -->
    <section class="hero">
      <!-- Logo grande -->
      <div class="logo-container">
        <img 
          src="/logo.png.png" 
          alt="Logo Mordiditas" 
          class="logo-img" 
        />
      </div>

      <!-- Menú vertical -->
      <nav class="nav-vertical">
        <ul>
          <li><a href="#" @click="playSound('ladrido')">Inicio</a></li>
          <li><a href="#" @click="playSound('maullido')">Productos</a></li>
          <li><a href="#" @click="playSound('pitido')">Contacto</a></li>
          <li><a href="#" @click="playSound('maullido')">Quienes somos</a></li>
        </ul>
      </nav>
    </section>

    <!-- Mensaje de bienvenida -->
    <main class="main">
      <h1 class="bienvenida">🐾 Bienvenido a Mordiditas 🐾</h1>
      <p class="subtexto">Tu lugar para productos únicos, divertidos y llenos de personalidad</p>
    </main>
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
  background: #000; /* fondo negro */
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
}

/* Contenedor superior ocupa toda la pantalla */
.hero {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 6rem;
  height: 100vh;
  width: 100%;
}

/* Logo grande a la izquierda */
.logo-container {
  flex: 1;
  display: flex;
  justify-content: center;
}

.logo-img {
  height: 400px;
  width: auto;
  border-radius: 50%;
  border: 10px solid #fff; /* borde blanco para contraste */
  transition: transform 0.3s ease;
}

.logo-img:hover {
  transform: scale(1.1) rotate(10deg);
}

/* Menú vertical ocupa gran parte a la derecha */
.nav-vertical {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}

.nav-vertical ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

.nav-vertical li {
  margin: 2rem 0;
}

.nav-vertical a {
  text-decoration: none;
  font-size: 2.5rem;
  font-weight: 700;
  color: #fff; /* letras blancas */
  transition: color 200ms ease;
}

.nav-vertical a:hover {
  color: #d6336c; /* efecto hover rosado */
}

/* Mensaje de bienvenida debajo */
.main {
  margin: 3rem 0;
  text-align: center;
}

.bienvenida {
  font-size: 3rem;
  font-weight: 700;
  color: #fff; /* blanco */
  margin-bottom: 1rem;
  text-shadow: 2px 2px 4px rgba(255,255,255,0.2);
}

.subtexto {
  font-size: 1.4rem;
  color: #ccc; /* gris claro para contraste */
  max-width: 600px;
  margin: 0 auto;
  line-height: 1.6;
}
</style>
