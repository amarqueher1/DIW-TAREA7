# Adóptame - Encuentra tu compañero perfecto

Repositorio de la tarea DIW7 SVGs y Animaciones de Adur Marques

## Decisiones de Diseño

### 1. **Diseño Mobile-First**
   - La estructura y los estilos han sido diseñados priorizando a los dispositivos móviles. 
   - Se utilizan **media queries** para ajustar el diseño en pantallas más grandes, asegurando una experiencia de usuario óptima en todos los dispositivos.

### 2. **Uso de Variables CSS**
   - Se han definido variables en `:root` para colores, tipografía, espaciado, bordes y sombras. Esto facilita la consistencia visual y permite realizar cambios globales de manera sencilla.
   - Ejemplo:
     ```css
     :root {
       --color-primary: #ff6b6b;
       --font-size-base: 1rem;
       --spacing-sm: 1rem;
     }
     ```

### 3. **Tipografía**
   - Se ha utilizado la fuente `Poppins` para un diseño moderno y amigable.
   - Los tamaños de fuente están definidos en `rem` para garantizar escalabilidad y accesibilidad.

### 4. **Estructura BEM**
   - Se ha seguido la metodología BEM (Block, Element, Modifier) para nombrar las clases CSS, lo que mejora la legibilidad y el mantenimiento del código.
   - Ejemplo:
     ```html
     <div class="tarjeta-mascota">
       <div class="tarjeta-mascota__imagen"></div>
       <div class="tarjeta-mascota__info"></div>
     </div>
     ```

### 5. **Colores y Accesibilidad**
   - Se han seleccionado colores con buen contraste para garantizar la legibilidad.
   - Los botones y enlaces tienen estados `hover` para mejorar la experiencia del usuario.

## Animaciones

### 1. **Animación de Botones**
  Los botones tienen una animación de desplazamiento hacia arriba y una sombra al pasar el cursor (`hover`).
  - Implementación:
     ```css
     .boton--primary:hover {
       transform: translateY(-0.125rem); /* 2px */
       box-shadow: var(--shadow-md);
     }
     ```

### 2. **Animaciones en SVGs**
  El SVG de la primera mascota incluye una animación que utiliza las propiedades stroke-dasharray y stroke-dashoffset para simular el dibujo progresivo de la cola.
   
  Además, se emplea la propiedad transform para generar un movimiento oscilante, dando la impresión de que la cola se mueve de manera natural.

  Por otro lado se ha utilizado la propiedad transform para animar el movimiento de los ojos de la mascota, simulando una mascota feliz.

   - Implementación:
     ```css
      .cola {
        stroke-dasharray: 300; /* Define la longitud total del trazo para el contorno de la cola */
        stroke-dashoffset: 300; /* Oculta el trazo inicialmente desplazándolo completamente */
        fill: transparent; /* La cola no tiene relleno al inicio */
        animation: 
          dibujarCola 2s ease-out forwards, /* Dibuja el contorno de la cola en 2 segundos */
          mostrarRelleno 0.5s ease forwards, /* Aplica el relleno después del dibujo */
          moverCola 0.5s ease-in-out infinite alternate; /* Oscila la cola continuamente */
        animation-delay: 0s, 2s, 2.5s; /* Retrasa cada animación para que ocurran en secuencia */
        transform-origin: left center; /* Establece el punto de pivote para la rotación de la cola */
      }

      /* Animación para dibujar el contorno de la cola */
      @keyframes dibujarCola {
        to {
          stroke-dashoffset: 0; /* Reduce el desplazamiento a 0, revelando el trazo */
          stroke-dasharray: 0; /* Elimina el efecto de trazo una vez completado */
        }
      }

      /* Animación para mostrar el relleno de la cola */
      @keyframes mostrarRelleno {
        to {
          fill: #C57D08; /* Aplica un color de relleno a la cola */
        }
      }

      /* Animación para oscilar la cola */
      @keyframes moverCola {
        0% {
          transform: rotate(0deg); /* Posición inicial de la cola */
        }
        100% {
          transform: rotate(2deg); /* Rotación ligera hacia un lado */
        }
      }

      .ojos {
        animation: agrandarYGirar 1s ease-in-out infinite alternate; /* Escala y rota los ojos continuamente */
        transform-origin: center; /* Establece el punto de pivote en el centro de los ojos */
      }

      /* Animación para escalar y rotar los ojos */
      @keyframes agrandarYGirar {
        to {
          transform: scale(1.05) rotate(1deg); /* Aumenta ligeramente el tamaño y rota los ojos */
        }
      }
     ```

## Resumen

1. **Estructura HTML**:
   - El HTML está dividido en secciones (`header`, `main`, `footer`) con clases específicas para cada bloque.
   - Ejemplo:
     ```html
     <section id="mascotas" class="mascotas">
       <div class="container">
         <h2>Nuestras Mascotas</h2>
         <div class="tarjeta-mascota">
            <div class="tarjeta-mascota__imagen">
              ...
            </div>
          </div>
       </div>
     </section>
     ```

2. **Estilos CSS**:
   - Los estilos están organizados por bloques y se utilizan media queries para adaptarse a diferentes tamaños de pantalla.

3. **Interactividad**:
   - Las animaciones y efectos `hover` están diseñados para mejorar la experiencia del usuario y guiar su atención hacia elementos clave.