# ✨ Guía Alegre de ESLint + Prettier para Angular

¡Bienvenido! Esta guía te ayudará a tener un código ordenado, bonito y feliz en tu proyecto Angular. Con Prettier para el estilo y ESLint para la calidad, ¡tu código brillará! 🌈

## 🚀 Instalación

### 1) Añade soporte ESLint para Angular
Reemplaza `18` por tu versión actual de Angular:

```bash
ng add @angular-eslint/schematics@18
```

### 2) Instala dependencias de Prettier y ESLint

```bash
npm install prettier prettier-eslint eslint-config-prettier eslint-plugin-prettier typescript-eslint eslint-plugin-import eslint-plugin-unused-imports --save-dev
```

## 🛠 Configuración

### Copia los archivos de configuración
Coloca en el raíz del proyecto:

- `.prettierrc` → reglas de estilo (comillas, ancho de línea, etc.)
- `.prettierignore` → archivos que Prettier no debe tocar
### ⚙️ Configuración de VS Code (dos opciones)
Para que el guardado y pegado automaticen correcciones de ESLint/Prettier, añade estas preferencias en VS Code. Puedes hacerlo de dos maneras:

1) Configuración por proyecto (recomendado)
- Crea el archivo `.vscode/settings.json` en la raíz del proyecto.
- Copia este contenido:

```json
{
  "editor.formatOnPaste": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": "explicit",
    "source.fixAll": "explicit",
    "source.sortMembers": "explicit"
  }
}
```

2) Configuración global de VS Code
- Abre VS Code → File > Preferences > Settings.
- Usa el botón “Open Settings (JSON)” o busca “settings.json” y abre el archivo de usuario.
- Pega el mismo bloque JSON en el objeto raíz.

Notas:
- `source.fixAll.eslint: "explicit"` aplica las correcciones de ESLint al guardar cuando se ejecutan acciones de código.
- `source.fixAll` cubre correcciones de otros proveedores que soporten fixAll.
- `source.sortMembers` ordena automáticamente miembros (si tu extensión lo soporta).
- `eslint.config.js` → configuración completa de ESLint (más pulida que la generada por defecto)

Agrega este script para formatear fácilmente:

```json
"prettier": "npx prettier --write ."
```

Ejemplo de `package.json` (sección `scripts`):

```json
{
  "scripts": {
    "ng": "ng",
    "start": "ng serve",
    "build": "ng build",
    "watch": "ng build --watch --configuration development",
    "test": "ng test",
    "lint": "ng lint",
    "prettier": "npx prettier --write ."
  }
}
```

## 🎯 Uso rápido

- Formatear código con Prettier:

  ```bash
  npm run prettier
  ```

- Ejecutar el lint de Angular/ESLint:

  ```bash
  npm run lint
  ```

## 🧪 Reglas más flexibles… ¡solo en tests!

Para que escribir pruebas sea más cómodo, en `eslint.config.js` aplicamos reglas relajadas únicamente a archivos `*.spec.ts` y `*.test.ts`. Por ejemplo:

- Permitir `any` y patrones "unsafe" (útil para mocks y stubs)
- No exigir tipo de retorno explícito
- Permitir variables/parámetros no usados en escenarios de Given/When/Then
- Consola libre para depurar (`console.log` permitido)
- Imports extrínsecos sin quejarse

Estas reglas NO afectan al código de aplicación: solo a tus tests. Así puedes mantener código de producción estricto y pruebas ágiles. ✅

## 📎 Notas

- La configuración de `eslint.config.js` en este repo es más completa que la generada automáticamente por Angular.
- Asegúrate de tener instalados `prettier` y `eslint-plugin-prettier` para que la integración funcione bien.
- Si quieres aún más libertad en tests, puedes desactivar `prettier` en esa sección del config (`prettier/prettier: 'off'`).

---

¡Y listo! Disfruta un código limpio, consistente y feliz 🎉.
