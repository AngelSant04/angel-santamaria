# Vue Prueba Técnica

Este repositorio contiene el proyecto de prueba técnica en Vue. La aplicación es una SPA (Single Page Application) que permite ver un listado de peliculas, consumida con axios al momento de la carga y filtrar por nombre, genero y descripción.

## Requisitos Previos

Asegúrate de tener instalado lo siguiente:

- Node.js (versión 14 o superior)
- npm (versión 6 o superior) o yarn (versión 1.22 o superior)

## Instalación

Sigue los siguientes pasos para instalar y ejecutar el proyecto localmente:

1. **Clonar el repositorio:**

   ```bash
   git clone https://github.com/AngelSant04/angel-santamaria.git
   cd angel-santamaria

2. **Instalar Dependencias:**

 Usando npm:

    ``` npm install

 Usando yarn:

    ``` yarn install

3. **Scripts Disponibles:**
    En el directorio del proyecto, puedes ejecutar:

    ``` npm run serve o yarn serve
    
    Ejecuta la aplicación en modo desarrollo.

    ``` npm run build o yarn build
    
    Compila la aplicación para producción en la carpeta dist.
    Empaqueta correctamente React en modo de producción y optimiza la compilación para obtener el mejor rendimiento.

   ```npm run lint o yarn lint

    Ejecuta ESLint para encontrar y arreglar problemas en el código.

    ```npm run lint:fix o yarn lint:fix
   
    Ejecuta ESLint y trata de arreglar automáticamente los problemas encontrados en el código.

    ```npm run format o yarn format
   
    Formatea el código utilizando Prettier.  
    Este comando se aplica a todos los archivos del proyecto, asegurando un formato consistente.

## Estructura del Proyecto:

    ├── node_modules
    ├── public
    │   └── imgs (Carpeta de imagenes de las peliculas).
    │   └── index.html
    │   └── Movies.json
    ├── src
    │   ├── assets
    │   │   └── styles
    │   │       └── Styles.css
    │   ├── components
    │   │   ├── AppFooter.vue
    │   │   ├── AppHeader.vue
    │   │   ├── CardMovie.vue
    │   ├── interface
    │   │   └── Movie.ts
    │   ├── router
    │   │   └── index.ts
    │   ├── store
    │   │   └── index.ts
    │   ├── views
    │   │   ├── ErrorPage.vue
    │   │   └── HomeView.vue
    │   ├── App.vue
    │   ├── main.ts
    ├── .gitignore
    ├── .prettierrc
    ├── .babel.config.js
    ├── package-lock.json
    ├── package.json
    ├── README.md
    ├── tsconfig.json
    └── .vue.config.js


## Notas Adicionales:

    Persistencia de Datos: La información del primary color se almacena en localStorage.
    
    API: La aplicación se conecta a una API(axios) para obtener caracteristicas de las peliculas.
    
    Responsividad: La aplicación es responsiva y se ajusta para verse correctamente en diferentes tamaños de pantalla.
    

## Problemas Comunes:

    Error al ejecutar npm run serve: Asegúrate de ejecutar npm run format o yarn format 
    para asegurar el formato consistente configurado en el proyecto.

## Contribuciones:
    Las contribuciones son bienvenidas. Por favor, abre un issue para discutir lo que te gustaría cambiar.


