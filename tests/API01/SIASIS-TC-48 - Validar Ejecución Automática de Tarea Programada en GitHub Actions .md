# 🧪 Test Case: SIASIS-TC-12 - Validar Ejecución Automática de Tarea Programada en GitHub Actions

> [!IMPORTANT] > **ID del Test Case:** SIASIS-TC-48
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
> | Campo               |                                Valor                                 |
> | ------------------- | :------------------------------------------------------------------: |
> | **ID Test Case**    |                             SIASIS-TC-48                             |
> | **Nombre**          | Validar Ejecución Automática de Tarea Programada <br> en GitHub Actions para Obtención de Datos de Asistencia |
> | **Módulo/Feature**  |   SIASIS-TP-6 - Obtención de Datos para Toma de Asistencia Diaria    |
> | **Epic/User Story** |                             No se tiene                              |
> | **Tipo de Prueba**  |                             🔧 Funcional                             |
> | **Nivel de Prueba** |                              🌐 System                               |
> | **Prioridad**       |                             🔴 Critical                              |
> | **Severidad**       |                              🔴 Blocker                              |
> | **Automatizable**   |                                ✅ SI                                 |
> | Automatizado        |                                ✅ SI                                 |

---

> [!TIP]
>
> ### 🏷️ Tags y Categorización
>
> **Tags principales:**
>
> ```gherkin
> @SIASIS-TC-48
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
> Este test valida que la tarea programada en GitHub Actions se ejecute automáticamente a las 4:30am en días escolares (Lunes-Viernes) para obtener y almacenar todos los datos necesarios para la toma de asistencia diaria en formato JSON en RDP04 (Blob de Vercel).
> [!NOTE]
>
> ### 🎯 Objetivo Principal
>
> **Objetivo:** Verificar que GitHub Actions ejecute correctamente la tarea programada a las 4:30am en días escolares para obtener datos de asistencia
>
> **Criterio de Éxito:** <br>
>
> - GitHub Action se ejecuta automáticamente a las 4:30am ±5 minuto <br>
> - Status de ejecución: SUCCESS <br>
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
> | **EMCS01** | Ejecutor múltiple de consultas SQL de Escritura de API01 hacia RDP02 y RDP03                                                                                 | ✅  |     |
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
> Feature: Ejecución Automática de Tarea Programada para Obtención de Datos de Asistencia
>  Como Líder Técnico del sistema SIASIS
>  Quiero que se ejecute automáticamente una tarea programada a las 4:30am
>  Para obtener todos los datos necesarios para la toma de asistencia diaria
>
>  Background:
>    Given el sistema SIASIS está operativo
>    And GitHub Actions está configurado correctamente
>    And es un día escolar (Lunes-Viernes)
>
> @SIASIS-TC-16 @github-actions-scheduled @tarea-programada-execution
> Scenario: Ejecución automática de tarea programada a las 4:30am
>    Given son las 4:30am ±5 minutos de un día escolar
>    And el workflow de GitHub Actions está habilitado
>    When se ejecuta automáticamente la tarea programada
>    Then el GitHub Action debe iniciarse correctamente
>    And el status de ejecución debe ser "SUCCESS"
>    And debe consultar datos de profesores de primaria y secundaria
>    And debe obtener los horarios del día escolar actual
>    And debe almacenar los datos en formato JSON en RDP04
>    And los logs de ejecución deben estar disponibles
> ```

---

## ⚙️ Precondiciones y Setup

> [!IMPORTANT]
>
> ### 🔧 Precondiciones
>
> #### Estado del Sistema:
>
> - ✅ GitHub Actions habilitado en el repositorio
> - ✅ Workflow configurado con cron job para 4:30am
> - ✅ API01 y RDP02 disponibles para consultas
> - ✅ RDP04 (Blob de Vercel) accesible para escritura
>
> #### Datos de Prueba Requeridos:
>
> - 📊 📊 Datos específicos: Base de datos con información de profesores y horarios
> - 📅 Fecha: Día escolar (Lunes-Viernes)

---

## 📊 Métricas y Performance

> [!INFO]
>
> ### ⏱️ Criterios de Performance (si aplica)
>
> | Métrica                       | Valor Esperado | Crítico       |
> | ----------------------------- | -------------- | ------------- |
> | **Tiempo de Ejecución Total** | < 5 minutos    | < 10 minutos  |
> | **Tiempo de Consulta API**    | < 2 minutos    | < 5 minutos   |
> | **Tiempo de Almacenamiento**  | < 1 minuto     | < 3 minutos   |
> | **Precisión Horaria**         | ±5 minutos     | < ±10 minutos |

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
> | **Autor del Test** |  Andry Diego   |        -        | Creación y mantenimiento |
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
