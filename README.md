# Práctica 3 — Configuración Básica de Pipeline CI/CD
**Electiva 1 — DevOps | ITLA 2026-C-3**

## 1. Descripción del proyecto
Este proyecto consiste en una aplicación web de gestión de tareas desarrollada con Node.js y Express. Su propósito es practicar la configuración de un pipeline de Integración Continua y Entrega Continua (CI/CD) utilizando GitHub Actions.

El proyecto incluye una API REST, una interfaz web estática, pruebas automatizadas con Jest y Supertest, y un contenedor Docker.

## 2. Tecnologías utilizadas
- Node.js 20+
- Express
- Jest
- Supertest
- Git y GitHub
- GitHub Actions
- Docker
- GitHub Pages

## 3. Estructura del proyecto
- `src/app.js`: configuración de la API y sus endpoints.
- `src/server.js`: inicio del servidor.
- `public/index.html`: interfaz web.
- `tests/app.test.js`: pruebas automatizadas.
- `Dockerfile`: configuración de la imagen Docker.
- `.github/workflows/ci.yml`: configuración del pipeline CI/CD.

## 4. Instalación y ejecución
Para instalar las dependencias:
```bash
npm install
```

Para ejecutar las pruebas:
```bash
npm test
```

Para iniciar la aplicación:
```bash
npm start
```

La aplicación estará disponible en:
[http://localhost:3000](http://localhost:3000)

## 5. Endpoints de la API

| Método | Endpoint | Descripción |
| :--- | :--- | :--- |
| **GET** | `/health` | Verifica el estado de la aplicación. |
| **GET** | `/metrics` | Consulta métricas de la aplicación. |
| **GET** | `/api/tareas` | Lista las tareas. |
| **POST** | `/api/tareas` | Crea una tarea. |
| **PATCH** | `/api/tareas/:id` | Cambia el estado de una tarea. |
| **DELETE** | `/api/tareas/:id` | Elimina una tarea por su identificador. |

## 6. Nueva funcionalidad implementada
Se agregó el endpoint:
`DELETE /api/tareas/:id`

Esta funcionalidad permite eliminar una tarea mediante su identificador.
- Si la tarea existe, devuelve el código HTTP `200` y un mensaje de confirmación.
- Si la tarea no existe, devuelve el código HTTP `404` y un mensaje de error.

## 7. Pruebas automatizadas
Se agregaron dos pruebas nuevas:
1. **Eliminar una tarea**: verifica que una tarea se elimine correctamente y que deje de aparecer en la lista.
2. **Eliminar una tarea inexistente**: verifica que el sistema responda con el código `404` cuando se intenta eliminar una tarea que no existe.

### Resultados obtenidos
La ejecución de `npm test` produjo los siguientes resultados:

| Indicador | Resultado |
| :--- | :--- |
| Suites aprobadas | 1 |
| Suites fallidas | 0 |
| Pruebas aprobadas | 8 |
| Pruebas fallidas | 0 |
| Cobertura de instrucciones | 95.55 % |
| Cobertura de ramas | 85.71 % |
| Cobertura de funciones | 100 % |
| Cobertura de líneas | 100 % |

## 8. Explicación de las etapas del pipeline CI/CD
El pipeline se encuentra configurado en `.github/workflows/ci.yml` y utiliza GitHub Actions. Sus etapas son:

1. **Checkout**: obtiene el código fuente del repositorio para iniciar el proceso.
2. **Setup Node.js**: configura el entorno de ejecución con Node.js.
3. **Instalación de dependencias**: instala los paquetes necesarios mediante `npm ci`.
4. **Lint**: ejecuta la etapa de validación estática configurada en el workflow.
5. **Pruebas automatizadas**: ejecuta Jest y genera el reporte de cobertura.
6. **Construcción Docker**: construye la imagen de la aplicación utilizando el `Dockerfile`.
7. **Despliegue a GitHub Pages**: publica el contenido estático del proyecto mediante GitHub Actions.

## 9. Comprobación del pipeline
Se realizaron dos comprobaciones:

- **Ejecución fallida (rojo)**:
Se modificó intencionalmente una expectativa de una prueba, cambiando el código HTTP esperado de `200` a `201`. Como la API devuelve `200`, la prueba falló y GitHub Actions mostró una ejecución fallida.

- **Ejecución exitosa (verde)**:
Se corrigió la expectativa, restaurando el código HTTP `200`. Después se ejecutaron nuevamente las pruebas y se publicó la corrección en GitHub. El pipeline terminó satisfactoriamente.

## 10. Repositorio GitHub
El proyecto se encuentra publicado en el siguiente repositorio:
🔗 [https://github.com/Jason-0525/practica-3-devops-itla](https://github.com/Jason-0525/practica-3-devops-itla)
**Rama principal:** `main`

## 11. Conclusión
La práctica permitió implementar una funcionalidad adicional en una API REST, ampliar las pruebas automatizadas y configurar un pipeline CI/CD utilizando GitHub Actions. 

Se comprobó el funcionamiento del proceso mediante una ejecución fallida intencional y una ejecución exitosa posterior. Finalmente, se obtuvieron ocho pruebas aprobadas y una cobertura de líneas del 100 %. 

Esta experiencia permitió comprender la importancia de la automatización, las pruebas y el control de versiones dentro de un proceso DevOps.