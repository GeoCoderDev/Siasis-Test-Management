# 🧪 Test Case: SIASIS-TC-12 - Validar Integridad de Datos Almacenados en RDP04

> [!IMPORTANT] > **ID del Test Case:** SIASIS-TC-49
> **Fecha de Creación:** 13/07/2025
> **Autor:** Andry Diego
> **Última Actualización:** 13/07/2025
> **Estado:** 🟢 Ready

---

## 📋 Información General

> [!NOTE]
>
> ### 🔖 Metadatos del Test
>
> | Campo               |                                        Valor                                         |
> | ------------------- | :----------------------------------------------------------------------------------: |
> | **ID Test Case**    |                                     SIASIS-TC-47                                     |
> | **Nombre**          | Validar Integridad y Completitud de Datos <br> Almacenados en RDP04 (Blog de Vercel) |
> | **Módulo/Feature**  |           SIASIS-TP-6 - Obtención de Datos para Toma de Asistencia Diaria            |
> | **Epic/User Story** |                                     No se tiene                                      |
> | **Tipo de Prueba**  |                                     🔧 Funcional                                     |
> | **Nivel de Prueba** |                                      🌐 System                                       |
> | **Prioridad**       |                                     🔴 Critical                                      |
> | **Severidad**       |                                      🔴 Blocker                                      |
> | **Automatizable**   |                                        ✅ SI                                         |
> | Automatizado        |                                        ✅ SI                                         |

---

> [!TIP]
>
> ### 🏷️ Tags y Categorización
>
> **Tags principales:**
>
> ```gherkin
> @SIASIS-TC-49
> ```
>
> **Tags por componente:**
>
> ```gherkin
> @TPS01 @API01 @RDP04
> ```
>
> **Tags por rol:**
>
> ```gherkin
> @dev @cert @prod
> ```

---

## 🎯 Descripción y Objetivos

> [!IMPORTANT]
>
> ### 📖 Descripción del Test Case
>
> Este test valida que los datos almacenados en RDP04 después de la ejecución de la tarea programada contienen toda la información necesaria y correcta para la toma de asistencia, incluyendo listas de profesores por nivel, horarios del día, información de turnos y estructura JSON válida.
> [!NOTE]
>
> ### 🎯 Objetivo Principal
>
> **Objetivo:** Verificar que los JSONs almacenados en RDP04 contienen datos completos, íntegros y estructurados correctamente para la toma de asistencia diaria
>
> **Criterio de Éxito:** <br>
>
> - JSONs con estructura válida <br>
> - Datos actualizados (timestamp reciente <br>
> - Datos almacenados correctamente en RDP04 <br>
> - Logs de ejecución disponibles

---

## 🔧 Configuración Técnica

> [!WARNING]
>
> ### 💻 Tecnología y Componentes
>
> | Aspecto                  | Detalle        |
> | ------------------------ | -------------- |
> | **Tecnología Principal** | GitHub Actions |
> | **Dispositivos**         | Desktop        |
> | **Sistemas Operativos**  | Windows        |

> [!CAUTION]
>
> ### 🏗️ Componentes Involucrados
>
> | Componente | Descripción                                                                                                                                                  | Si  | No  |
> | :--------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | --- | --- |
> | **SIU01**  | Servidor de Interfaces de Usuario                                                                                                                            |     | ❌  |
> | **API01**  | API para personal del colegio (Directivos, Auxiliares, Profesores, etc)                                                                                      | ✅  |     |
> | **API02**  | API para padres de Familia                                                                                                                                   |     | ❌  |
> | **API03**  | API para obtención de hora real UTC                                                                                                                          | ✅  |     |
> | **TPS01**  | Tareas programadas con Scripts                                                                                                                               | ✅  |     |
> | **EMCS01** | Ejecutor múltiple de consultas SQL de Escritura de API01 hacia RDP02 y RDP03                                                                                 |     | ❌  |
> | **EMCN01** | Ejecutor múltiple de consultas SQL de escritura para API02 hacia RDP03                                                                                       |     | ❌  |
> | **RDP01**  | Repositorio de Datos Persistentes solo para Archivos del Sistema en General (Fotos de Perfil, Excels de Asistencia, Backups, etc) ➡️**Google Drive**         |     | ❌  |
> | **RDP02**  | Repositorio de Datos Persistentes para Datos Relacionados a Personal del Colegio (Directivos, Auxiliares, Profesores, etc) ➡️ PostgreSQL                     | ✅  |     |
> | **RDP03**  | Repositorio de Datos Persistentes para Datos Relacionados a Responsables (Padres de Familia/Apoderados) ➡️ MongoDB                                           |     | ❌  |
> | **RDP04**  | Repositorio de Datos Persistentes para JSONs con Información de Datos de Asistencia del Día Actual (Se actualiza todos los días por TPS01) ➡️ Blob de Vercel | ✅  |     |
> | **RDP05**  | Repositorio de Datos Persistentes para Asistencias Tomadas a lo largo del día actual exclusivamente ➡️ Redis                                                 |     | ❌  |
> |  **SS01**  | Servidor de Sockets para operaciones en tiempo real                                                                                                          |     | ❌  |
> |  **SE01**  | Servicio Externo de Correo Electrónico por GMAIL de Google                                                                                                   |     | ❌  |

---

## 📝 Definición en Gherkin

> [!TIP]
>
> ### 🥒 Scenario en Gherkin
>
> ```gherkin
> Feature: Validación de Integridad de Datos en RDP04
>  Como Líder Técnico del sistema SIASIS
>  Quiero que los datos almacenados en RDP04 sean completos e íntegros
>  Para garantizar una correcta toma de asistencia diaria
>
>  Background:
>    Given la tarea programada se ha ejecutado correctamente
>    And los datos han sido almacenados en RDP04
>
> @SIASIS-TC-49 @validacion-integridad-datos @almacenamiento-json-rdp04
> Scenario: Validar integridad y completitud de datos en RDP04
>    Given existen archivos JSON en RDP04 del día actual
>    When accedo y consulto los archivos JSON almacenados
>    Then los JSONs deben tener estructura válida
>    And debe contener lista completa de profesores de primaria
>    And debe contener lista completa de profesores de secundaria
>    And debe incluir horarios completos del día escolar actual
>    And debe tener información de turnos disponible
>    And los timestamps deben ser del día actual
>    And no debe haber campos obligatorios vacíos o nulos
>    And los datos deben coincidir con la fuente original (RDP02)
> ```

---

## ⚙️ Precondiciones y Setup

> [!IMPORTANT]
>
> ### 🔧 Precondiciones
>
> #### Estado del Sistema:
>
> - ✅ Tarea programada ejecutada exitosamente (TC-16 passed)
> - ✅ Herramientas de validación JSON disponibles
> - ✅ Datos de referencia disponibles en RDP02
> - ✅ RDP04 (Blob de Vercel) accesible para escritura
>
> #### Datos de Prueba Requeridos:
>
> - 📊 Datos de referencia: Información actual de profesores en RDP02

---

## 📊 Métricas y Performance

> [!INFO]
>
> ### ⏱️ Criterios de Performance (si aplica)
>
> | Métrica                      | Valor Esperado | Crítico       |
> | ---------------------------- | -------------- | ------------- |
> | **Tiempo de Descarga JSON**  | < 30 segundos  | < 2 minutos   |
> | **Tiempo de Validación**     | <12 minutos    | < 3 minutos   |
> | **Tiempo de Almacenamiento** | < 5 KB         | < 10.25 KB    |
---

## 🔗 Dependencias y Relaciones

> [!NOTE]
>
> ### 🔗 Dependencias
>
> #### Test Cases Relacionados:
>
> - 📋 **Pre-requisito:** No hay Pre-requitsitos
> - 🔄 **Dependiente:** No hay dependencias
> - 🔗 **Relacionado:** No hay Relacion

---

## 🎭 Roles y Permisos

> [!CAUTION]
>
> ### 👥 Roles Involucrados
>
> | Rol                     | SI  | NO  |
> | ----------------------- | --- | --- |
> | **Directivo**           |     | ❌  |
> | **Profesor Primaria**   |     | ❌  |
> | **Auxiliar**            |     | ❌  |
> | Profesor Secundaria     |     | ❌  |
> | Tutor                   |     | ❌  |
> | Personal Administrativo |     | ❌  |
> | **Responsable**         |     | ❌  |

---

## 📎 Evidencias y Documentación

> [!TIP]
>
> ### 📸 Evidencias Requeridas
>
> #### Durante la Ejecución:
>
> - 📸 Screenshot de cada paso crítico
> - 📸 Screenshot del resultado final
>
> #### Logs y Datos:
>
> - 📝 Logs de aplicación
> - 📝 Request/Response de APIs
> - 📝 Tiempos de respuesta

---

## 📞 Información de Contacto

> [!INFO]
>
> ### 👥 Responsables
>
> |        Rol         |   Nombre    | Email / Celular |     Responsabilidad      |
> | :----------------: | :---------: | :-------------: | :----------------------: |
> | **Autor del Test** | Andry Diego |        -        | Creación y mantenimiento |
> | **Product Owner**  | Juan Chavez |        -        | Validación de criterios  |
> |   **Tech Lead**    | Juan Chavez |        -        |     Revisión técnica     |
> |  **Dev Asignado**  | Juan Chavez |        -        |    Corrección de bugs    |

---

## 📝 Notas y Observaciones

> [!NOTE]
>
> ### 💡 Notas Importantes
>
> - No hay notas por el momento
>
> ### 🔄 Historial de Cambios
>
> |    Fecha     | Versión | Cambio               |    Autor    |
> | :----------: | :-----: | -------------------- | :---------: |
> |  28/06/2025  |   1.0   | Creación inicial     | Andry Diego |
> | [DD/MM/YYYY] |   1.1   | [Descripción cambio] |  [Nombre]   |

---

**📅 Última Actualización:** 07/07/2025 01:26AM
**✅ Estado de Revisión:** Aprobado
**👤 Revisado por:** Juan Chavez - Lider Técnico
