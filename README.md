# Pipelines de Azure DevOps – NequiDev

Este repositorio contiene los principales pipelines de Azure DevOps utilizados para automatizar el ciclo de vida de aplicaciones backend en el ecosistema NequiDev. Cada pipeline cumple una función específica dentro de la integración continua (CI) y entrega continua (CD), cubriendo desde la construcción de imágenes y el análisis de calidad del código, hasta el escaneo de seguridad y el despliegue en ambientes de contenedores.

---

## Estructura de los Pipelines

| Pipeline (YAML)                      | Propósito Principal                                                                    |
| ------------------------------------- | ---------------------------------------------------------------------------           |
| `devops-pipelines-dev-nequidev.yml`   | Orquestador general. Ejecuta los stages que integran los demás pipelines.             |
| `build_push_backend.yml`              | Construcción y push de la imagen Docker del backend a Azure Container Registry (ACR). |
| `sonar_cloud_py.yml`                  | Análisis de calidad y cobertura de código con SonarCloud.                             |
| `owasp_Initial_py.yml`                | Escaneo inicial de seguridad usando herramientas OWASP (SCA, SAST, etc.).             |
| `owasp_final.yml`                     | Escaneo de seguridad final, posterior al build de la imagen.                          |
| `deploy_app_container.yml`            | Despliegue automatizado de la aplicación en Kubernetes o Azure Container Apps.        |

---

## Flujo de Trabajo

1. **Construcción y Push:**  
   El pipeline `build_push_backend.yml` construye la imagen del backend y la publica en el ACR.

2. **Análisis de Calidad:**  
   El pipeline `sonar_cloud_py.yml` realiza análisis de calidad, asegurando buenas prácticas y cobertura en SonarCloud.

3. **Escaneo de Seguridad:**  
   - **Inicial:** `owasp_Initial_py.yml` ejecuta controles de seguridad antes del build (análisis de dependencias y código).
   - **Final:** `owasp_final.yml` realiza una verificación posterior al build, garantizando la ausencia de vulnerabilidades conocidas.

4. **Despliegue:**  
   `deploy_app_container.yml` despliega automáticamente la aplicación usando la imagen más reciente en Kubernetes o Azure Container Apps.

5. **Orquestación General:**  
   El pipeline principal (`devops-pipelines-dev-nequidev.yml`) orquesta todos los pasos anteriores, permitiendo un flujo CI/CD completo, seguro y automatizado.

---

## Tecnologías y Herramientas

- **Azure DevOps Pipelines**
- **Docker & Azure Container Registry (ACR)**
- **Kubernetes / Azure Container Apps**
- **SonarCloud** (análisis de calidad y cobertura)
- **OWASP Dependency Check / SAST** (seguridad y análisis estático)
- **Python** (proyectos backend)

---

## Beneficios

- **Automatización de extremo a extremo**: desde el commit hasta el despliegue.
- **Detección temprana** de errores y vulnerabilidades.
- **Despliegue seguro y repetible** en ambientes de contenedores.
- **Alineamiento con buenas prácticas de DevSecOps.**

---

> Para cualquier consulta o mejora sobre estos pipelines, por favor abre un issue o contacta al equipo de DevOps.
