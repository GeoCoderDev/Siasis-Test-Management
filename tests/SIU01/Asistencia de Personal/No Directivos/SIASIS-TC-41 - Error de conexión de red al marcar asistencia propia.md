# 🧪 Test Case: SIASIS-TC-41 - Error de conexión de red al marcar asistencia propia

> [!IMPORTANT]
> **ID del Test Case:** SIASIS-TC-41
> **Fecha de Creación:** 06/07/2025
> **Autor:** Juan Chavez
> **Última Actualización:** **06/07/2025**
> **Estado:** 🟢 Ready

---

## 📋 Información General

> [!NOTE]
>
> ### 🔖 Metadatos del Test
>
> | Campo                     |                                     Valor                                     |
> | ------------------------- | :---------------------------------------------------------------------------: |
> | **ID Test Case**    |                                 SIASIS-TC-41                                 |
> | **Nombre**          |             Error de conexión de red al marcar asistencia propia             |
> | **Módulo/Feature** | Registro de Asistencia Propia con Gelocalización para usuarios no Directivos |
> | **Epic/User Story** |                                  No se tiene                                  |
> | **Tipo de Prueba**  |                                 🔧 Funcional                                 |
> | **Nivel de Prueba** |                                   🌐 System                                   |
> | **Prioridad**       |                                   🟢 Medium                                   |
> | **Severidad**       |                                   🟡 Major                                   |
> | **Automatizable**   |                                    ✅ Sí                                    |
> | Automatizado              |                                     ❌ No                                     |

---

> [!TIP]
>
> ### 🏷️ Tags y Categorización
>
> **Tags principales:**
>
> ```gherkin
> @SIASIS-TC-41 @regresion @network-error @mobile
> ```
>
> **Tags por componente:**
>
> ```gherkin
> @SIU01 @API03 @RDP05
> ```
>
> **Tags por rol:**
>
> ```gherkin
> @profesor-primaria @profesor-secundaria @auxiliar @personal-administrativo
> ```

---

## 🎯 Descripción y Objetivos

> [!IMPORTANT]
>
> ### 📖 Descripción del Test Case
>
> Este test validará que el sistema maneja robustamente los problemas de conectividad que pueden ocurrir durante el proceso de marcado de asistencia. Se verificará que el sistema detecte problemas de red, informe claramente al usuario sobre la situación, proporcione opciones para reintentar, y no genere registros parciales o corruptos debido a fallas de comunicación.

> [!NOTE]
>
> ### 🎯 Objetivo Principal
>
> **Objetivo:** Verificar que el sistema maneja adecuadamente los problemas de conectividad durante el proceso de marcado de asistencia.
>
> **Criterio de Éxito:** El sistema muestra modal de "Error de Conexión", sugiere verificar internet, permite reintentar y no registra asistencia hasta resolver conectividad

---

## 🔧 Configuración Técnica

> [!WARNING]
>
> ### 💻 Tecnología y Componentes
>
> | Aspecto                         |                Detalle                |
> | ------------------------------- | :-----------------------------------: |
> | **Tecnología Principal** |                🌐 Web                |
> | **Navegadores**           |             Chrome, Edge             |
> | **Dispositivos**          |            Desktop, Mobile            |
> | **Sistemas Operativos**   |           Windows, Android           |
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
> | **API03** | API para obtención de hora real UTC                                                                                                                              | ✅ |    |
> | **TPS01** | Tareas programadas con Scripts                                                                                                                                    |    | ❌ |
> | **EMCS01** | Ejecutor múltiple de consultas SQL de Escritura de API01 hacia RDP02 y RDP03                                                                                     |    | ❌ |
> | **EMCN01** | Ejecutor múltiple de consultas SQL de escritura para API02 hacia RDP03                                                                                           |    | ❌ |
> | **RDP01** | Repositorio de Datos Persistentes solo para Archivos del Sistema en General (Fotos de Perfil, Excels de Asistencia, Backups, etc) ➡️**Google Drive**      |    | ❌ |
> | **RDP02** | Repositorio de Datos Persistentes para Datos Relacionados a Personal del Colegio (Directivos, Auxiliares, Profesores, etc) ➡️ PostgreSQL                        |    | ❌ |
> | **RDP03** | Repositorio de Datos Persistentes para Datos Relacionados a Responsables (Padres de Familia/Apoderados) ➡️ MongoDB                                              |    | ❌ |
> | **RDP04** | Repositorio de Datos Persistentes para JSONs con Información de Datos de Asistencia del Día Actual (Se actualiza todos los días por TPS01) ➡️ Blob de Vercel |    | ❌ |
> | **RDP05** | Repositorio de Datos Persistentes para Asistencias Tomadas a lo largo del día actual exclusivamente ➡️ Redis                                                   | ✅ |    |
> |  **SS01**  | Servidor de Sockets para operaciones en tiempo real                                                                                                               |    | ❌ |
> |  **SE01**  | Servicio Externo de Correo Electrónico por GMAIL de Google                                                                                                       |    | ❌ |

---

## 📝 Definición en Gherkin

> [!TIP]
>
> ### 🥒 Scenario en Gherkin
>
> ```gherkin
> Feature: Registro de Asistencia Propia con Gelocalización para usuarios no Directivos
>   Como personal no Directivo del colegio IE20935 (Profesores, Auxiliares, Personal Administrativo)
>   Quiero poder registrar mi propia asistencia desde mi dispositivo móvil
>   Para no depender de usuarios con rol Directivo para marcar mi asistencia de entrada y salida
>
> Background:
>   Given que el sistema está funcionando correctamente
>   And todos los servicios están disponibles
>   And soy un usuario no directivo con cuenta activa
>   And tengo horario laboral configurado para el día actual
>
> @SIASIS-TC-41 @regression @network-error @mobile
> Scenario: Error de conexión de red
>   Given que estoy usando mi dispositivo móvil
>   And me encuentro dentro del perímetro del colegio
>   And me encuentro en mi rango horario laboral
>   And tengo conexión de red inestable o nula
>   And he iniciado sesión correctamente
>   When accedo a la interfaz principal y hago clic en el botón flotante
>   And hago clic en "Registrar Entrada" o "Registrar Salida"
>   Then me aparece un modal de "Error de Conexión"
>   And el modal sugiere verificar mi conexión a internet
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
> - 📊 **Datos específicos:** Credenciales de usuarios con rol de personal del colegio (No directivos)

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
> | **Directivo**         |    | ❌ |
> | **Profesor Primaria** | ✅ |    |
> | **Auxiliar**          | ✅ |    |
> | Profesor Secundaria         | ✅ |    |
> | Tutor                       | ✅ |    |
> | Personal Administrativo     | ✅ |    |
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
> | **Autor del Test** | Juan Chavez |        -        | Creación y mantenimiento |
> | **Product Owner** | Juan Chavez |        -        | Validación de criterios |
> |   **Tech Lead**   | Juan Chavez |        -        |    Revisión técnica    |
> |  **Dev Asignado**  | Juan Chavez |        -        |    Corrección de bugs    |

---

## 📝 Notas y Observaciones

> [!NOTE]
>
> ### 💡 Notas Importantes
>
> - Aun falta especificar los Test Cases relacionados
> - [Consideración especial]
>
> ### 🔄 Historial de Cambios
>
> |    Fecha    | Versión | Cambio                |    Autor    |
> | :----------: | :------: | --------------------- | :---------: |
> |  06/07/2025  |   1.0   | Creación inicial     | Juan Chavez |
> | [DD/MM/YYYY] |   1.1   | [Descripción cambio] |  [Nombre]  |

---

**📅 Última Actualización:** 06/07/2025 05:35PM
**✅ Estado de Revisión:** Aprobado
**👤 Revisado por:** Juan Chavez - Lider Técnico
