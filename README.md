# TP5 - Release Pipeline

Este proyecto implementa y despliega un conjunto de aplicaciones web (backend y frontend) en **Azure App Service**, utilizando **pipelines de CI/CD** para automatizar el proceso desde Azure DevOps.

---

## 🌐 Acceso a los servicios

### Entorno de QA
- **WebApp QA:**    ->   https://webqa-fqgnbwexh5dzgzca.canadacentral-01.azurewebsites.net 

### Entorno de Producción
- **WebApp PROD:**  ->   https://webprod-a8a2dagufte2etd3.canadacentral-01.azurewebsites.net/


---

## 🚀 Proceso de despliegue

1. **Desarrollo local:**  
   Los cambios se realizan en las ramas `main` del repositorio correspondiente.

2. **Integración continua (CI):**  
   Al realizar un **push** hacia la rama `main`, se ejecuta automáticamente el pipeline de Azure DevOps que:
   - Compila el código.
   - Construye front y back juntos 
   - Genera el artefacto de despliegue.

3. **Despliegue continuo (CD):**  
   - **Pipeline QA:** Despliega automáticamente en el entorno **QA** al hacer merge en `main`.  
   - **Pipeline PROD:** Se ejecuta **MANUALME** desde Azure DevOps (necesita aprobarse primero) desplegando a **Producción**.

<img width="850" height="165" alt="image" src="https://github.com/user-attachments/assets/90c07bef-4b03-4d75-8582-896436e61316" />


---

## ⚙️ Estructura de entornos en Azure

- **Resource Group:** `rgISW`
- **WebApps:**
  - `WebPROD`
  - `WebQA` 
- **Service Connections:** configuradas en Azure DevOps para ambos entornos.

  <img width="900" height="127" alt="image" src="https://github.com/user-attachments/assets/31c555ff-a92f-49ed-909d-d0637e2b67ad" />


---

## 🧩 Repositorio vinculado

- *https://dev.azure.com/santiagotricherri/Tricherri-Ojeda-Reyna/_git/Web_Node*

<img width="273" height="323" alt="image" src="https://github.com/user-attachments/assets/c8cab499-6dd7-4169-bfaf-4ab05f6709d2" />

---

## ✅ Verificación post-despliegue

1. Abrir las URLs de QA o PROD.  
2. Probar las operaciones del CRUD de usuarios.  
3. Confirmar que la API responde correctamente y los datos se persisten en la base de datos.

<img width="934" height="519" alt="image" src="https://github.com/user-attachments/assets/38eb09b2-75b2-4b78-95d6-fadca87cc7f2" />


---

