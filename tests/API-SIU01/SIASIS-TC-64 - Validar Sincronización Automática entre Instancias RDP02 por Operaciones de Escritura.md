# 🧪 Test Case: SIASIS-TC-64 - Validar Sincronización Automática entre Instancias RDP02 por Operaciones de Escritura

> [!IMPORTANT] > **ID del Test Case:** SIASIS-TC-64
> **Fecha de Creación:** 16/07/2025
> **Autor:** Andry Diego
> **Última Actualización:** 16/07/2025
> **Estado:** 🟢 Ready

---

## 📋 Información General

> [!NOTE]
>
> ### 🔖 Metadatos del Test
>
> | Campo               | Valor                                                                                 |
> | ------------------- | ------------------------------------------------------------------------------------- |
> | **ID Test Case**    | SIASIS-TC-64                                                                          |
> | **Nombre**          | Validar Sincronización Automática entre Instancias RDP02 por Operaciones de Escritura |
> | **Módulo/Feature**  | Sincronización de Bases de Datos                                                      |
> | **Epic/User Story** | SIASIS-TP-9                                                                           |
> | **Tipo de Prueba**  | 🔧 Funcional \| 🔗 Integration                                                        |
> | **Nivel de Prueba** | 🌐 System                                                                             |
> | **Prioridad**       | 🔴 Critical                                                                           |
> | **Severidad**       | 🔴 Blocker                                                                            |
> | **Automatizable**   | ✅ Sí                                                                                 |
> | **Automatizada**    | ⏳ Futuro                                                                             |

---

> [!TIP]
>
> ### 🏷️ Tags y Categorización
>
> **Tags principales:**
>
> ```gherkin
> @SIASIS-TC-64 @database-replication @automatic-sync-trigger @user-data-modification
> ```
>
> **Tags por componente:**
>
> ```gherkin
> @EMCS01 @RDP02 @SIU01 @API01
> ```
>
> **Tags por ambiente:**
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
> Este test valida el proceso automático de sincronización entre las 3 instancias de PostgreSQL (RDP02) cuando un usuario realiza una operación de escritura en el sistema web. Se verifica que el job de replicación se ejecute automáticamente vía GitHub Actions (EMCS01) y que los datos se mantengan consistentes en todas las instancias.

> [!NOTE]
>
> ### 🎯 Objetivo Principal
>
> **Objetivo:** Verificar que las operaciones de escritura realizadas en una instancia principal de RDP02 se repliquen automáticamente a las instancias secundarias mediante el sistema EMCS01, manteniendo la consistencia de datos entre todas las instancias.
>
> **Criterio de Éxito:**
>
> - Operación de escritura ejecutada exitosamente en instancia principal
> - Job de replicación disparado automáticamente en GitHub Actions
> - Datos replicados correctamente en todas las instancias secundarias
> - Consistencia de datos verificada en las 3 instancias RDP02

---

## 🔧 Configuración Técnica

> [!WARNING]
>
> ### 💻 Tecnología y Componentes
>
> | Aspecto                  | Detalle                                    |
> | ------------------------ | ------------------------------------------ |
> | **Tecnología Principal** | 🔌 API \| 💾 Database \| 🖥️ GitHub Actions |
> | **Navegadores**          | Chrome (para operaciones web)              |
> | **Dispositivos**         | Desktop, Server                            |
> | **Sistemas Operativos**  | Linux (Ubuntu), Windows                    |

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
> | **EMCS01** | Ejecutor múltiple de consultas SQL de Escritura de API01 hacia RDP02 y RDP03                                                                                     | ✅ |    |
> | **EMCN01** | Ejecutor múltiple de consultas NoSQL de escritura para API02 hacia RDP03                                                                                         |    | ❌ |
> | **RDP01** | Repositorio de Datos Persistentes solo para Archivos del Sistema en General (Fotos de Perfil, Excels de Asistencia, Backups, etc) ➡️**Google Drive**      |    | ❌ |
> | **RDP02** | Repositorio de Datos Persistentes para Datos Relacionados a Personal del Colegio (Directivos, Auxiliares, Profesores, etc) ➡️ PostgreSQL                        | ✅ |    |
> | **RDP02_INS1** | Instancia Secundaria 1 de PostgreSQL                                                                                                                          | ✅ |    |
> | **RDP02_INS2** | Instancia Secundaria 2 de PostgreSQL                                                                                                                          | ✅ |    |
> | **RDP03** | Repositorio de Datos Persistentes para Datos Relacionados a Responsables (Padres de Familia/Apoderados) ➡️ MongoDB                                              |    | ❌ |
> | **RDP04** | Repositorio de Datos Persistentes para JSONs con Información de Datos de Asistencia del Día Actual (Se actualiza todos los días por TPS01) ➡️ Blob de Vercel | |    | ❌ |
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
> @SIASIS-TC-64 @database-replication @automatic-sync-trigger @EMCS01 @RDP02
> Feature: Sincronización automática entre instancias RDP02 por operaciones de escritura
>   Como Líder Técnico del sistema SIASIS
>   Quiero que las operaciones de escritura se repliquen automáticamente entre instancias
>   Para mantener la consistencia de datos en todas las bases de datos RDP02
>
> Background:
>   Given existen 3 instancias de PostgreSQL RDP02 operativas
>   And el sistema EMCS01 está configurado y funcionando
>   And GitHub Actions está habilitado para el repositorio
>   And un usuario con permisos está autenticado en el sistema
>
> @SIASIS-TC-64 @critical @data-synchronization
> Scenario: Sincronización exitosa de operación de escritura entre instancias RDP02
>   Given un usuario de rol "Directivo" está autenticado en el sistema web
>   And las 3 instancias RDP02 están disponibles y sincronizadas
>   And el workflow "database-replication" está activo en GitHub Actions
>   When el usuario realiza una operación de escritura "modificar nombre de usuario"
>   And los datos se actualizan en la instancia principal RDP02
>   Then se debe disparar automáticamente un "Repository Dispatch" event
>   And el job "database-replication" se debe ejecutar en GitHub Actions
>   And el script "ReplicateTo***P02Instances.ts" se debe ejecutar correctamente
>   And los datos se deben replicar a la instancia "R***P02_INS1"
>   And los datos se deben replicar a la instancia "R***P02_INS2"
>   And la operación debe completarse en menos de 30 segundos
>   And los datos deben ser consistentes en las 3 instancias RDP02
>   And no debe haber pérdida de integridad referencial
> ```

---

## ⚙️ Precondiciones y Setup

> [!IMPORTANT]
>
> ### 🔧 Precondiciones
>
> #### Estado del Sistema:
>
> - ✅ 3 instancias RDP02 operativas y conectadas
> - ✅ GitHub Actions habilitado en repositorio EMCS01
> - ✅ Workflow "database-replication" configurado
> - ✅ Script de replicación deployado y funcional
> - ✅ Usuario con permisos de escritura autenticado
>
> #### Datos de Prueba Requeridos:
>
> - 📊 **Usuario de prueba:** Directivo con permisos de modificación
> - 📊 **Datos iniciales:** Registro existente en instancia principal
> - 📊 **Conectividad:** Red estable entre todas las instancias
> - ⏰ **Tiempo disponible:** Ventana de prueba sin operaciones concurrentes
>
> #### Configuración del Ambiente:
>
> - 🌐 **URLs:** Acceso a las 3 instancias RDP02
> - 🔧 **GitHub Actions:** Repository dispatch configurado
> - 🕘 **Timeouts:** Configurados según ambiente

---

## 📋 Pasos de Ejecución

> [!NOTE]
>
> ### 🚶‍♂️ Pasos Detallados
>
> | #   | Acción                                             | Datos de Entrada                  | Resultado Esperado                                  |
> | --- | -------------------------------------------------- | --------------------------------- | --------------------------------------------------- |
> | 1   | Verificar estado inicial de las 3 instancias RDP02 | Consulta de datos existentes      | Datos consistentes en las 3 instancias              |
> | 2   | Autenticarse en el sistema web                     | Credenciales de usuario Directivo | Acceso exitoso al sistema                           |
> | 3   | Navegar a la sección "MIS DATOS"                   | Interfaz web del sistema          | Página de datos personales cargada                  |
> | 4   | Hacer clic en "Editar Datos"                       | Botón de edición                  | Formulario de edición habilitado                    |
> | 5   | Modificar datos del usuario (ej: nombre)           | Nuevos datos a actualizar         | Cambios aplicados en formulario                     |
> | 6   | Guardar los cambios                                | Envío del formulario              | Mensaje "Datos actualizados correctamente"          |
> | 7   | Verificar trigger de GitHub Actions                | Monitoreo de workflows            | Job "database-replication" iniciado automáticamente |
> | 8   | Monitorear ejecución del workflow                  | Logs de GitHub Actions            | Script de replicación ejecutándose                  |
> | 9   | Validar replicación en instancia R\*\*\*P02_INS1   | Consulta a instancia secundaria 1 | Datos replicados correctamente                      |
> | 10  | Validar replicación en instancia R\*\*\*P02_INS2   | Consulta a instancia secundaria 2 | Datos replicados correctamente                      |
> | 11  | Verificar consistencia entre las 3 instancias      | Comparación de datos              | Datos idénticos en las 3 instancias                 |
> | 12  | Confirmar integridad referencial                   | Validación de relaciones FK       | Sin violaciones de integridad                       |

---

## ✅ Criterios de Aceptación

> [!SUCCESS]
>
> ### 🎯 Resultado Esperado Principal
>
> La operación de escritura realizada por el usuario se replica automáticamente en las 3 instancias RDP02 mediante el sistema EMCS01, manteniendo la consistencia de datos y la integridad referencial en tiempo menor a 30 segundos.

> [!TIP]
>
> ### ✅ Validaciones Específicas
>
> #### Validaciones Funcionales:
>
> - ✅ Operación de escritura ejecutada exitosamente en instancia principal
> - ✅ Repository dispatch event disparado automáticamente
> - ✅ Job "database-replication" ejecutado en GitHub Actions
> - ✅ Script de replicación completado sin errores
> - ✅ Datos replicados correctamente en R\*\*\*P02_INS1
> - ✅ Datos replicados correctamente en R\*\*\*P02_INS2
>
> #### Validaciones de UI/UX:
>
> - ✅ Interfaz web muestra mensaje de éxito al guardar
> - ✅ Datos actualizados visibles inmediatamente en la interfaz
> - ✅ Sin errores o interrupciones en la experiencia del usuario
>
> #### Validaciones de Datos:
>
> - ✅ Consistencia de datos entre las 3 instancias RDP02
> - ✅ Integridad referencial mantenida en todas las instancias
> - ✅ No hay pérdida de datos durante el proceso de replicación
> - ✅ Timestamps correctos en todos los registros replicados

---

## 🚫 Casos Negativos y Edge Cases

> [!WARNING]
>
> ### ⚠️ Escenarios de Error
>
> | Escenario                              | Acción                            | Resultado Esperado                         |
> | -------------------------------------- | --------------------------------- | ------------------------------------------ |
> | **Instancia secundaria no disponible** | Una instancia RDP02 está offline  | Error controlado, log de fallo, reintentos |
> | **Fallo en GitHub Actions**            | GitHub Actions no disponible      | Error registrado, operación en cola        |
> | **Timeout de replicación**             | Proceso excede tiempo límite      | Cancelación controlada, alerta enviada     |
> | **Datos corruptos**                    | Registro con formato inválido     | Validación previa, rollback automático     |
> | **Conflicto de concurrencia**          | Múltiples operaciones simultáneas | Manejo de locks, procesamiento secuencial  |

---

## 📊 Métricas y Performance

> [!INFO]
>
> ### ⏱️ Criterios de Performance
>
> | Métrica                                 | Valor Esperado | Crítico       |
> | --------------------------------------- | -------------- | ------------- |
> | **Tiempo Total de Sincronización**      | < 20 segundos  | < 30 segundos |
> | **Tiempo de Trigger**                   | < 5 segundos   | < 10 segundos |
> | **Tiempo de Replicación por Instancia** | < 10 segundos  | < 15 segundos |
> | **Tasa de Éxito**                       | 100%           | > 95%         |
> | **Consistencia de Datos**               | 100%           | 100%          |

---

## 🔗 Dependencias y Relaciones

> [!NOTE]
>
> ### 🔗 Dependencias
>
> #### Test Cases Relacionados:
>
> - 📋 **Pre-requisito:** Configuración inicial de instancias RDP02
> - 🔄 **Dependiente:** Tests de failover y recuperación
> - 🔗 **Relacionado:** Tests de performance de base de datos
>
> #### Historias de Usuario:
>
> - 📝 **SIASIS-TP-9:** Sincronización entre instancias RDP02
> - 📝 **Componente EMCS01:** Ejecutor múltiple de consultas SQL

---

## 🎭 Roles y Permisos

> [!CAUTION]
>
> ### 👥 Roles Involucrados
>
> | Rol                       | Permisos Requeridos | Operaciones Permitidas             |
> | ------------------------- | ------------------- | ---------------------------------- |
> | **Directivo**             | Escritura completa  | Modificar datos propios y de otros |
> | **Profesor Primaria**     | Escritura limitada  | Modificar solo datos propios       |
> | **Auxiliar**              | Escritura limitada  | Modificar solo datos propios       |
> | **Administrador Sistema** | Escritura total     | Todas las operaciones              |

---

## 📎 Evidencias y Documentación

> [!TIP]
>
> ### 📸 Evidencias Requeridas
>
> #### Durante la Ejecución:
>
> - 📸 Screenshot de interfaz web "MIS DATOS" antes de modificación
> - 📸 Screenshot de modificación de datos en formulario
> - 📸 Screenshot de mensaje de éxito "Datos actualizados correctamente"
> - 📸 Screenshot de GitHub Actions workflow ejecutándose
> - 📸 Screenshot de logs detallados del proceso de replicación
> - 📸 Screenshot de datos replicados en instancias secundarias
> - 🎥 Video del proceso completo (recomendado)
>
> #### Logs y Datos:
>
> - 📝 Logs de GitHub Actions workflow completo
> - 📝 Logs de script de replicación ReplicateTo\*\*\*P02Instances.ts
> - 📝 Queries SQL de validación de consistencia
> - 📝 Tiempos de ejecución detallados
> - 📝 Estados de las 3 instancias RDP02

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
> |  **Dev Asignado**  | Andry Diego |        -        |    Corrección de bugs    |

---

## 📝 Notas y Observaciones

> [!NOTE]
>
> ### 💡 Notas Importantes
>
> - El test debe validar la sincronización en tiempo real sin afectar la experiencia del usuario
> - Es crítico verificar la consistencia de datos en todas las instancias
> - El sistema debe manejar fallos de instancias individuales graciosamente
> - Las operaciones de escritura deben ser atómicas y consistentes
>
> ### 🔄 Historial de Cambios
>
> |   Fecha    | Versión | Cambio           |    Autor    |
> | :--------: | :-----: | ---------------- | :---------: |
> | 20/07/2025 |   1.0   | Creación inicial | Andry Diego |

---

**📅 Última Actualización:** 20/07/2025 09:05  
**✅ Estado de Revisión:** Pendiente  
**👤 Revisado por:** Juan Chavez - Líder Técnico
