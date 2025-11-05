# decisiones.md

## 🧩 Introducción
En este trabajo implementamos el despliegue de una aplicación completa en **Azure**, utilizando **Azure DevOps** para automatizar la integración y entrega continua (CI/CD).  
El objetivo fue poner en práctica los conceptos de pipelines, entornos y despliegues reales en la nube.

---

## ⚙️ Estructura de la aplicación
Nuestra aplicación está compuesta por un **CRUD de usuarios**, desarrollado con un **backend** y un **frontend** conectados a una base de datos **MongoDB**.  
El backend expone las operaciones de creación, lectura, actualización y eliminación de usuarios, mientras que el frontend permite interactuar con dichas funciones de forma visual.

---

## ☁️ Creación de recursos en Azure
Desde el **Azure Portal** creamos los siguientes recursos:
- **Dos WebApps** para cada entorno: `backend-qa`, `frontend-qa`, `backend-prod`, `frontend-prod`.
- **Base de datos MongoDB** alojada en un servicio externo.
- **Service Connection** en Azure DevOps para permitir la autenticación y despliegue directo desde los pipelines hacia las WebApps.

Cada recurso fue agrupado dentro del mismo **Resource Group**, facilitando la administración y monitoreo.

---

## 🔄 Desarrollo del pipeline
El pipeline de Azure DevOps fue diseñado con tres etapas principales:

1. **Build:** compila la aplicación, instala dependencias y genera los artefactos.  
2. **Deploy QA:** despliega automáticamente en el entorno de pruebas al hacer merge en `main`.  
3. **Deploy PROD:** despliega en producción tras una **aprobación manual** desde Azure DevOps.

Este flujo garantiza control y trazabilidad sobre los cambios antes de su publicación final.

---

## 🔐 Variables y configuración por entorno
Se configuraron **variables secretas** (como cadenas de conexión y claves) en el panel de **Library → Variable groups** de Azure DevOps, para mantener la seguridad.  
Además, cada WebApp tiene sus propias **App Settings**, lo que permitió definir configuraciones distintas para QA y Producción (por ejemplo, URLs del backend, conexiones o claves privadas).

---

## 🧰 Resolución de errores con Kudu
Durante el desarrollo encontramos errores en los despliegues, especialmente al ejecutar `npm ci` y al detectar respuestas incorrectas en el frontend.  
Utilizamos la herramienta **Kudu (Advanced Tools)** dentro de cada WebApp para inspeccionar logs, revisar archivos desplegados y ejecutar comandos, lo que nos permitió identificar y resolver los problemas del proceso de publicación.

---

## 🤖 Apoyo de la Inteligencia Artificial
A lo largo del trabajo, la **IA** nos ayudó a comprender conceptos de CI/CD, pipelines y configuración de servicios en Azure.  
También fue clave para **proponer alternativas de solución** ante los errores de despliegue y optimizar la estructura general del proyecto.

---

**Autores:**  
- Santiago Tricherri  
- Dante Ojeda

