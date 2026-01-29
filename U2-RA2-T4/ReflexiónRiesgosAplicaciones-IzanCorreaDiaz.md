# Apartado 4 - Reflexión sobre los Riesgos de las Aplicaciones

## Introducción

Después de haber analizado la aplicación desarrollada en Python (SKF Requirements Tool) evaluada con OWASP ASVS Nivel 1 y habiendo estudiado vulnerabilidades como SQL Injection en bWAPP, surge la necesidad de reflexionar sobre cómo los riesgos de seguridad varían significativamente en función de las características, el contexto de ejecución y el tipo de datos que maneja cada aplicación.

## 1. Riesgos de la Aplicación Educativa (ASVS Nivel 1)

La aplicación Python evaluada es un programa educativo ejecutado en un entorno controlado (aula, laboratorio o máquina local) con características muy específicas:

### Riesgos Identificados:

**Bajo riesgo externo:**
- No está expuesta a Internet
- Solo accesible en red local o localhost
- Usuarios conocidos y de confianza
- Datos de ejemplo, no datos reales

**Riesgos internos presentes:**
- Falta de cifrado de datos en reposo
- Ausencia de autenticación robusta
- Validación de entrada incompleta (especialmente en límites de rango y tamaño)
- No implementa mecanismos de registro y auditoría
- Carencia de protección contra acceso no autorizado a la base de datos

**Mitigación natural:**
El entorno controlado actúa como primera línea de defensa, reduciendo significativamente la probabilidad de explotación.

---

## 2. Comparativa de Riesgos por Tipo de Aplicación

### A. Aplicaciones Bancarias

**Contexto:**
- Acceso público directo desde Internet
- Manejo de datos críticos: saldos, transacciones, datos financieros
- Alto impacto económico en caso de compromiso
- Regulación estricta (PCI-DSS, normativas bancarias)

**Riesgos específicos (CRITICIDAD MÁXIMA):**
- **Robo de fondos directo**: Un ataque exitoso compromete dinero real
- **Ataques de phishing**: Suplantación de la entidad bancaria
- **Malware/Ransomware**: Bloqueo de acceso a cambio de rescate
- **Manipulación de datos**: Alteración de saldos o transacciones
- **Parálisis operacional**: Afecta servicios críticos para múltiples usuarios
- **Robo de identidad**: Acceso a datos personales de clientes

**Diferencias clave respecto a app educativa:**
```
App Educativa              →  App Bancaria
- Bajo volumen de datos   →  Millones de registros de clientes
- Usuarios internos        →  Acceso público sin restricción
- Impacto: Académico      →  Impacto: Económico y legal
- Sin regulación especial  →  Regulación exhaustiva
```

### B. Aplicaciones de Salud / Healthcare

**Contexto:**
- Manejo de datos sensibles: historial médico, diagnósticos, tratamientos
- Datos considerados de especial protección (GDPR, HIPAA)
- Impacto directo en la vida y seguridad de las personas

**Riesgos específicos (CRITICIDAD MÁXIMA):**
- **Filtración de datos médicos**: Exposición de condiciones de salud
- **Suplantación de pacientes**: Acceso a información médica ajena
- **Modificación de historiales**: Cambio de alergias, medicamentos, diagnósticos
- **Indisponibilidad de servicios**: Impacto en atención médica en tiempo real
- **Violación de privacidad**: Datos sensibles comprometen derechos fundamentales
- **Chantaje o extorsión**: Amenaza con revelar condiciones médicas

**Estadísticas reales (según búsqueda):**
- El 80% de las apps de salud Android no cumplen estándares de seguridad
- 50% compartía datos personales con terceros
- Más de 50% transmitía datos de salud sin cifrado (HTTP)
- Muchas no usaban conexiones seguras para contraseñas

### C. Aplicaciones de Redes Sociales

**Contexto:**
- Millones de usuarios conectados simultáneamente
- Datos personales: fotos, ubicación, contactos, preferencias
- Modelo de negocio basado en monetización de datos

**Riesgos específicos (CRITICIDAD ALTA):**
- **Robo de credenciales**: Acceso a múltiples cuentas conectadas
- **Suplantación de identidad**: Uso de cuenta para difundir información falsa
- **Ciberacoso / Bullying**: Acceso a información para acosar usuarios
- **Doxing**: Exposición de información personal para encontrar usuarios
- **Recolección no autorizada de datos**: Venta a terceros publicitarios
- **Filtración masiva**: Compromiso afecta a millones simultáneamente
- **Manipulación de contenido**: Difusión de desinformación o malware

**Estadísticas alarmantes:**
- 96% de apps educativas comparten información con terceros
- 78% de estos datos se ceden a publicitarios sin consentimiento

---

## 3. Matriz Comparativa de Riesgos

| Aspecto | App Educativa | App Bancaria | App Salud | Red Social |
|--------|---|---|---|---|
| **Accesibilidad** | Local/Controlada | Pública Internet | Pública Internet | Pública Internet |
| **Severidad de datos** | Bajo | Crítica | Crítica | Alta |
| **Impacto económico** | Bajo | Máximo | Muy Alto | Alto |
| **Impacto en vida real** | Académico | Financiero | Sanitario | Social/Psicológico |
| **Riesgo explotación** | Muy Bajo | Máximo | Máximo | Máximo |
| **Necesidad autenticación** | Media | Crítica | Crítica | Alta |
| **Cifrado requerido** | Recomendado | Obligatorio | Obligatorio | Recomendado |
| **Usuarios externos** | No | Sí (millones) | Sí (miles-millones) | Sí (millones-miles millones) |
| **Regulación** | Ninguna | PCI-DSS, Bancaria | GDPR, HIPAA | GDPR, CCPA, LSSI-CE |

---

## 4. Riesgos Comunes entre Todas las Aplicaciones

Aunque los contextos varían, existen riesgos presentes en TODAS las aplicaciones:

### 4.1 Inyección de Código (SQL Injection, XSS, etc.)

**En App Educativa:**
- Riesgo: Bajo (acceso local, usuarios confiables)
- Impacto: Robo de datos académicos, modificación de calificaciones

**En App Bancaria:**
- Riesgo: Crítico (público accesible)
- Impacto: Robo directo de fondos, acceso a todas las cuentas

**En App Salud:**
- Riesgo: Crítico (público accesible)
- Impacto: Filtración masiva de historiales médicos

**En Red Social:**
- Riesgo: Crítico (público accesible)
- Impacto: Compromiso de millones de cuentas simultáneamente

**Conclusión:** La misma vulnerabilidad tiene impacto EXPONENCIALMENTE diferente según el contexto.

### 4.2 Validación de Entrada

Todos los sistemas requieren validación, pero el rigor depende del contexto:

```
App Educativa:        Validación básica de tipos y formatos
                      ↓
App Bancaria:         Validación exhaustiva, listas blancas, límites estrictos
                      ↓
App Salud:            Validación exhaustiva + auditoría de cambios
                      ↓
Red Social:           Validación + detección de patrones de ataque
```

### 4.3 Gestión de Sesiones

| Aplicación | Requisito | Razón |
|---|---|---|
| Educativa | Sesiones cortas | Bajo riesgo |
| Bancaria | Sesiones muy cortas, re-autenticación frecuente | Impedir secuestro de sesión |
| Salud | Sesiones moderadas + auditoría | Privacidad + compliance |
| Red Social | Sesiones largas | UX, pero con renovación de tokens |

---

## 5. OWASP ASVS: Aplicación por Contexto

OWASP ASVS proporciona tres niveles de seguridad:

### **ASVS Nivel 1 (Bajo Riesgo)** → Aplicación Educativa
- Entorno controlado
- Datos no críticos
- Sin acceso público
- Adecuada para laboratorios y aprendizaje

### **ASVS Nivel 2 (Riesgo Moderado)** → Red Social
- Acceso público
- Datos personales
- Muchos usuarios
- Requiere seguridad robusta pero no crítica

### **ASVS Nivel 3 (Alto Riesgo)** → Aplicaciones Bancarias y de Salud
- Acceso público
- Datos muy sensibles
- Impacto crítico en caso de fallo
- Requiere seguridad máxima
- Cumplimiento normativo exhaustivo

---

## 6. Reflexión Personal: ¿Son los Mismos Riesgos?

**RESPUESTA: NO. Son los mismos tipos de vulnerabilidades, pero con impactos radicalmente diferentes.**

### Similitudes:
- Todas enfrentan amenazas de inyección, validación inadecuada, etc.
- Todas necesitan proteger datos y sesiones
- Todas requieren buenas prácticas de desarrollo

### Diferencias Fundamentales:

**1. Probabilidad de Ataque:**
- App Educativa: Baja (no es blanco interesante)
- App Bancaria/Salud/RRSS: Máxima (objetivos lucrativos/sensibles)

**2. Impacto si Falla:**
- App Educativa: Inconveniente académico
- App Bancaria: Pérdida económica masiva
- App Salud: Riesgo para vidas humanas
- RRSS: Daño psicológico y reputacional de millones

**3. Responsabilidad Legal:**
- App Educativa: Responsabilidad limitada
- App Bancaria: Responsabilidad legal y normativa crítica
- App Salud: Responsabilidad legal + compliance GDPR/HIPAA
- RRSS: Responsabilidad legal + compliance GDPR

---

## 7. Lecciones Aprendidas

### Del Análisis de bWAPP (SQL Injection):

bWAPP demostraba que sin validación adecuada (Nivel 0) y apenas con filtros básicos (Nivel 1), es posible ejecutar SQL Injection. Esto ilustra que:

**En un contexto educativo (como nuestra aplicación):**
- La misma vulnerabilidad es un riesgo académico

**En un banco:**
- La misma vulnerabilidad permite transferir dinero

**En un hospital:**
- La misma vulnerabilidad expone historiales completos de pacientes

---

## 8. Conclusiones

### La seguridad no es absoluta, es contextual:

1. **Nivel de Seguridad = Función del Riesgo**: Una aplicación educativa Nivel 1 es perfecta para su contexto, pero sería peligrosa si manejara datos bancarios.

2. **La Amenaza Determina la Defensa**: Aplicaciones públicas requieren defensas exponencialmente más fuertes que aplicaciones internas.

3. **Datos = Responsabilidad**: Cuanto más sensibles los datos, más rigurosa debe ser la seguridad y mayor el cumplimiento normativo.

4. **ASVS es Escalable**: ASVS Nivel 1 es correcto para laboratorios, pero la migración a producción requiere Nivel 2 o 3 según el tipo de datos.

5. **La Educación en Riesgos es Crítica**: Entender que los mismos errores de código tienen impactos diferentes según el contexto es fundamental para desarrollar software seguro.

### Reflexión Final:

Como desarrollador de seguridad, debo recordar que no existe "seguridad perfecta", sino "seguridad apropiada al contexto". La clave es identificar correctamente el nivel de riesgo de cada aplicación y aplicar controles proporcionados.

Nuestra aplicación educativa no necesita (ni debe tener) la complejidad de un sistema bancario, pero si en el futuro maneja datos reales de usuarios, deberíamos migrar a ASVS Nivel 2 o superior inmediatamente.

---

**Autor:** Izan Correa Díaz  
**Fecha:** 29 de enero de 2026  
**Asignatura:** Puesta en Producción Segura - UT2  
**Actividad:** Apartado 4 - Reflexión sobre Riesgos de Aplicaciones
