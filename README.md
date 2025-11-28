# Instalación y Configuración de ESLint

## Instalación

### 1. Instalar ESLint con Angular

Reemplaza `18` por tu versión actual de Angular:

```bash
ng add @angular-eslint/schematics@18
```

### 2. Instalar dependencias de Prettier y ESLint

```bash
npm install prettier prettier-eslint eslint-config-prettier eslint-plugin-prettier typescript-eslint eslint-plugin-import eslint-plugin-unused-imports --save-dev
```

## Configuración

### 1. Copiar archivos de configuración

Copia los siguientes archivos al directorio raíz del proyecto:

- `.prettierrc` (configuración de Prettier)
- `.prettierignore` (archivos a ignorar por Prettier)
- `eslint.config.js` (configuración de ESLint - más completo que el generado automáticamente)

### 2. Agregar script de Prettier al package.json

Añade el siguiente script en la sección `"scripts"` del archivo `package.json`:

```json
"prettier": "npx prettier --write ."
```

**Ejemplo de package.json:**

```json
{
  "scripts": {
    "ng": "ng",
    "start": "ng serve",
    "build": "ng build",
    "watch": "ng build --watch --configuration development",
    "test": "ng test",
    "prettier": "npx prettier --write ."
  }
}
```

## Uso

Una vez configurado, puedes ejecutar:

- **Formatear código con Prettier:**

  ```bash
  npm run prettier
  ```

- **Verificar linting con ESLint:**
  ```bash
  ng lint
  ```

## Notas

- La configuración `eslint.config.js` incluida en el raíz contiene settings más completos que los generados automáticamente por Angular.
- Asegúrate de que tanto `prettier` como `eslint-plugin-prettier` estén correctamente instalados para que funcione la integración.
