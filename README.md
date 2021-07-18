# El problema con React básico

- `React`  esta enfocado en la vista (`view`) de nuestra aplicación.
- `React` no tiene enfoque en el modelo (`model`) y el controlador (`controller`) de nuestra aplicación. 

### React Data management. (Investigar)

- React está diseñado a propósito, para permitir a los desarrolladores tomar sus propias decisiones de administración de datos. 

- La mayoría de los desarrolladores de React no piensan mucho en estas decisiones.

### Separation of concerns en React. (Investigar)

Esta es la idea principal detrás de la mayoría de las herramientas del Ecosistema `React`.

### React Ecosystem. (Investigar)

- `React Redux` - State Management - using flux architecture
- `Redux Thunk` - Side Effect Management (network requests, etc)
- `Reselect` -  Abstract away the state's structure
- `Styled Components` - Abstract away the state's structure

# Preparando nuestro entorno de trabajo

Debes tener instalado: 

- Git Bash
- Cuenta de GitHub
- Node y NPM
- VSC

Los pasos siguientes los realizamos en la terminal provista por VSC. 

1. Verificamos  en que directorio de trabajo nos encontramos. En nuestro caso estamos en una carpeta llamada `/react` y usamos un sistema de archivos de `linux`. 

```bash
pwd
# /home/tu_user/Documents/courses_notes/react
```

2. Si no te encuentras en una ruta como la nuestra ruta `~tu_user/Documents/courses_notes/react` debes crearla.

3. Muévete a tu carpeta `Documents` o `Documentos`

```bash
cd Documents
```

​    3.1 Creamos una carpeta `courses_notes`

```bash
mkdir courses_notes
```

4. Nos movemos a  `courses_notes`

```bash
cd courses_notes
```

5. Creamos la carpeta  `react`

```bash
mkdir react
```

6. Nos movemos a la carpeta `react`

```bash 
cd react
```

7. Dentro de  `react` creamos las carpetas `public` y `src`, estas son carpetas típicas en cualquier proyecto Web. 

```bash
mkdir public
mkdir src
```

8. Crear archivo `index.html`

``` bash
touch public/index.html
```

9. Crear archivo `README.md`

```bash
touch README.md
```

10 . Crear archivo `.gitignore`

```bash
touch .gitignore
```

11. Iniciamos `git` local en nuestro proyecto.

```bash
git init
#Initialized empty Git repository in ~tu_user/Documents/courses_notes/react/.git/

```

12. Iniciamos `npm`

```bash
npm init -y
```

Al finalizar debemos tener nuestro archivo `package.json` debes tener algo parecido a esto (no lo mismo- solo parecido)

```json
{
  "name": "react_topics",
  "version": "1.0.0",
  "description": "React topics in linkedin course 2021",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [
    "react",
    "ecosystem",
    "project",
    "redux",
    "reselect",
    "style"
  ],
  "author": "tu",
  "license": "MIT"
}
```



13. Agregamos todos nuestros cambios a `git`

```bash
git add .
```

14. Agregamos todos nuestros a cambios a un `commit`

```bash
git commit -m "Init commit - tu nombre - tu numero"
```

13. Instalamos [`Github CLI`](https://cli.github.com/) en nuestra `PC`. Si usas Windows descarga el [instalador](https://github.com/cli/cli/releases/download/v1.12.1/gh_1.12.1_windows_amd64.msi) 

    Nota: Esta es una herramienta para manipular `GitHub` desde nuestro [terminal de forma local](https://www.youtube.com/watch?v=tm9gdHd9qmE) puedes ver este vídeo con los subtitulo para saber como instalarlo. 

14. Cuando tengas instalado GitHub CLI

```bash
gh repo create
```

Nota esto te va pedir un conjunto de confirmaciones que puedes saltar simplemente dando `enter`, pero te recomiendo que pruebes y leas las opciones. 

15. Subimos nuestros cambios al `repo` remoto creado con `GitHub CLI`.

```bash
git push -u origin main
```

Si todo esta bien deberá pedirte tu usuario y contraseña a `Github` o subir los archivos al nuevo repositorio remoto. Puedes dirigirte a la plataforma y buscar el nuevo repositorio creado, debe contener lo mismo que nuestro repositorio local. 

# Creando nuestro documento .`html` 

Todo proyecto `React`  necesita un documento .`html`  para poder manipular un `DOM` real. 

En el documento `index.html` creado en el paso `8` realizamos las siguientes modificaciones.

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>React ecosystem topics </title>
</head>

<body>
    <div id="root">
        <!--
            Todo nuestro codigo con React se ejecutara dentro de este div. 
            React constantemente modificara la apariencia del DOM en este elemento.
            El id="root" es considerado por React como su punto de entrada.
        -->
    </div>
    <noscript>
        Por favor habilita JavaScript para ver este sitio.
        Please enable JavaScript to view this site.
    </noscript>
    <script src="../dist/bundle.js">
        // dist/bundle.js es un archivo de produccion para desplegar nuestra app al publico. 
    </script>

</body>

</html>
```

## Instalando `babel`  en modo `dev`

Antes de instalar `babel` vamos a excluir la carpeta `node_modules` de nuestro control de versiones. Para esto modificaremos nuestro archivo `.gitignore` agregándole la linea `node_modules/`.

Dentro de `.gitignore` editamos con `VSC`. 

```
node_modules/
package-lock.json
```

O podemos usar un comando de terminal 

```bash 
echo "node_modules/\npackage-lock.json" > .gitignore
```

Instalamos babel  como herramienta de desarrollo:

```bash
npm install --save-dev @babel/core @babel/cli @babel/preset-env @babel/preset-react
```

Notaremos que al terminal de ejecutar si no presenta ningún error, se deben crear la carpeta `node_modules` y el archivo `packag-lock.json`

Dentro de nuestro `package.json` ocurren ciertas modificaciones de forma automática, estas modificaciones nos informan de los nuevos paquetes instalados en nuestro proyecto. Los `...`  indican que se mantiene igual. 

```json
{
  "name": "react_topics",
  
    ...,
  
  "author": "tu",
  "license": "MIT",
  "devDependencies": {
    "@babel/cli": "^7.14.5",
    "@babel/core": "^7.14.6",
    "@babel/preset-env": "^7.14.7",
    "@babel/preset-react": "^7.14.5"
  }
}

```

Creando `.babelrc`

```bash
touch .babelrc
```

Agrega al archivo el siguiente texto en `JSON`

```json
{
	"presets": ["@babel/preset-env", "@babel/preset-react"]
}
```

Esta configuración no permite usar `React` en diferentes navegadores, hasta algunos viejos. 

Confirmamos nuestros cambios y los subimos a `github`

```bash
git add .
git commit -m "Add babel config and packages"
git pull origin main
git push origin main
```

# Creando nuestra primera aplicación 

Crearemos los archivos siguientes:

```bash
touch src/index.js
touch src/App.js
touch src/App.css
```

Dentro de `App.js` agregaremos el siguiente código:

```js
import React from 'react';
import ',/App.css';

const App = () => {
    <div className="App">
        <h1>Hello, world!</h1>
    </div>
}

export default App;
```

Dentro de `App.css` agregamos el siguiente código:

``` css
.App {
    margin: 1rem;
    font-family: Arial, Helvetica, sans-serif;
    color: #222222;       
}
```

Dentro de `index.js` agregamos el siguiente código:

```js
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App.js';

ReactDOM.render(<App />, document.getElementById('root'));
```

Instalar los paquetes `react` y `react-dom`

```bash
npm install react react-dom
```

```bash
git add .
git commit -m "Add react and react-dom c packages"
git pull origin main
git push origin main
```

