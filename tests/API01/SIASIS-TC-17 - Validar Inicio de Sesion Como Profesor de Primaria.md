# 🧪 Test Case: SIASIS-TC-17 - Validar Inicio de Sesión de Sesión Exitoso para rol de Profesor de Primaria

> [!IMPORTANT]
> **ID del Test Case:** SIASIS-TC-17
> **Fecha de Creación:** 13/07/2025
> **Autor:** Jose Gil
> **Última Actualización:** 13/07/2025
> **Estado:** 🟢 Ready

---

## 📋 Información General

> [!NOTE]
>
> ### 🔖 Metadatos del Test
>
> | Campo                     |                                                                        Valor                                                                        |
> | ------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------: |
> | **ID Test Case**    |                                                                    SIASIS-TC-17                                                                   |
> | **Nombre**          | Validar Inicio de Sesión de Sesión Exitoso <br> para rol de Profesor de Primaria |
> | **Módulo/Feature** |                                                           Login                                                       |
> | **Epic/User Story** |                                                                     No se tiene                                                                     |
> | **Tipo de Prueba**  |                                                                🔧 Funcional                                                              |
> | **Nivel de Prueba** |                                                                      🌐 System                                                                      |
> | **Prioridad**       |                                                                       🟡 High                                                                       |
> | **Severidad**       |                                                                      🟡 Major                                                                      |
> | **Automatizable**   |                                                                       ✅ SI                                                                       |
> | Automatizado              |                                                                       ✅ SI                                                                       |

---

> [!TIP]
>
> ### 🏷️ Tags y Categorización
>
> **Tags principales:**
>
> ```gherkin
> @SIASIS-TC-17
> ```
>
> **Tags por componente:**
>
> ```gherkin
> @API01
> ```
>
> **Tags por rol:**
>
> ```gherkin
> @Iniciar-Sesion-Profesor-Primaria
> ```

---

## 🎯 Descripción y Objetivos

> [!IMPORTANT]
>
> ### 📖 Descripción del Test Case
>
> Este test evalúa el flujo de autenticación exitoso para el rol de Profesor de Primaria mediante la validación del inicio de sesión a través de la API del sistema.

> [!NOTE]
>
> ### 🎯 Objetivo Principal
>
> **Objetivo:** Verificar que los usuarios con el rol de Profesor de Primaria puedan iniciar sesión correctamente en el sistema
>
> **Criterio de Éxito:** <br>
> Código de estado: 200 OK <br>
> Mensaje: "Inicio de sesión exitoso" <br>
> Campo success: true

---

## 🔧 Configuración Técnica

> [!WARNING]
>
> ### 💻 Tecnología y Componentes
>
> | Aspecto                         | Detalle                               |
> | ------------------------------- | ------------------------------------- |
> | **Tecnología Principal** | API   |
> | **Dispositivos**          | Desktop               |
> | **Sistemas Operativos**   | Windows                     |

> [!CAUTION]
>
> ### 🏗️ Componentes Involucrados
>
> |    Componente    | Descripción                                                                                                                                                      | Si | No |
> | :--------------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | -- | -- |
> | **SIU01** | Servidor de Interfaces de Usuario                                                                                                                                 |  | ❌  |
> | **API01** | API para personal del colegio (Directivos, Auxiliares, Profesores, etc)                                                                                           |✅  |  |
> | **API02** | API para padres de Familia                                                                                                                                        |    | ❌ |
> | **API03** | API para obtención de hora real UTC                                                                                                                              |    | ❌ |
> | **TPS01** | Tareas programadas con Scripts                                                                                                                                    |    | ❌ |
> | **EMCS01** | Ejecutor múltiple de consultas SQL de Escritura de API01 hacia RDP02 y RDP03                                                                                     |    | ❌ |
> | **EMCN01** | Ejecutor múltiple de consultas SQL de escritura para API02 hacia RDP03                                                                                           |    | ❌ |
> | **RDP01** | Repositorio de Datos Persistentes solo para Archivos del Sistema en General (Fotos de Perfil, Excels de Asistencia, Backups, etc) ➡️**Google Drive**      |    | ❌ |
> | **RDP02** | Repositorio de Datos Persistentes para Datos Relacionados a Personal del Colegio (Directivos, Auxiliares, Profesores, etc) ➡️ PostgreSQL                        |    | ❌ |
> | **RDP03** | Repositorio de Datos Persistentes para Datos Relacionados a Responsables (Padres de Familia/Apoderados) ➡️ MongoDB                                              |    | ❌ |
> | **RDP04** | Repositorio de Datos Persistentes para JSONs con Información de Datos de Asistencia del Día Actual (Se actualiza todos los días por TPS01) ➡️ Blob de Vercel |    | ❌ |
> | **RDP05** | Repositorio de Datos Persistentes para Asistencias Tomadas a lo largo del día actual exclusivamente ➡️ Redis                                                   |  |❌    |
> |  **SS01**  | Servidor de Sockets para operaciones en tiempo real                                                                                                               |  |❌    |
> |  **SE01**  | Servicio Externo de Correo Electrónico por GMAIL de Google                                                                                                       |    | ❌ |

---

## 📝 Definición en Gherkin

> [!TIP]
>
> ### 🥒 Scenario en Gherkin
>
> ```gherkin
> Feature: Inicio de Sesion de Profesor de Primaria
>  Como Profesor de Primaria
>  Quiero poder iniciar sesión exitosamente
>  Para acceder a las funcionalidades correspondientes 
>   a  mi rol
>
>   Background:
>     Given tengo acceso a la API01 
>
>   @SIASIS-TC-17 @API01 @Iniciar-Sesion-Personal-Administrativo
>   Scenario: Iniciar Sesion con usuario de Profesor de Primaria
>   Given El usuario tiene credenciales válidas para el rol 
>   When El usuario realiza la solicitud POST 
>   Then La API debe devolver un código de estado 200 OK
>   And El mensaje de respuesta debe indicar "Inicio de sesión exitoso"
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
> - 📊 **Datos específicos:** Credenciales **_(Nombre de Usuario y Contraseña)_** de un usuario con Rol de Profesor de Primaria

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
> - 🔗 **Relacionado:** No hay Relacion

---

## 🎭 Roles y Permisos

> [!CAUTION]
>
> ### 👥 Roles Involucrados
>
> | Rol                         | SI | NO |
> | --------------------------- | -- | -- |
> | **Directivo**         |  |   ❌ |
> | **Profesor Primaria** |  ✅  |  |
> | **Auxiliar**          |    | ❌ |
> | **Profesor Secundaria**         |    | ❌ |
> | **Tutor**                       |    | ❌ |
> | **Personal Administrativo**     |    |❌  |
> | **Responsable**       |    | ❌ |

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
>
> [!INFO]
>
> ### 👥 Responsables
>
> |           Rol           |   Nombre   | Email / Celular |      Responsabilidad      |
> | :----------------------: | :---------: | :-------------: | :-----------------------: |
> | **Autor del Test** | Jose Gil |        -        | Creación y mantenimiento |
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

**📅 Última Actualización:** 13/07/2025 13:20PM
**✅ Estado de Revisión:** Aprobado
**👤 Revisado por:** Juan Chavez - Lider Técnico
