# 🧪 Test Case: SIASIS-TC-8 - Validar edicion de datos personales propios de Directivo

> [!IMPORTANT] > **ID del Test Case:** SIASIS-TC-8
> **Fecha de Creación:** 28/06/2025 
> **Autor:** Gil Pardo
> **Última Actualización:** 28/06/2025
> **Estado:** 🟡 Draft | 🟢 Ready | 🔵 In Review | ⚪ Approved

---

## 📋 Información General

> [!NOTE]
>
> ### 🔖 Metadatos del Test
>
> | Campo                     |                                                                                           Valor                                                                                           |
> | ------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
> | **ID Test Case**    |                                                                                        SIASIS-TC-8                                                                                        |
> | **Nombre**          |                                                                 Validar Edición de Datos personales propios de Directivo                                                                 |
> | **Módulo/Feature** |                                                                                     Edición de Datos                                                                                     |
> | **Epic/User Story** |                                                                                        No se tiene                                                                                        |
> | **Tipo de Prueba**  |                                                                                   🔧 Funcional\|🌐 E2E                                                                                   |
> | **Nivel de Prueba** |                                                                                         🌐 System                                                                                         |
> | **Prioridad**       |                                                                                        🔴 Critical                                                                                        |
> | **Severidad**       |                                                                                        🔴 Blocker                                                                                        |
> | **Automatizable**   |                                                                                          ✅ Sí                                                                                          |
> | Automatizado              | ✅ Sí ([Test Automatizado](https://github.com/GeoCoderDev/continuous-testing-selenium-SIASIS-SIU01-WEB/blob/master/src/test/resources/features/EdicionDatosPersonales.feature "👁️Ver Test")) |

---

> [!TIP]
>
> ### 🏷️ Tags y Categorización
>
> **Tags principales:**
>
> ```gherkin
> @SIASIS-TC-8 @happy @edicion-datos-personales-propios
> ```
>
> **Tags por componente:**
>
> ```gherkin
> @SIU01 @API01 @RDP02
> ```
>
> **Tags por rol:**
>
> ```gherkin
> @directivo
> ```

---

## 🎯 Descripción y Objetivos

> [!IMPORTANT]
>
> ### 📖 Descripción del Test Case
>
> Este es un test de funcionalidad que verifica la capacidad de un directivo para modificar sus propios datos personales en el sistema SIASIS.

> [!NOTE]
>
> ### 🎯 Objetivo Principal
>
> **Objetivo:** Validar que los directivos pueden actualizar exitosamente su información personal (DNI, nombres, apellidos, género, celular) y que los cambios persisten correctamente en el sistema.
>
> **Criterio de Éxito:** Luego de la modificación, los datos del directivo permanecen modificados.

---

## 🔧 Configuración Técnica

> [!WARNING]
>
> ### 💻 Tecnología y Componentes
>
> | Aspecto                         | Detalle                                                     |
> | ------------------------------- | ----------------------------------------------------------- |
> | **Tecnología Principal** | 🌐 Web\| 📱 Mobile \| 🔌 API \| 💾 Database \| 🖥️ Desktop |
> | **Navegadores**           | Chrome, Edge                                                |
> | **Dispositivos**          | Desktop, Mobile, Tablet                                     |
> | **Sistemas Operativos**   | Windows, Linux, Android                                     |
> | **Resoluciones**          | 1920x1080, 1366x768, 375x667 (mobile)                       |

> [!CAUTION]
>
> ### 🏗️ Componentes Involucrados
>
> |    Componente    | Descripción                                                                                                                                                      | Si | No |
> | :--------------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | -- | -- |
> | **SIU01** | Servidor de Interfaces de Usuario                                                                                                                                 | ✅ |    |
> | **API01** | API para personal del colegio (Directivos, Auxiliares, Profesores, etc)                                                                                           | ✅ |    |
> | **API02** | API para padres de Familia                                                                                                                                        |    | ❌ |
> | **API03** | API para obtención de hora real UTC                                                                                                                              |    | ❌ |
> | **TPS01** | Tareas programadas con Scripts                                                                                                                                    |    | ❌ |
> | **EMCS01** | Ejecutor múltiple de consultas SQL de Escritura de API01 hacia RDP02 y RDP03                                                                                     |    | ❌ |
> | **EMCN01** | Ejecutor múltiple de consultas SQL de escritura para API02 hacia RDP03                                                                                           |    | ❌ |
> | **RDP01** | Repositorio de Datos Persistentes solo para Archivos del Sistema en General (Fotos de Perfil, Excels de Asistencia, Backups, etc) ➡️**Google Drive**      |    | ❌ |
> | **RDP02** | Repositorio de Datos Persistentes para Datos Relacionados a Personal del Colegio (Directivos, Auxiliares, Profesores, etc) ➡️ PostgreSQL                        | ✅ |    |
> | **RDP03** | Repositorio de Datos Persistentes para Datos Relacionados a Responsables (Padres de Familia/Apoderados) ➡️ MongoDB                                              |    | ❌ |
> | **RDP04** | Repositorio de Datos Persistentes para JSONs con Información de Datos de Asistencia del Día Actual (Se actualiza todos los días por TPS01) ➡️ Blob de Vercel |    | ❌ |
> | **RDP05** | Repositorio de Datos Persistentes para Asistencias Tomadas a lo largo del día actual exclusivamente ➡️ Redis                                                   |    | ❌ |
> |  **SS01**  | Servidor de Sockets para operaciones en tiempo real                                                                                                               |    | ❌ |
> |  **SE01**  | Servicio Externo de Correo Electrónico por GMAIL de Google                                                                                                       |    | ❌ |

---

## 📝 Definición en Gherkin

> [!TIP]
>
> ### 🥒 Scenario en Gherkin
>
> ```gherkin
> Feature: Edicion de Datos Personales por Rol
>   Como usuario del sistema SIASIS
>   Quiero poder modificar mis datos personales
>   Para mantener actualizada mi informacion en el sistema
>
>   Background:
>     Given Estoy en la página de login
>
>   @SIASIS-TC-2 @happy @edicion-datos-personales-propios @SIU01 @API01 @RDP02 @directivo
>   Scenario: Directivo edita sus propios datos personales
>     Given Selecciono el rol DIRECTIVO
>     And Ingreso mi nombre de usuario y contraseña
>     Then Accedo al sistema como DIRECTIVO
>     When Estoy en la página de edición de perfil
>     And Edito mis datos personales con los valores aleatorios
>     Then Verifico que se han guardado los cambios
>     And Restauro los datos originales
>     Then verifico que los datos originales son correctos
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
> - 📊 **Datos específicos:** Credenciales **_(Nombre de Usuario y Contraseña)_** de cualquier usuario con rol de Directivo

---

## 📋 Pasos de Ejecución

> [!NOTE]
>
> ### 🚶‍♂️ Pasos Detallados
>
> No necesario, el test esta automatizado.

---

## 🚫 Casos Negativos y Edge Cases

> [!WARNING]
>
> ### ⚠️ Escenarios de Error
>
> | Escenario                   | Acción                        | Resultado Esperado          |
> | --------------------------- | ------------------------------ | --------------------------- |
> | **Datos Inválidos**  | [Ingreso de datos incorrectos] | [Mensaje de error esperado] |
> | **Sin Permisos**      | [Acceso sin autorización]     | [Bloqueo o redirección]    |
> | **Timeout**           | [Operación que excede tiempo] | [Manejo de timeout]         |
> | **Conexión Perdida** | [Pérdida de conectividad]     | [Recuperación o error]     |

---

## 📊 Métricas y Performance

> [!INFO]
>
> ### ⏱️ Criterios de Performance (si aplica)
>
> | Métrica                      | Valor Esperado | Crítico      |
> | ----------------------------- | -------------- | ------------- |
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
> - 📋 **Pre-requisito:** No hay pre-requisitos
> - 🔄 **Dependiente:** No hay dependencias
> - 🔗 **Relacionado:** No hay test relacionados

---

## 🎭 Roles y Permisos

> [!CAUTION]
>
> ### 👥 Roles Involucrados
>
> | Rol                         | SI | NO |
> | --------------------------- | -- | -- |
> | **Directivo**         | ✅ |    |
> | **Profesor Primaria** |    | ❌ |
> | **Auxiliar**          |    | ❌ |
> | Profesor Secundaria         |    | ❌ |
> | Tutor                       |    | ❌ |
> | Personal Administrativo     |    | ❌ |
> | **Responsable**       |    | ❌ |

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
> |           Rol           |   Nombre   | Email / Celular |      Responsabilidad      |
> | :----------------------: | :---------: | :-------------: | :-----------------------: |
> | **Autor del Test** |  Gil Pardo  |        -        | Creación y mantenimiento |
> | **Product Owner** | Juan Chavez |        -        | Validación de criterios |
> |   **Tech Lead**   | Juan Chavez |        -        |    Revisión técnica    |
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
> |    Fecha    | Versión | Cambio                |    Autor    |
> | :----------: | :------: | --------------------- | :---------: |
> |  28/06/2025  |   1.0   | Creación inicial     | Juan Chavez |
> | [DD/MM/YYYY] |   1.1   | [Descripción cambio] |  [Nombre]  |

---

**📅 Última Actualización:** 28/06/2025 06:12PM
**✅ Estado de Revisión:** Aprobado
**👤 Revisado por:** Juan Chavez - Lider Técnico
