# tipti.surf.ui
## Description
```
Esta es una prueba creando una clon de una interfaz web,
que incluye una galería que se puede mover con tracking del mouse
mostrando información de tablas de surf con diferentes imagenes y
precio.
```
Ejemplo final : [Surf UI](https://surf.santiagomora.com/)
## Stack
```
Para el proyecto se uso Vue, junto con las herramientas de Vue CLI, asi como el lenguaje de sass como preprocesador de css, adicional se escogio una estructura simple de carpetas en 
donde el proyecto se separa por Vistas y componentes reutilizables.
```

## Project setup
Luego de clonar el repositorio nos ubicamos dentro de la carpeta del proyecto e instalamos todas las dependencias atraves de NPM con siguiente comando
```
npm install
```


### Compiles and hot-reloads for development
Para levantar el proyecto en un servidor de desarrollo ejecutaremos el siguiente comando y accederemos a la ruta que nos provee el script
```
npm run serve
```

### Compiles and minifies for production
Compilación del proyecto para la súbida a producción.
```
npm run build
```

### Dependencies
El proyecto presentaba el reto de crear un drag dentro de los elementos,
se utilizo la libreria de Swiper, que nos provee de los metodos y eventos necesarios
para interactuar con el usuario atraves del movimiento del mouse en los elementos.

[Swiper](https://swiperjs.com/)

Para iniciar el proyecto se utilizo Vue Cli la cual es una herramienta que nos ayuda
en la creación de proyectos con vuejs, se escogió esta manera ya que el objetivo de la
prueba era desarrollar una interfaz muy parecida al ejemplo que se nos fue otorgado,
en un proyecto de gran desarrollo se consideraria configurar un sistema desde cero con
webpack que nos ayude en la compilación y automatización del proyecto para su paso a 
producción.

[Vue CLI](https://cli.vuejs.org/)