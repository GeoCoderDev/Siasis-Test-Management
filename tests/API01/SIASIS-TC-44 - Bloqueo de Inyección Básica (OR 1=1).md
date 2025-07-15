# 🧪 Test Case: SIASIS-TC-14 - Validar Inicio de Sesión de Sesión Exitoso para rol de Directivo

> [!IMPORTANT] > **ID del Test Case:** SIASIS-TC-15
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
> | Campo               |              Valor              |
> | ------------------- | :-----------------------------: |
> | **ID Test Case**    |          SIASIS-TC-44           |
> | **Nombre**          | Bloqueo de Inyección SQL Básica |
> | **Módulo/Feature**  |        API01 - Seguridad        |
> | **Epic/User Story** | API01-Protección SQL Injection  |
> | **Tipo de Prueba**  |           🔒 Security           |
> | **Nivel de Prueba** |          🌐 System 🔗           |
> | **Prioridad**       |           🔴 Critical           |
> | **Severidad**       |           🔴 Blocker            |
> | **Automatizable**   |              ❌ No              |
> | **Automatizado**    |              ❌ No              |

---

> [!TIP]
>
> ### 🏷️ Tags y Categorización
>
> **Tags principales:**
>
> ```gherkin
> @SIASIS-TC-44
> ```
>
> **Tags por componente:**
>
> ```gherkin
> @API01 @RDP02
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
> Verificar que el endpoint bloquea intentos de inyección SQL básica usando condición OR 1=1 en query params

> [!NOTE]
>
> ### 🎯 Objetivo Principal
>
> **Objetivo:** Garantizar que la aplicación es resistente ante ataques de inyección SQL en ambiente de (desarrollo, certificación y producción)
>
> **Criterio de Éxito:** <br>
>
> - Bloqueo de payloads clásicos de bypass <br>
> - Mensaje de error genérico sin detalles técnicos <br>
> - Registro en logs de seguridad <br>
>   Campo success: true

---

## 🔧 Configuración Técnica

> [!WARNING]
>
> ### 💻 Tecnología y Componentes
>
> | Aspecto                  | Detalle       |
> | ------------------------ | ------------- |
> | **Tecnología Principal** | API (Postman) |
> | **Dispositivos**         | Desktop       |
> | **Sistemas Operativos**  | Windows       |

> [!CAUTION]
>
> ### 🏗️ Componentes Involucrados
>
> | Componente | Descripción                                                                                                                                                  | Si  | No  |
> | :--------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | --- | --- |
> | **SIU01**  | Servidor de Interfaces de Usuario                                                                                                                            |     | ❌  |
> | **API01**  | API para personal del colegio (Directivos, Auxiliares, Profesores, etc)                                                                                      | ✅  |     |
> | **TPS01**  | Tareas programadas con Scripts                                                                                                                               |     | ❌  |
> | **EMCS01** | Ejecutor múltiple de consultas SQL de Escritura de API01 hacia RDP02 y RDP03                                                                                 |     | ❌  |
> | **EMCN01** | Ejecutor múltiple de consultas SQL de escritura para API02 hacia RDP03                                                                                       |     | ❌  |
> | **RDP01**  | Repositorio de Datos Persistentes solo para Archivos del Sistema en General (Fotos de Perfil, Excels de Asistencia, Backups, etc) ➡️**Google Drive**         |     | ❌  |
> | **RDP02**  | Repositorio de Datos Persistentes para Datos Relacionados a Personal del Colegio (Directivos, Auxiliares, Profesores, etc) ➡️ PostgreSQL                     | ✅  |     |
> | **RDP03**  | Repositorio de Datos Persistentes para Datos Relacionados a Responsables (Padres de Familia/Apoderados) ➡️ MongoDB                                           |     | ❌  |
> | **RDP04**  | Repositorio de Datos Persistentes para JSONs con Información de Datos de Asistencia del Día Actual (Se actualiza todos los días por TPS01) ➡️ Blob de Vercel |     | ❌  |
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
> Feature: Protección contra SQL Injection en Query Params
>  Como QA del sistema
>  Quiero verificar el bloqueo de inyecciones básicas
>  Para garantizar la seguridad de los datos
>
>   Background:
>     Given la API01 está operativa en el ambiente de (desarrollo, certificación y desarrollo).
>
>   @SIASIS-TC-44 @API01 @RDP02
>   Scenario: Bloqueo de condición OR 1=1
>   Given el endpoint "/api/usuarios-genericos" está operativo
>   When realizo una petición GET con "Criterio=rol=1' OR '1'='1"
>   Then recibo un código HTTP 400
>   And el mensaje de error no revela detalles técnicos
>   And el sistema registra el intento en logs de seguridad
> ```

---

## ⚙️ Precondiciones y Setup

> [!IMPORTANT]
>
> ### 🔧 Precondiciones
>
> #### Estado del Sistema:
>
> - ✅ Aplicación desplegada y funcionando
> - ✅ Base de datos con datos de prueba cargados
> - ✅ Servicios externos disponibles
> - ✅ Conectividad de red estable
>
> #### Datos de Prueba Requeridos:
>
> - 📊 **Datos específicos:** Datos de prueba: Usuarios con roles PP, PS, A, PA

---

## 📊 Métricas y Performance

> [!INFO]
>
> ### ⏱️ Criterios de Performance (si aplica)
>
> | Métrica                 | Valor Esperado | Crítico       |
> | ----------------------- | -------------- | ------------- |
> | **Tiempo de Respuesta** | < 2 segundos   | < 5 segundos  |
> | **Tiempo de Carga**     | < 3 segundos   | < 10 segundos |
> | **Uso de Memoria**      | < 500MB        | < 1GB         |
> | **Ancho de Banda**      | < 1MB          | < 5MB         |

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
> | Rol                         | SI  | NO  |
> | --------------------------- | --- | --- |
> | **Directivo**               |     | ❌  |
> | **Profesor Primaria**       | ✅  |     |
> | **Auxiliar**                | ✅  |     |
> | **Profesor Secundaria**     | ✅  |     |
> | **Tutor**                   |     | ❌  |
> | **Personal Administrativo** | ✅  |     |
> | **Responsable**             |     | ❌  |

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
