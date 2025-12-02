<template>
  <header class="header">
    <!-- Logo -->
    <div class="logo">
      <img 
        src="/logo.png.png" 
        class="logo-img" 
        alt="Logo Mordiditas" 
        @click="playNextSound" 
      />
    </div>

    <!-- Menú de navegación -->
    <nav class="nav">
      <ul>
        <li><a href="#" @click="playSound('ladrido')">Inicio</a></li>
        <li><a href="#" @click="playSound('maullido')">Productos</a></li>
        <li><a href="#" @click="playSound('pitido')">Contacto</a></li>
        <li><a href="#" @click="playSound('maullido')">Quienes somos</a></li>
      </ul>
    </nav>
  </header>
</template>

<script setup>
import { ref } from 'vue'

// Pre-cargar los sonidos
const sonidos = {
  ladrido: new Audio('/ladrido.mp3.mp3'),
  maullido: new Audio('/maullido.mp3.mp3'),
  pitido: new Audio('/pitido.mp3.mp3')
}

// Para el logo seguimos con la rotación de sonidos
const sounds = [sonidos.ladrido, sonidos.maullido, sonidos.pitido]
const currentIndex = ref(0)

function playNextSound() {
  const audio = sounds[currentIndex.value]
  audio.currentTime = 0
  audio.play().catch(err => console.error('Error al reproducir:', err))
  currentIndex.value = (currentIndex.value + 1) % sounds.length
}

// Para las secciones, reproducimos directamente el sonido indicado
function playSound(tipo) {
  const audio = sonidos[tipo]
  audio.currentTime = 0
  audio.play().catch(err => console.error('Error al reproducir:', err))
}
</script>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #ffe0e0;
  padding: 1rem 2rem;
  border-bottom: 1px solid #f3caca;
}

.logo-img {
  height: 250px;
  width: auto;
  display: block;
  border-radius: 50%;
  border: 7px solid #000;
  transition: transform 0.3s ease;
}

.logo-img:hover {
  transform: scale(2.2) rotate(15deg);
}

.nav ul {
  list-style: none;
  display: flex;
  gap: 1.5rem;
  margin: 0;
  padding: 0;
}

.nav a {
  text-decoration: none;
  color: #333;
  font-weight: 600;
  transition: color 150ms ease;
}

.nav a:hover {
  color: #d6336c;
}
</style>
