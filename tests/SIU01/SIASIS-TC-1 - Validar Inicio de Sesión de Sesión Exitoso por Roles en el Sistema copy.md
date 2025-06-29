# 🧪 Test Case: SIASIS-TC-1 - Validar Inicio de Sesión de Sesión Exitoso por Roles en el Sistema

> [!IMPORTANT]
> **ID del Test Case:** SIASIS-TC-1
> **Fecha de Creación:** 28/06/2025 
> **Autor:** Gil Pardo
> **Última Actualización:** 28/06/2025
> **Estado:** 🟢 Ready

---

## 📋 Información General

> [!NOTE]
>
> ### 🔖 Metadatos del Test
>
> | Campo               |                                                                                    Valor                                                                                    |
> | ------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
> | **ID Test Case**    |                                                                                 SIASIS-TC-1                                                                                 |
> | **Nombre**          |                                                          Validar Inicio de Sesión  Exitoso por Roles en el Sistema                                                          |
> | **Módulo/Feature**  |                                                                              Inicio de Sesión                                                                               |
> | **Epic/User Story** |                                                                                 No se tiene                                                                                 |
> | **Tipo de Prueba**  |                                                                            🔧 Funcional\|🌐 E2E                                                                             |
> | **Nivel de Prueba** |                                                                                  🌐 System                                                                                  |
> | **Prioridad**       |                                                                                 🔴 Critical                                                                                 |
> | **Severidad**       |                                                                                 🔴 Blocker                                                                                  |
> | **Automatizable**   |                                                                                    ✅ Sí                                                                                    |
> | Automatizada        | ✅ Sí ([Test Automatizado](https://github.com/GeoCoderDev/continuous-testing-selenium-SIASIS-SIU01-WEB/blob/master/src/test/resources/features/Login.feature "👁️Ver Test")) |

---

> [!TIP]
>
> ### 🏷️ Tags y Categorización
>
> **Tags principales:**
>
> ```gherkin
> @SIASIS-TC-1 @happy @login @auth @regresion @smoke
> ```
>
> **Tags por componente:**
>
> ```gherkin
> @SIU01
> ```
>
> **Tags por rol:**
>
> ```gherkin
> @todos-los-roles
> ```

---

## 🎯 Descripción y Objetivos

> [!IMPORTANT]
>
> ### 📖 Descripción del Test Case
>
> Este es un **test de autenticación básico** que verifica el flujo de login exitoso para todos los roles del sistema SIASIS (Sistema de Control de Asistencia).

> [!NOTE]
>
> ### 🎯 Objetivo Principal
>
> **Objetivo:** Validar que cada tipo de usuario puede iniciar sesión correctamente con sus credenciales y acceder a su interfaz de bienvenida correspondiente.
>
> **Criterio de Éxito:** Se puede visualizar las interfaces de bienvenida con los nombres y roles espectivos de cada usuario.

---

## 🔧 Configuración Técnica

> [!WARNING]
>
> ### 💻 Tecnología y Componentes
>
> | Aspecto                  | Detalle                               |
> | ------------------------ | ------------------------------------- |
> | **Tecnología Principal** | 🌐 Web\| 🖥️ Desktop                   |
> | **Navegadores**          | Chrome, Edge                          |
> | **Dispositivos**         | Desktop, Mobile, Tablet               |
> | **Sistemas Operativos**  | Windows, macOS, Linux, iOS, Android   |
> | **Resoluciones**         | 1920x1080, 1366x768, 375x667 (mobile) |

> [!CAUTION]
>
> ### 🏗️ Componentes Involucrados
>
> | Componente | Descripción                                                                                                                                                  | Si  | No  |
> | :--------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | --- | --- |
> | **SIU01**  | Servidor de Interfaces de Usuario                                                                                                                            | ✅  |     |
> | **API01**  | API para personal del colegio (Directivos, Auxiliares, Profesores, etc)                                                                                      | ✅  |     |
> | **API02**  | API para padres de Familia                                                                                                                                   |     | ❌  |
> | **API03**  | API para obtención de hora real UTC                                                                                                                          |     | ❌  |
> | **TPS01**  | Tareas programadas con Scripts                                                                                                                               |     | ❌  |
> | **EMCS01** | Ejecutor múltiple de consultas SQL de Escritura de API01 hacia RDP02 y RDP03                                                                                 |     | ❌  |
> | **EMCN01** | Ejecutor múltiple de consultas SQL de escritura para API02 hacia RDP03                                                                                       |     | ❌  |
> | **RDP01**  | Repositorio de Datos Persistentes solo para Archivos del Sistema en General (Fotos de Perfil, Excels de Asistencia, Backups, etc) ➡️**Google Drive**         |     | ❌  |
> | **RDP02**  | Repositorio de Datos Persistentes para Datos Relacionados a Personal del Colegio (Directivos, Auxiliares, Profesores, etc) ➡️ PostgreSQL                     |     | ❌  |
> | **RDP03**  | Repositorio de Datos Persistentes para Datos Relacionados a Responsables (Padres de Familia/Apoderados) ➡️ MongoDB                                           | ✅  |     |
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
> Feature: Inicio de Sesión en el sistema SIASIS
>   Como usuario del sistema SIASIS
>   Quiero poder iniciar sesión con diferentes roles
>   Para acceder a las funcionalidades correspondientes a mi rol
>
>   Background:
>     Given Estoy en la página de login
>
>   @SIASIS-TC-1 @happy @login @auth @regresion @smoke @SIU01 @API02 @RDP03 @todos-los-roles
>   Scenario Outline: Ingreso de login a SIASIS con el rol <rol>
>     Given Selecciono el rol <rol>
>     And Ingreso mi nombre de usuario y contraseña
>     Then Accedo al sistema como <rol>
>
>     Examples:
>       | rol                     |
>       | DIRECTIVO               |
>       | PROFESOR_PRIMARIA       |
>       | AUXILIAR                |
>       | PROFESOR_SECUNDARIA     |
>       | TUTOR                   |
>       | PERSONAL_ADMINISTRATIVO |
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
> - 📊 **Datos específicos:** Credenciales **_(Nombre de Usuario y Contraseña)_** por cada Rol

---

## 📋 Pasos de Ejecución

> [!NOTE]
>
> ### 🚶‍♂️ Pasos Detallados
>
> No necesarios, el test esta automatizado

---

## 🚫 Casos Negativos y Edge Cases

> [!WARNING]
>
> ### ⚠️ Escenarios de Error
>
> | Escenario            | Acción                         | Resultado Esperado          |
> | -------------------- | ------------------------------ | --------------------------- |
> | **Datos Inválidos**  | [Ingreso de datos incorrectos] | [Mensaje de error esperado] |
> | **Sin Permisos**     | [Acceso sin autorización]      | [Bloqueo o redirección]     |
> | **Timeout**          | [Operación que excede tiempo]  | [Manejo de timeout]         |
> | **Conexión Perdida** | [Pérdida de conectividad]      | [Recuperación o error]      |

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
> - 🔗 **Relacionado:** SIASIS-TC-2 (Login solo para Directivos)
> - 🔗 **Relacionado:** SIASIS-TC-3 (Login solo para Profesores de Primaria)
> - 🔗 **Relacionado:** SIASIS-TC-4 (Login solo para Auxiliar)
> - 🔗 **Relacionado:** SIASIS-TC-5 (Login solo para Profesores de Secundaria)
> - 🔗 **Relacionado:** SIASIS-TC-6 (Login solo para Tutores)
> - 🔗 **Relacionado:** SIASIS-TC-7 (Login solo para Personales Administrativos)

---

## 🎭 Roles y Permisos

> [!CAUTION]
>
> ### 👥 Roles Involucrados
>
> | Rol                     | SI  | NO  |
> | ----------------------- | --- | --- |
> | **Directivo**           | ✅  |     |
> | **Profesor Primaria**   | ✅  |     |
> | **Auxiliar**            | ✅  |     |
> | Profesor Secundaria     | ✅  |     |
> | Tutor                   | ✅  |     |
> | Personal Administrativo | ✅  |     |
> | **Responsable**         | ✅  |     |

---

## 📎 Evidencias y Documentación

> [!TIP]
>
> ### 📸 Evidencias Requeridas
>
> #### Durante la Ejecución:
>
> - 📸 Screenshot del estado inicial
> - 📸 Screenshot de cada paso crítico
> - 📸 Screenshot del resultado final
> - 🎥 Video de la ejecución completa (si es complejo)
>
> #### Logs y Datos:
>
> - 📝 Logs de aplicación
> - 📝 Logs de base de datos
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
> | **Autor del Test** |  Gil Pardo  |        -        | Creación y mantenimiento |
> | **Product Owner**  | Juan Chavez |        -        | Validación de criterios  |
> |   **Tech Lead**    | Juan Chavez |        -        |     Revisión técnica     |
> |  **Dev Asignado**  | Juan Chavez |        -        |    Corrección de bugs    |

---

## 📝 Notas y Observaciones

> [!NOTE]
>
> ### 💡 Notas Importantes
>
> - Aun falta agregar el Rol de Responsable
> - Aun falta especificar los Test Cases relacionados
> - [Consideración especial]
>
> ### 🔄 Historial de Cambios
>
> |    Fecha     | Versión | Cambio               |    Autor    |
> | :----------: | :-----: | -------------------- | :---------: |
> |  28/06/2025  |   1.0   | Creación inicial     | Juan Chavez |
> | [DD/MM/YYYY] |   1.1   | [Descripción cambio] |  [Nombre]   |

---

**📅 Última Actualización:** 28/06/2025 01:21PM
**✅ Estado de Revisión:** Aprobado
**👤 Revisado por:** Juan Chavez - Lider Técnico
