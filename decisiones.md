# Decisiones del TP5

## 🧩 Introducción
En este trabajo implementamos el despliegue de una aplicación completa en **Azure**, utilizando **Azure DevOps** para automatizar la integración y entrega continua (CI/CD).  
El objetivo fue poner en práctica los conceptos de pipelines, entornos y despliegues reales en la nube.

---

## ⚙️ Estructura de la aplicación
Nuestra aplicación está compuesta por un **CRUD de usuarios**, desarrollado con un **backend** y un **frontend** conectados a una base de datos **MongoDB**.  
El backend expone las operaciones de creación y lectura de usuarios (Proximamente: actualización y eliminación) mientras que el frontend permite interactuar con dichas funciones de forma visual.
Cada entorno responde a su propia base de datos, por lo que son independientes una de la otra.

<img width="302" height="197" alt="image" src="https://github.com/user-attachments/assets/e6c29391-1803-4cf1-8414-2a8d1e7b3792" />


---

## ☁️ Creación de recursos en Azure
Desde el **Azure Portal** creamos los siguientes recursos:
- **Dos WebApps** para cada entorno: `PROD`y `QA`
- **Base de datos MongoDB** alojada en un servicio externo.
- **Service Connection** en Azure DevOps para permitir la autenticación y despliegue directo desde los pipelines hacia las WebApps.

Cada recurso fue agrupado dentro del mismo **Resource Group**, facilitando la administración y monitoreo.

<img width="419" height="737" alt="image" src="https://github.com/user-attachments/assets/8f7765d6-590d-43c0-a62f-a2e7532d475a" />

---

## 🔄 Desarrollo del pipeline
El pipeline de Azure DevOps fue diseñado con tres etapas principales:

1. **Build:** compila la aplicación, instala dependencias y genera los artefactos.  
2. **Deploy QA:** despliega automáticamente en el entorno de pruebas al hacer merge en `main`.  
3. **Deploy PROD:** despliega en producción tras una **aprobación manual** desde Azure DevOps.

<img width="908" height="320" alt="image" src="https://github.com/user-attachments/assets/fd7f4a84-84af-487e-b8ee-6b0e135bd78f" />


Este flujo garantiza control y trazabilidad sobre los cambios antes de su publicación final.

---

## 🔐 Variables y configuración por entorno
Se configuraron **variables secretas** (como cadenas de conexión y claves) en el panel de **Library → Variable groups** de Azure DevOps, para mantener la seguridad.  
Además, cada WebApp tiene sus propias **App Settings**, lo que permitió definir configuraciones distintas para QA y Producción (por ejemplo, URLs del backend, conexiones o claves privadas).

<img width="1064" height="600" alt="image" src="https://github.com/user-attachments/assets/a0eb5406-2f5f-4908-8816-a2bd04c8192d" />

-

<img width="776" height="628" alt="image" src="https://github.com/user-attachments/assets/2a794a07-0c8d-4ca8-84cc-f16be96983b2" />

Las variables de las app settings tambien las incluimos en el azure-pipeline.yml por las dudas, pero no harían falta.

---

## 🧰 Resolución de errores con Kudu
Durante el desarrollo encontramos errores en los despliegues y al detectar respuestas incorrectas en el frontend.  
Utilizamos la herramienta **Kudu (Advanced Tools)** dentro de cada WebApp para inspeccionar logs, revisar archivos desplegados y ejecutar comandos, lo que nos permitió identificar y resolver los problemas durante el proceso.


<img width="1316" height="370" alt="image" src="https://github.com/user-attachments/assets/396aacdf-9652-4276-84b5-e357e7540abd" />


---

## 🤖 Apoyo de la Inteligencia Artificial
A lo largo del trabajo, la **IA** nos ayudó a comprender conceptos de CI/CD, pipelines y configuración de servicios en Azure.  
También fue clave para **proponer alternativas de solución** ante los errores de despliegue y optimizar la estructura general del proyecto.

