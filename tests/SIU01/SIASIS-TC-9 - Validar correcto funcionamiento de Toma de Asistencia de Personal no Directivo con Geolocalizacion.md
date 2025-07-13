# 🧪 Test Case: SIASIS-TC-9 - Validar correcto funcionamiento de Toma de Asistencia de Personal no Directivo con Geolocalización

> [!IMPORTANT]
> **ID del Test Case:** SIASIS-TC-9
> **Fecha de Creación:** 03/07/2025
> **Autor:** Juan Chavez
> **Última Actualización:** **03/07/2025**
> **Estado:** 🟢 Ready

---

## 📋 Información General

> [!NOTE]
>
> ### 🔖 Metadatos del Test
>
> | Campo                     |                                                Valor                                                |
> | ------------------------- | :-------------------------------------------------------------------------------------------------: |
> | **ID Test Case**    |                                             SIASIS-TC-9                                             |
> | **Nombre**          | Validar correcto funcionamiento de Toma de Asistencia de Personal no Directivo con Geolocalización |
> | **Módulo/Feature** |                      Toma de Asistencia Individual para Personal no Directivo                      |
> | **Epic/User Story** |                                             No se tiene                                             |
> | **Tipo de Prueba**  |                                 🔧 Funcional\| 🎨 UI/UX \| 🌐 E2E                                 |
> | **Nivel de Prueba** |                                      🌐 System\| ✅ Acceptance                                      |
> | **Prioridad**       |                                               🟡 High                                               |
> | **Severidad**       |                                              🟡 Major                                              |
> | **Automatizable**   |                                                ❌ No                                                |

---

> [!TIP]
>
> ### 🏷️ Tags y Categorización
>
> **Tags principales:**
>
> ```gherkin
> @smoke @regression @geolocation @web @mobile
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
> @profesor-primaria @profesor-secundaria @auxiliar @personal-administrativo
> ```

---

## 🎯 Descripción y Objetivos

> [!IMPORTANT]
>
> ### 📖 Descripción del Test Case
>
> Este test validara todos los casos posibles a siceder al momento de que un personal no directivo(Profesor de Primaria, Profesor de Secundaria, Auxiliar o Personal Administrativo) registre su asistencia desde su propio dispositivo con Geolocalización activada.

> [!NOTE]
>
> ### 🎯 Objetivo Principal
>
> **Objetivo:** [Describir qué funcionalidad o comportamiento específico se va a verificar]
>
> **Criterio de Éxito:** [Definir claramente cuándo el test se considera exitoso]

---

## 🔧 Configuración Técnica

> [!WARNING]
>
> ### 💻 Tecnología y Componentes
>
> | Aspecto                         | Detalle                               |
> | ------------------------------- | ------------------------------------- |
> | **Tecnología Principal** | 🌐 Web                                |
> | **Navegadores**           | Chrome, Edge                          |
> | **Dispositivos**          | Desktop, Mobile                       |
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
> @smoke @auth @web @SIU01 @API01
> Feature: Toma de Asistencia de Personal no Directivo con Gelocalización Activada
>   Como personal no Directivo del colegio IE20935
>   Quiero Quiero poder tomar mi propia asistencia en el sistema ingresando con mi cuenta desde mi propio dispositivo movil
>   Para así no depender de la directora para poder registrar mi asistencia (entrada y salida) en el sistema
>
> Background:
>   Given el usuario 
>   And el sistema está funcionando correctamente
>   And todos los servicios están disponibles
>
> @SIASIS-TC-9 @smoke @regression @geolocation @web @mobile @profesor-primaria @profesor-secundaria @auxiliar @personal-administrativo
> Scenario Outline: Personal no Directivo del Colegio toma su asistencia con Geolocalización Activada
>   Given que <situacion>
>   And he iniciado sesion con mis respectivas credenciales
>   And me encuentro en la interfaz de bienvenida segun mi rol 
>   And he dado click en el boton flotante de registrar asistencia de Entrada o Salida(Segun la Hora)
>   And me aparece en pantalla el modal de Marcado de Asistencia
>   When hago click en el boton Registrar asistencia
>   Then me aparece el modal <modal_resultante>
>
>   Examples:
>     | situacion                                                                       | modal_resultante                                     |
>     | Me encuentro dentro del perimetro del Colegio con GPS y permisos habillitados   | Modal de Registro Exitoso                            |
>     | Estoy usando mi laptop o algun dispositivo que no sea un celular                | Modal de Solo uso de Celulares para Geolocaclizacion |
>     | Tengo mi celular con GPS Desactivado o Permisos no Condedidos                   | Modal de Solicitud de Permisos o Activación de GPS   |
>     | No me encuentro dentro del perimetro del Colegio con GPS y permisos habilitados | Modal de Te encuentras fuera del colegio             |
>     | El sistema ha estado fallando ultimamente                                       | Modal de Error generico                              |
>     | Mi red es inestable o nula                                                      | Modal de Error de Conexion                           |
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
> - Aun falta agregar el Rol de Responsable
> - Aun falta especificar los Test Cases relacionados
> - [Consideración especial]
>
> ### 🔄 Historial de Cambios
>
> |    Fecha    | Versión | Cambio                |    Autor    |
> | :----------: | :------: | --------------------- | :---------: |
> |  03/07/2025  |   1.0   | Creación inicial     | Juan Chavez |
> | [DD/MM/YYYY] |   1.1   | [Descripción cambio] |  [Nombre]  |

---

**📅 Última Actualización:** 03/07/2025 05:00PM
**✅ Estado de Revisión:** Aprobado
**👤 Revisado por:** Juan Chavez - Lider Técnico
