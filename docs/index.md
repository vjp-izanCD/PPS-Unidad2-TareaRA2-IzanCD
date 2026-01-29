# Tarea Unidad 2 - Determinación del Nivel de Seguridad Requerido por las Aplicaciones

Bienvenido a la documentación de la **Tarea Obligatoria Unidad 2 RA2** del módulo de **Puesta en Producción Segura**.

## Información General

**Autor**: Izan Correa Díaz  
**Módulo**: Puesta en Producción Segura  
**Unidad**: 2 - Determinación del Nivel de Seguridad Requerido por las Aplicaciones  
**Fecha**: Enero 2026

## Objetivos de la Tarea

Esta tarea tiene como objetivo principal demostrar las competencias en:

- Trazado de vulnerabilidades utilizando fuentes abiertas (CVE, NVD, CWE, CAPEC)
- Análisis de vulnerabilidades en aplicaciones web (bWAPP - SQL Injection)
- Verificación de requisitos de seguridad mediante OWASP ASVS
- Evaluación y comparación de riesgos de seguridad según contexto de aplicación
- Aplicación de metodologías de seguridad para diferentes tipos de aplicaciones

## Estructura de la Documentación

La documentación está organizada en cuatro apartados principales:

### 🔍 Apartado 1: Trazado de Vulnerabilidad CVE-2024-0204

Trazado completo de la vulnerabilidad crítica en GoAnywhere MFT, siguiendo el flujo desde el aviso de INCIBE hasta las bases de datos CVE, NVD, CWE y CAPEC. Incluye:

- Identificación de la vulnerabilidad (CVE-2024-0204)
- Análisis de severidad (CVSS 9.8 - CRÍTICA)
- Debilidad asociada (CWE-425 - Direct Request Forced Browsing)
- Vector de explotación y mitigaciones

**Archivo**: `U2-RA2-T1/Trazado-de-una-vulnerabilidad-Izan-Correa-Diaz.md`

### 🛡️ Apartado 2: Análisis de Vulnerabilidad SQL Injection en bWAPP

Análisis detallado de cómo funciona la vulnerabilidad de inyección SQL en la aplicación bWAPP, incluyendo:

- Entrada de datos del usuario sin validación
- Construcción insegura de consultas SQL por concatenación
- Niveles de seguridad (0, 1, 2) y sus limitaciones
- Problemas detectados y recomendaciones de producción segura

**Archivo**: `U2-RA2-T2/analisisVulnerabilidad-IzanCorreaDiaz.md`

### ✅ Apartado 3: Comprobación de Requisitos ASVS

Verificación de requisitos de seguridad de una aplicación Python (SKF Requirements Tool) utilizando OWASP ASVS Nivel 1:

- Justificación del nivel de seguridad requerido (ASVS Nivel 1)
- Evaluación de validación de entrada y código malicioso
- Hoja de cálculo ASVS con requisitos verificados
- Análisis del grado de cobertura de seguridad
- Herramientas automáticas de verificación (Bandit, OWASP ZAP, SonarQube)

**Archivo**: `U2-RA2-T3/ComprobacionRequisitosAplicacion-IzanCorreaDiaz.md`

### 📊 Apartado 4: Reflexión sobre Riesgos de Aplicaciones

Reflexion personal sobre cómo los riesgos de seguridad varían según el tipo de aplicación y su contexto:

- Comparación de riesgos: Aplicación Educativa vs Bancaria vs Salud vs Redes Sociales
- Matriz comparativa de riesgos por tipo de aplicación
- Riesgos comunes vs riesgos específicos
- Aplicación de OWASP ASVS según contexto
- Conclusión: "La seguridad no es absoluta, es contextual"

**Archivo**: `U2-RA2-T4/ReflexiónRiesgosAplicaciones-IzanCorreaDiaz.md`

## Marco de Trabajo Utilizado

### OWASP ASVS (Application Security Verification Standard)

Marco de referencia para verificar requisitos de seguridad en aplicaciones:

- **Nivel 1**: Aplicaciones de bajo riesgo (entornos controlados, datos no críticos)
- **Nivel 2**: Aplicaciones de riesgo moderado (acceso público, datos personales)
- **Nivel 3**: Aplicaciones de alto riesgo (datos muy sensibles, impacto crítico)

### Fuentes de Información sobre Vulnerabilidades

- **CVE.org**: Lista de vulnerabilidades comunes (CVE Records)
- **NVD (NIST)**: Base de datos nacional de vulnerabilidades con métricas CVSS
- **CWE (MITRE)**: Lista de debilidades comunes en software
- **CAPEC (MITRE)**: Patrones de ataque comunes
- **INCIBE**: Avisos de seguridad y vulnerabilidades críticas

## Aplicaciones Analizadas

### 1. GoAnywhere MFT (CVE-2024-0204)

Aplicación de transferencia gestionada de archivos con vulnerabilidad crítica de omisión de autenticación.

### 2. bWAPP (Buggy Web Application)

Aplicación web deliberadamente insegura para prácticas de seguridad, utilizada para analizar SQL Injection.

### 3. SKF Requirements Tool

Aplicación Python Flask educativa evaluada con OWASP ASVS Nivel 1.

## Tecnologías y Herramientas Utilizadas

- **Lenguajes**: Python, PHP
- **Frameworks**: Flask, bWAPP
- **Contenedores**: Docker, Docker Compose
- **Herramientas de Seguridad**: 
  - OWASP ASVS Checklist
  - Bandit (análisis estático Python)
  - OWASP ZAP (pruebas de penetración web)
  - SonarQube (calidad y seguridad de código)
- **Bases de Datos de Vulnerabilidades**: CVE, NVD, CWE, CAPEC
- **Entorno de Pruebas**: Kali Linux

## Conceptos Clave Aprendidos

### Severidad de Vulnerabilidades (CVSS)

- **CRÍTICA (9.0-10.0)**: Impacto máximo, explotación sencilla
- **ALTA (7.0-8.9)**: Impacto significativo
- **MEDIA (4.0-6.9)**: Impacto moderado
- **BAJA (0.1-3.9)**: Impacto mínimo

### Tipos de Inyección
- **SQL Injection**: Inyección de código SQL en consultas
- **XSS (Cross-Site Scripting)**: Inyección de scripts maliciosos
- **Command Injection**: Inyección de comandos del sistema

### Principios de Seguridad

1. **Validación de Entrada**: Nunca confíar en datos del usuario
2. **Consultas Preparadas**: Usar binding de parámetros, no concatenación
3. **Principio de Mínimo Privilegio**: Otorgar solo permisos necesarios
4. **Defensa en Profundidad**: Múltiples capas de seguridad
5. **Seguridad por Diseño**: Incorporar seguridad desde el inicio

## Enlaces Rápidos

- [Repositorio en GitHub](https://github.com/vjp-izanCD/PPS-Unidad2-TareaRA2-IzanCD)
- [OWASP ASVS](https://owasp.org/www-project-application-security-verification-standard/)
- [CVE.org](https://www.cve.org/)
- [NVD - NIST](https://nvd.nist.gov/)
- [CWE - MITRE](https://cwe.mitre.org/)
- [INCIBE](https://www.incibe.es/)

## Navegación por los Apartados

### 📂 Documentación Completa

1. **[Trazado de Vulnerabilidad CVE-2024-0204](U2-RA2-T1/TrazadoVulnerabilidadGoAnywhere-IzanCorreaDiaz.md)**  
   _Trazado completo de vulnerabilidad crítica en GoAnywhere MFT_

2. **[Análisis de Vulnerabilidad SQL Injection en bWAPP](U2-RA2-T2/AnalisisVulnerabilidad-IzanCorreaDiaz.md)**  
   _Análisis detallado de inyección SQL y niveles de seguridad_

3. **[Comprobación de Requisitos de Seguridad ASVS](U2-RA2-T3/ComprobacionRequisitosAplicacion-IzanCorreaDiaz.md)**  
   _Verificación OWASP ASVS Nivel 1 de aplicación Python_

4. **[Reflexión sobre Riesgos de Aplicaciones](U2-RA2-T4/ReflexiónRiesgosAplicaciones-IzanCorreaDiaz.md)**  
   _Comparación de riesgos según contexto de aplicación_

---

## Conclusiones Generales

A lo largo de esta unidad se ha trabajado con:

✅ **Identificación y trazado de vulnerabilidades** en fuentes abiertas  
✅ **Análisis práctico** de vulnerabilidades comunes (SQL Injection)  
✅ **Verificación sistemática** de requisitos de seguridad con ASVS  
✅ **Evaluación contextual** de riesgos según tipo de aplicación  
✅ **Aplicación de mejores prácticas** de desarrollo seguro

La seguridad en aplicaciones no es un concepto absoluto, sino que debe adaptarse al **contexto**, **tipo de datos** y **nivel de exposición** de cada aplicación.

---

**Última actualización**: 29 de enero de 2026  
**Contacto**: Izan Correa Díaz - IES Virgen del Puerto - Plasencia, Extremadura
