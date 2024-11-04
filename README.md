# Tutorial para trabajar con Typescript en Nodejs 

### **1. Instala Node.js y npm**

- Asegúrate de tener instalado [Node.js](https://nodejs.org) en tu sistema, lo cual también incluye npm (Node Package Manager).

### **2. Crea una carpeta para tu proyecto**

- En tu terminal, navega al directorio donde deseas crear tu proyecto y ejecuta:
  ```bash
  mkdir mi-proyecto-backend
  cd mi-proyecto-backend
  ```

### **3. Inicializa un proyecto npm**

- Crea un `package.json` básico:
  ```bash
  npm init -y
  ```

### **4. Instala TypeScript y otras dependencias de desarrollo**

- Instala TypeScript, ts-node y los tipos para Node.js:
  ```bash
  npm install typescript ts-node @types/node --save-dev
  ```

### **5. Inicializa la configuración de TypeScript**

- Crea un archivo `tsconfig.json` con la configuración predeterminada:
  ```bash
  npx tsc --init
  ```

### **6. Configura el archivo tsconfig.json**

- Abre `tsconfig.json` y ajusta las opciones necesarias. Aquí hay una configuración recomendada:
  ```json
  {
    "compilerOptions": {
      "target": "ES6",
      "module": "CommonJS",
      "outDir": "./dist",
      "rootDir": "./src",
      "strict": true,
      "esModuleInterop": true
    },
    "include": ["src"],
    "exclude": ["node_modules"]
  }
  ```

### **7. Crea la estructura de carpetas**

- Crea una carpeta `src` para tus archivos TypeScript:
  ```bash
  mkdir src
  ```

### **8. Instala Express y sus definiciones de tipos (opcional)**

- Si planeas usar Express.js:
  ```bash
  npm install express
  npm install @types/express --save-dev
  ```

### **9. Escribe tu código en TypeScript**

- Crea un archivo `src/index.ts` y agrega el siguiente código de ejemplo:
  ```typescript
  import express from 'express';

  const app = express();
  const port = 3000;

  app.get('/', (req, res) => {
    res.send('¡Hola, mundo!');
  });

  app.listen(port, () => {
    console.log(`Servidor escuchando en http://localhost:${port}`);
  });
  ```

### **10. Compila y ejecuta tu proyecto**

- **Opción 1: Usando ts-node (ideal para desarrollo)**
  ```bash
  npx ts-node src/index.ts
  ```
- **Opción 2: Compilando a JavaScript y ejecutando con Node.js**
  - Compila el código TypeScript:
    ```bash
    npx tsc
    ```
  - Ejecuta el código compilado:
    ```bash
    node dist/index.js
    ```

### **11. Agrega scripts a tu package.json**

- Para facilitar el desarrollo, añade scripts en tu `package.json`:
  ```json
  "scripts": {
    "build": "tsc",
    "start": "node dist/index.js",
    "dev": "ts-node src/index.ts"
  }
  ```
- Ahora puedes usar:
  - `npm run dev` para ejecutar en modo desarrollo.
  - `npm run build` para compilar.
  - `npm start` para ejecutar el código compilado.

### **12. Configura Nodemon para recarga automática (opcional)**

- Instala Nodemon como dependencia de desarrollo:
  ```bash
  npm install nodemon --save-dev
  ```
- Actualiza el script de desarrollo en `package.json`:
  ```json
  "scripts": {
    "dev": "nodemon --watch 'src/**/*.ts' --exec 'ts-node' src/index.ts"
  }
  ```
- Ejecuta tu proyecto en modo desarrollo con recarga automática:
  ```bash
  npm run dev
  ```

### **13. Considera herramientas adicionales**

- **ESLint y Prettier** para mantener un código limpio y consistente:
  ```bash
  npm install eslint prettier eslint-config-prettier eslint-plugin-prettier --save-dev
  ```
- **Configuración de ESLint**:
  - Inicializa ESLint:
    ```bash
    npx eslint --init
    ```
  - Selecciona las opciones apropiadas para TypeScript.

### **14. Implementa pruebas unitarias (opcional)**

- Si deseas agregar pruebas a tu proyecto, puedes usar Jest:
  ```bash
  npm install jest ts-jest @types/jest --save-dev
  ```
- Configura Jest para TypeScript:
  ```bash
  npx ts-jest config:init
  ```

### **15. Recursos adicionales**

- **Documentación oficial de TypeScript**: [typescriptlang.org](https://www.typescriptlang.org/docs/)
- **Guía de Express.js con TypeScript**: [Express & TypeScript](https://expressjs.com/en/advanced/best-practice-security.html)
