# 🧪 Test Case: SIASIS-TC-11 - Validar la no sincronizacion al tomar asistencia de personal por parte de directivo en varios dispositivos con diferente seccion seleccionada

> [!IMPORTANT]
> **ID del Test Case:** SIASIS-TC-11
> **Fecha de Creación:** 07/07/2025
> **Autor:** Andry Diego
> **Última Actualización:** 07/07/2025
> **Estado:** 🟢 Ready

---

## 📋 Información General

> [!NOTE]
>
> ### 🔖 Metadatos del Test
>
> | Campo                     |                                                                        Valor                                                                        |
> | ------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------: |
> | **ID Test Case**    |                                                                    SIASIS-TC-11                                                                    |
> | **Nombre**          | VValidar la no sincronizacion al tomar asistencia de personal por<br />parte de directivo en varios dispositivos con diferente seccion seleccionada |
> | **Módulo/Feature** |                                                           Toma de Asistencia de Personal                                                           |
> | **Epic/User Story** |                                                                     No se tiene                                                                     |
> | **Tipo de Prueba**  |                                                                🔧 Funcional\|🌐 E2E                                                                |
> | **Nivel de Prueba** |                                                                      🌐 System                                                                      |
> | **Prioridad**       |                                                                       🟡 High                                                                       |
> | **Severidad**       |                                                                      🟡 Major                                                                      |
> | **Automatizable**   |                                                                       ❌ No                                                                       |
> | Automatizado              |                                                                       ❌ No                                                                       |

---

> [!TIP]
>
> ### 🏷️ Tags y Categorización
>
> **Tags principales:**
>
> ```gherkin
> @SIASIS-TC-11
> ```
>
> **Tags por componente:**
>
> ```gherkin
> @SIU01 @SS01 @RDP05
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
> Este es un test para verificar que la funcionalidad de marcado de asistencia de personal de manera sincronizada en varios dipositivos no funcione cuando en los diferentes dispositivos se tienen seleccionadas diferentes secciones de toma de asistencia.

> [!NOTE]
>
> ### 🎯 Objetivo Principal
>
> **Objetivo:** Validar que un usuario o usuarios con rol Directivo no pueden marcar la asistencia del Personal en varios dispositivos de manera sincronizada cuando en los diferentes dispositivos se tienen seleccionadas diferentes secciones de toma de asistencia.
>
> **Criterio de Éxito:** Las asistencias marcadas en un dispositivo con cierta seccionada no se marcan en otros dispositivos con secciones seleccionada diferentes.

---

## 🔧 Configuración Técnica

> [!WARNING]
>
> ### 💻 Tecnología y Componentes
>
> | Aspecto                         | Detalle                               |
> | ------------------------------- | ------------------------------------- |
> | **Tecnología Principal** | 🌐 Web\| 🖥️ Desktop \| 🔗Sockets   |
> | **Navegadores**           | Chrome, Edge                          |
> | **Dispositivos**          | Desktop, Mobile, Tablet               |
> | **Sistemas Operativos**   | Windows, Android                      |
> | **Resoluciones**          | 1920x1080, 1366x768, 375x667 (mobile) |

> [!CAUTION]
>
> ### 🏗️ Componentes Involucrados
>
> |    Componente    | Descripción                                                                                                                                                      | Si | No |
> | :--------------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | -- | -- |
> | **SIU01** | Servidor de Interfaces de Usuario                                                                                                                                 | ✅ |    |
> | **API01** | API para personal del colegio (Directivos, Auxiliares, Profesores, etc)                                                                                           |    | ❌ |
> | **API02** | API para padres de Familia                                                                                                                                        |    | ❌ |
> | **API03** | API para obtención de hora real UTC                                                                                                                              |    | ❌ |
> | **TPS01** | Tareas programadas con Scripts                                                                                                                                    |    | ❌ |
> | **EMCS01** | Ejecutor múltiple de consultas SQL de Escritura de API01 hacia RDP02 y RDP03                                                                                     |    | ❌ |
> | **EMCN01** | Ejecutor múltiple de consultas SQL de escritura para API02 hacia RDP03                                                                                           |    | ❌ |
> | **RDP01** | Repositorio de Datos Persistentes solo para Archivos del Sistema en General (Fotos de Perfil, Excels de Asistencia, Backups, etc) ➡️**Google Drive**      |    | ❌ |
> | **RDP02** | Repositorio de Datos Persistentes para Datos Relacionados a Personal del Colegio (Directivos, Auxiliares, Profesores, etc) ➡️ PostgreSQL                        |    | ❌ |
> | **RDP03** | Repositorio de Datos Persistentes para Datos Relacionados a Responsables (Padres de Familia/Apoderados) ➡️ MongoDB                                              |    | ❌ |
> | **RDP04** | Repositorio de Datos Persistentes para JSONs con Información de Datos de Asistencia del Día Actual (Se actualiza todos los días por TPS01) ➡️ Blob de Vercel |    | ❌ |
> | **RDP05** | Repositorio de Datos Persistentes para Asistencias Tomadas a lo largo del día actual exclusivamente ➡️ Redis                                                   | ✅ |    |
> |  **SS01**  | Servidor de Sockets para operaciones en tiempo real                                                                                                               | ✅ |    |
> |  **SE01**  | Servicio Externo de Correo Electrónico por GMAIL de Google                                                                                                       |    | ❌ |

---

## 📝 Definición en Gherkin

> [!TIP]
>
> ### 🥒 Scenario en Gherkin
>
> ```gherkin
> Feature: Toma de Asistencia de Personal por Parte de Directivo en varios dispositivos
>   Como Directivo
>   Quiero poder tomar la asistencia del personal de la institucion en varios dispositivos a la vez
>   Para tomar la asistencia del personal en varios dispositivos a la vez 
>
>   Background:
>     Given Estoy en la página de login 
>     And he iniciado sesion como Directivo en varios dispositivos a la vez
>
>   @SIASIS-TC-10 @SIU01 @SS01 @RDP05 @directivo
>   Scenario: Directivo marca la asistencia de un personal en varios dispositivos a la vez
>     Given he seleccionado en todos los dispositivos diferentes tipos de registro(Entrada o Salida) para diferentes Roles
>     When marco la asistencia de cualquier personal en uno de los dispositivos
>     Then la asistencia solo se marca en ese dispositvo
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
> - 📊 **Datos específicos:** Credenciales **_(Nombre de Usuario y Contraseña)_** de un usuario con Rol de Directivo

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
> - 📋 **Pre-requisito:** No hay Pre-requitsitos
> - 🔄 **Dependiente:** No hay dependencias
> - 🔗 **Relacionado:** SIASIS-TC-10 (Caso positivo para marcado de toma de asistencia en varios dispositivos)

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
> | **Autor del Test** | Andry Diego |        -        | Creación y mantenimiento |
> | **Product Owner** | Juan Chavez |        -        | Validación de criterios |
> |   **Tech Lead**   | Juan Chavez |        -        |    Revisión técnica    |
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
> |    Fecha    | Versión | Cambio                |    Autor    |
> | :----------: | :------: | --------------------- | :---------: |
> |  28/06/2025  |   1.0   | Creación inicial     | Juan Chavez |
> | [DD/MM/YYYY] |   1.1   | [Descripción cambio] |  [Nombre]  |

---

**📅 Última Actualización:** 07/07/2025 01:26AM
**✅ Estado de Revisión:** Aprobado
**👤 Revisado por:** Juan Chavez - Lider Técnico
