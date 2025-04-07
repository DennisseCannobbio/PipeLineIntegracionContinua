# Reporte de Implementación de Pipeline de CI

## Pasos Realizados

1. **Configuración inicial del repositorio:**

   - Inicialización del repositorio Git local
   - Creación del repositorio remoto en GitHub
   - Configuración del enlace entre ambos

2. **Configuración básica de la API:**

   - Verificación del funcionamiento correcto de la API con db.json
   - Creación de un servidor para ejecutar la API (server.js)
   - Configuración de scripts en package.json

3. **Automatización básica con Jenkins:**

   - Creación del Jenkinsfile
   - Configuración de etapas para clonar el repositorio
   - Configuración para instalar dependencias y verificar el funcionamiento

4. **Ejecución de pruebas automatizadas:**

   - Modificación del pipeline para ejecutar pruebas
   - Configuración para detener la ejecución si las pruebas fallan

5. **Reporte y retroalimentación:**
   - Configuración para generar reportes de pruebas
   - Documentación del proceso

## Problemas Encontrados y Soluciones

- **Problema 1:** El pipeline no funcionaba debido a que no encontraba los archivos de reporte.
  **Solución:** Faltó instalar en el proyecto las dependencias necesarias (jest-junit).
