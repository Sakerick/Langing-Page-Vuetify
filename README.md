📸 Random Image Card Gallery
Una aplicación interactiva construida con Vue 3 y Vuetify 3 que consume la API de Picsum Photos para mostrar tarjetas de imágenes aleatorias con estados de carga optimizados.

🚀 Características
Generación Aleatoria: Obtiene imágenes y autores únicos de forma dinámica.

UX Fluida: Implementación de v-skeleton-loader para evitar saltos de interfaz mientras las imágenes cargan.

Estado de Carga: Botón interactivo con estado :loading y deshabilitado preventivo durante peticiones asíncronas.

Diseño Responsivo: Grid system de Vuetify para una visualización perfecta en cualquier dispositivo.

Componentización: Estructura limpia basada en componentes reutilizables (CardComp, TableComp).

🛠️ Stack Tecnológico
Framework: Vue 3 (Script Setup)

UI Library: Vuetify 3

Lenguaje: TypeScript

API: Lorem Picsum

Bundler: Vite

📦 Instalación
Clona el repositorio:

Bash
git clone https://github.com/tu-usuario/nombre-del-proyecto.git
cd nombre-del-proyecto
Instala las dependencias:

Bash
npm install
# o
yarn install
Inicia el servidor de desarrollo:

Bash
npm run dev
🧩 Estructura del Componente Principal
El corazón del proyecto reside en la lógica de changeImages(), la cual gestiona el ciclo de vida de la petición:

TypeScript
async function changeImages() {
  isLoading.value = true; // Activa Skeletons y Spinners
  try {
    const [img1, img2] = await fetchRandomImages();
    // Asignación reactiva de datos...
  } finally {
    isLoading.value = false; // Desactiva estados de carga
  }
}
