# 🧪 Test Case: SIASIS-TC-60 - Validar el metodo GET para obtener las asistencias por cada Rol

> [!IMPORTANT]
> **ID del Test Case:** SIASIS-TC-60
> **Fecha de Creación:** 18/07/2025
> **Autor:** Jose Gil
> **Última Actualización:** 18/07/2025
> **Estado:** 🟢 Ready

---

## 📋 Información General

> [!NOTE]
>
> ### 🔖 Metadatos del Test
>
>
> | Campo               |                                    Valor                                    |
> | --------------------- | :----------------------------------------------------------------------------: |
> | **ID Test Case**    |                                 SIASIS-TC-60                                 |
> | **Nombre**          | Validar el metodo GET para obtener las asistencias por cada Rol |
> | **Módulo/Feature** |                                AsistenciaHoy                                |
> | **Epic/User Story** |                                 No se tiene                                 |
> | **Tipo de Prueba**  |                                 🔧 Funcional                                 |
> | **Nivel de Prueba** |                                  🌐 System                                  |
> | **Prioridad**       |                                   🟡 High                                   |
> | **Severidad**       |                                   🟡 Major                                   |
> | **Automatizable**   |                                    ✅ SI                                    |
> | Automatizado        |                                    ✅ SI                                    |

---

> [!TIP]
>
> ### 🏷️ Tags y Categorización
>
> **Tags principales:**
>
> ```gherkin
> @SIASIS-TC-60
> ```
>
> **Tags por componente:**
>
> ```gherkin
> @API-SIU01
> ```
>
> **Tags por rol:**
>
> ```gherkin
> @AsistenciaHoy-Roles        
> ```

---

## 🎯 Descripción y Objetivos

> [!IMPORTANT]
>
> ### 📖 Descripción del Test Case
>
> Este test valida que el servidor responda correctamente a una solicitud GET para que obtener los datos de asistencias por cada rol.

> [!NOTE]
>
> ### 🎯 Objetivo Principal
>
> **Objetivo:** Verificar que el método GET funcione correctamente para obtener los datos de asistencia por cada rol .
>
> **Criterio de Éxito:** <br>
> Código de estado: 200 OK <br>

---

## 🔧 Configuración Técnica

> [!WARNING]
>
> ### 💻 Tecnología y Componentes
>
>
> | Aspecto                   | Detalle |
> | --------------------------- | --------- |
> | **Tecnología Principal** | API     |
> | **Dispositivos**          | Desktop |
> | **Sistemas Operativos**   | Windows |

> [!CAUTION]
>
> ### 🏗️ Componentes Involucrados
>
>
> | Componente | Descripción                                                                                                                                                      | Si | No |
> | :----------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---- | ---- |
> | **SIU01** | Servidor de Interfaces de Usuario                                                                                                                                 | ✅ |    |
> | **API01** | API para personal del colegio (Directivos, Auxiliares, Profesores, etc)                                                                                           | ✅ |    |
> | **API02** | API para padres de Familia                                                                                                                                        |    | ❌ |
> | **API03** | API para obtención de hora real UTC                                                                                                                              |    | ❌ |
> | **TPS01** | Tareas programadas con Scripts                                                                                                                                    |    | ❌ |
> | **EMCS01** | Ejecutor múltiple de consultas SQL de Escritura de API01 hacia RDP02 y RDP03                                                                                     |    | ❌ |
> | **EMCN01** | Ejecutor múltiple de consultas SQL de escritura para API02 hacia RDP03                                                                                           |    | ❌ |
> | **RDP01** | Repositorio de Datos Persistentes solo para Archivos del Sistema en General (Fotos de Perfil, Excels de Asistencia, Backups, etc) ➡️**Google Drive**            |    | ❌ |
> | **RDP02** | Repositorio de Datos Persistentes para Datos Relacionados a Personal del Colegio (Directivos, Auxiliares, Profesores, etc) ➡️ PostgreSQL                        |    | ❌ |
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
>    @SIASIS-TC-60 @API-SIU01 @AsistenciaHoy-Roles        
>    Scenario Outline: Marcar asistencia y luego consultar asistencias para un rol específico
>        Given path '/api/asistencia-hoy/consultar-asistencias-tomadas'
>        And param TipoAsistencia = 'personal'
>        And param Actor = <actor>
>        And param ModoRegistro = 'E'
>        When method get
>        Then status 200
>        Examples:
>            | actor |
>            | 'D'     |
>            | 'A'     |
>            | 'PP'    |
>            | 'PS'    |
>            | 'PA'    |
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
> - 📊 **Datos específicos:** Credenciales **_(Nombre de Usuario y Contraseña, Nombres, Apellidos ,Token,Genero ,Rol y ID de google foto)_** de todos los roles

---

## 📊 Métricas y Performance

> [!INFO]
>
> ### ⏱️ Criterios de Performance (si aplica)
>
>
> | Métrica                | Valor Esperado | Crítico      |
> | ------------------------- | ---------------- | --------------- |
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
>
> | Rol                         | SI | NO |
> | ----------------------------- | ---- | ---- |
> | **Directivo**               |  ✅  |  |
> | **Profesor Primaria**       |  ✅  |  |
> | **Auxiliar**                |  ✅  |  |
> | **Profesor Secundaria**     |  ✅  |  |
> | **Tutor**                   | ✅   |  |
> | **Personal Administrativo** |  ✅  |  |
> | **Responsable**             |    |❌  |

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
>
> |        Rol        |   Nombre   | Email / Celular |      Responsabilidad      |
> | :------------------: | :-----------: | :---------------: | :-------------------------: |
> | **Autor del Test** |  Jose Gil  |        -        | Creación y mantenimiento |
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
>
> |    Fecha    | Versión | Cambio                |    Autor    |
> | :------------: | :--------: | ----------------------- | :-----------: |
> |  28/06/2025  |   1.0   | Creación inicial     | Juan Chavez |
> | [DD/MM/YYYY] |   1.1   | [Descripción cambio] |  [Nombre]  |

---

**📅 Última Actualización:** 18/07/2025 01:26AM
**✅ Estado de Revisión:** Aprobado
**👤 Revisado por:** Juan Chavez - Lider Técnico
