# Proyecto de CV

## proyecto web usando react y taildwind

### 1 Configuración del proyecto

* Asegúrate de tener Node.jsy npm instalados en tu computadora.

* Crea un nuevo proyecto de Vite con React:

```js
Bash

npm create vite@latest mi-sitio-personal --template react
cd mi-sitio-personal
npm install

```

### 2 Instalar Taildwind CSS

* Instala Tailwind CSS y sus dependencias:

```js
Bash

npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p

```

### 3 Configurar Tailwind CSS

* Abre el archivo tailwind.config.js y añade las rutas de tus archivos de React

```javascript
  javascript

  module.exports = {
  content: [
    "./index.html",
    "./src/**/*.{js,jsx,ts,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}

```

* Crea un archivo src/index.css y añade las directivas de Tailwind CSS:
  
```css
  CSS

@tailwind base;
@tailwind components;
@tailwind utilities;

```

* Importa index.css en tu archivo src/main.jsx

```json
  package.json

  import './index.css'

```

### 4 Crear las páginas

* Crea una carpeta src/pages y dentro de ella, crea tres archivos: Inicio.jsx, Curriculum.jsx y Fotos.jsx.

* En cada archivo, crea un componente básico de React. Por ejemplo, para Inicio.jsx:

```javascript
  javascript

  import React from 'react';

const Inicio = () => {
  return (
    <div className="container mx-auto p-4">
      <h1 className="text-4xl font-bold">Bienvenido a mi sitio web</h1>
      <p>Esta es la página de inicio.</p>
    </div>
  );
};

export default Inicio;

```

### 5 Configurar el enrutamiento

* Instala React Router

```js
Bash

npm install react-router-dom

```

* Configura las rutas en tu archivo src/App.jsx

```javascript
  javascript

  import React from 'react';
import { BrowserRouter, Route, Routes } from 'react-router-dom';
import Inicio from './pages/Inicio';
import Curriculum from './pages/Curriculum';
import Fotos from './pages/Fotos';

const App = () => {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Inicio />} />
        <Route path="/curriculum" element={<Curriculum />} />
        <Route path="/fotos" element={<Fotos />} />
      </Routes>
    </BrowserRouter>
  );
};

export default App;

```

### 6 Estilizar las páginas

* Usa las clases de Tailwind CSS para estilizar tus componentes. Por ejemplo, en Curriculum.jsx

```javascript
  javascript

  import React from 'react';

const Curriculum = () => {
  return (
    <div className="container mx-auto p-4">
      <h1 className="text-4xl font-bold">Mi Curriculum</h1>
      <p>Aquí puedes ver mi experiencia y habilidades.</p>
    </div>
  );
};

export default Curriculum;

```

---
---
---
