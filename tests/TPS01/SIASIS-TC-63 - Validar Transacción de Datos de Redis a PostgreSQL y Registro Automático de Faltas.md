# 🧪 Test Case: SIASIS-TC-52 - Validar Transacción de Datos de Redis a PostgreSQL y Registro Automático de Faltas

> [!IMPORTANT]
> **ID del Test Case:** SIASIS-TC-63
> **Fecha de Creación:** 15/07/2025
> **Autor:** Andry Diego
> **Última Actualización:** 19/07/2025
> **Estado:** 🟢 Ready

---

## 📋 Información General

> [!NOTE]
>
> ### 🔖 Metadatos del Test
>
> | Campo                     |                                                                                  Valor                                                                                  |
> | ------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
> | **ID Test Case**    |                                                                               SIASIS-TC-63                                                                               |
> | **Nombre**          |                                      Validar Transacción de Datos de Redis a PostgreSQL y Registro Automático de Faltas                                      |
> | **Módulo/Feature** |                                                                       Transacción de Datos de Asistencia                                                                       |
> | **Epic/User Story** |                                                                               SIASIS-TP-8                                                                               |
> | **Tipo de Prueba**  |                                                                           🔧 Funcional\|🔗 Integration                                                                           |
> | **Nivel de Prueba** |                                                                                🌐 System                                                                                |
> | **Prioridad**       |                                                                               🔴 Critical                                                                               |
> | **Severidad**       |                                                                                🔴 Blocker                                                                                |
> | **Automatizable**   |                                                                                  ✅ Sí                                                                                  |
> | **Automatizada**    |                                                                                  ⏳ Futuro                                                                                 |

---

> [!TIP]
>
> ### 🏷️ Tags y Categorización
>
> **Tags principales:**
>
> ```gherkin
> @SIASIS-TC-63 @redis-transaction @auto-falta-registro @scheduled-task @data-integrity
> ```
>
> **Tags por componente:**
>
> ```gherkin
> @TPS01 @RDP02 @RDP05 @API03 @EMCS01
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
> Este test valida el proceso automatizado de transacción de datos de asistencia desde Redis (RDP05) hacia PostgreSQL (RDP02) mediante una tarea programada en GitHub Actions, incluyendo el registro automático de faltas para personal que no marcó asistencia durante el día escolar.

> [!NOTE]
>
> ### 🎯 Objetivo Principal
>
> **Objetivo:** Verificar que la tarea programada ejecute correctamente la transacción de datos de asistencia de Redis a PostgreSQL a las 9:30pm, registrando automáticamente las faltas del personal sin asistencia y manteniendo la integridad de los datos.
>
> **Criterio de Éxito:** 
> - Tarea programada se ejecuta automáticamente a las 9:30pm
> - Todos los registros de asistencia se transfieren exitosamente de Redis a PostgreSQL
> - Se registran automáticamente las faltas del personal sin asistencia
> - La interfaz muestra correctamente las faltas registradas

---

## 🔧 Configuración Técnica

> [!WARNING]
>
> ### 💻 Tecnología y Componentes
>
> | Aspecto                         | Detalle                               |
> | ------------------------------- | ------------------------------------- |
> | **Tecnología Principal** | 🔌 API\| 💾 Database \| 🖥️ GitHub Actions |
> | **Navegadores**           | Chrome (para validación UI)          |
> | **Dispositivos**          | Desktop, Server                       |
> | **Sistemas Operativos**   | Linux (Ubuntu), Windows               |
> | **Resoluciones**          | 1920x1080 (para validación UI)       |

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
> | **TPS01** | Tareas programadas con Scripts                                                                                                                                    | ✅ |    |
> | **EMCS01** | Ejecutor múltiple de consultas SQL de Escritura de API01 hacia RDP02 y RDP03                                                                                     | ✅ |    |
> | **EMCN01** | Ejecutor múltiple de consultas NoSQL de escritura para API02 hacia RDP03                                                                                         |    | ❌ |
> | **RDP01** | Repositorio de Datos Persistentes solo para Archivos del Sistema en General (Fotos de Perfil, Excels de Asistencia, Backups, etc) ➡️**Google Drive**      |    | ❌ |
> | **RDP02** | Repositorio de Datos Persistentes para Datos Relacionados a Personal del Colegio (Directivos, Auxiliares, Profesores, etc) ➡️ PostgreSQL                        | ✅ |    |
> | **RDP03** | Repositorio de Datos Persistentes para Datos Relacionados a Responsables (Padres de Familia/Apoderados) ➡️ MongoDB                                              |    | ❌ |
> | **RDP04** | Repositorio de Datos Persistentes para JSONs con Información de Datos de Asistencia del Día Actual (Se actualiza todos los días por TPS01) ➡️ Blob de Vercel | ✅ |    |
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
> @SIASIS-TC-52 @redis-transaction @auto-falta-registro @scheduled-task @TPS01 @RDP02 @RDP05 @API03 @EMCS01
> Feature: Transacción automática de datos de asistencia desde Redis a PostgreSQL
>   Como Líder Técnico del sistema SIASIS
>   Quiero que los datos de asistencia se transfieran automáticamente de Redis a PostgreSQL
>   Para evitar la pérdida de datos por expiración y registrar faltas automáticamente
>
> Background:
>   Given el día escolar ha finalizado (7:30 aproximadamente)
>   And existen datos de asistencia en Redis RDP05
>   And existen datos de personal programado para asistir ese día en RDP04
>   And todos los servicios están funcionando correctamente
>
> @SIASIS-TC-52 @critical @data-integrity
> Scenario: Ejecución exitosa de transacción de datos y registro de faltas
>   Given son las 9:30pm del día escolar
>   And la tarea programada está configurada en GitHub Actions
>   And Redis RDP05 contiene registros de asistencia del día
>   And PostgreSQL RDP02 está disponible para recibir datos
>   When se ejecuta la tarea programada automáticamente
>   Then todos los registros de asistencia se consultan desde Redis RDP05
>   And se procesan y transfieren exitosamente a PostgreSQL RDP02
>   And se identifican los personales sin registro de entrada o salida
>   And se registran automáticamente las faltas correspondientes
>   And se actualizan los registros mensuales en RDP02
>   And la interfaz UI muestra correctamente las faltas registradas
>   And se bloquean temporalmente los roles durante el procesamiento
>   And el proceso completo toma menos de 5 minutos
>   And no se pierde ningún dato durante la transacción
> ```

---

## ⚙️ Precondiciones y Setup

> [!IMPORTANT]
>
> ### 🔧 Precondiciones
>
> #### Estado del Sistema:
>
> - ✅ GitHub Actions configurado con tarea programada para 9:30pm
> - ✅ Redis RDP05 con datos de asistencia del día
> - ✅ PostgreSQL RDP02 disponible y funcional
> - ✅ Datos de personal programado cargados en RDP04
> - ✅ Conectividad entre todos los componentes
>
> #### Datos de Prueba Requeridos:
>
> - 📊 **Registros de asistencia en Redis:** Al menos 5 registros de entrada/salida
> - 📊 **Personal programado:** Lista de personal que debía asistir ese día
> - 📊 **Personal sin asistencia:** Al menos 3 personas sin registros para validar faltas
> - ⏰ **Hora específica:** 9:30pm del día de prueba
>
> #### Configuración del Ambiente:
>
> - 🌐 **URL Base:** Variable según ambiente (dev/cert/prod)
> - 🔧 **Ambiente:** Desarrollo, Certificación, Producción
> - 🕘 **Horario:** 9:30pm en zona horaria del sistema

---

## 📋 Pasos de Ejecución

> [!NOTE]
>
> ### 🚶‍♂️ Pasos Detallados
>
> | # | Acción                                              | Datos de Entrada                        | Resultado Esperado                                    |
> | - | --------------------------------------------------- | --------------------------------------- | ----------------------------------------------------- |
> | 1 | Verificar registros existentes en Redis RDP05      | Consulta a instancia Redis              | Se muestran registros de asistencia del día          |
> | 2 | Confirmar personal programado en RDP04             | Consulta a datos de asistencia del día | Lista de personal que debía asistir                  |
> | 3 | Esperar ejecución automática a las 9:30pm          | Hora del sistema: 21:30                | Tarea programada inicia automáticamente              |
> | 4 | Monitorear logs de GitHub Actions                   | Ejecución de workflow                   | Logs muestran inicio del procesamiento               |
> | 5 | Validar consulta de registros desde Redis          | Script de transacción                  | Se obtienen todos los registros de Redis             |
> | 6 | Verificar procesamiento de registros               | Datos extraídos de Redis               | Registros procesados correctamente                   |
> | 7 | Confirmar inserción en PostgreSQL RDP02           | Transacción SQL                        | Datos insertados en registros mensuales              |
> | 8 | Validar identificación de personal sin asistencia | Comparación datos programados vs reales| Se identifican personas sin entrada/salida           |
> | 9 | Verificar registro automático de faltas           | Script de faltas                       | Faltas registradas en base de datos                  |
> | 10| Confirmar bloqueo temporal de roles               | Estado de roles en sistema             | Roles bloqueados durante procesamiento               |
> | 11| Validar interfaz UI con faltas registradas        | Acceso a consulta de asistencias      | UI muestra faltas del día correctamente             |
> | 12| Verificar tiempo total de ejecución              | Logs de duración                       | Proceso completo en menos de 5 minutos               |

---

## ✅ Criterios de Aceptación

> [!SUCCESS]
>
> ### 🎯 Resultado Esperado Principal
>
> La tarea programada se ejecuta automáticamente a las 9:30pm, transfiere exitosamente todos los datos de asistencia desde Redis RDP05 hacia PostgreSQL RDP02, registra automáticamente las faltas del personal que no marcó asistencia, y la interfaz muestra correctamente toda la información procesada.

> [!TIP]
>
> ### ✅ Validaciones Específicas
>
> #### Validaciones Funcionales:
>
> - ✅ Tarea programada se ejecuta automáticamente a las 9:30pm
> - ✅ 100% de registros de Redis se transfieren a PostgreSQL
> - ✅ Faltas se registran automáticamente para personal sin asistencia
> - ✅ Integridad referencial mantenida en todos los datos
> - ✅ Registros mensuales actualizados correctamente
>
> #### Validaciones de UI/UX:
>
> - ✅ Interfaz de consulta muestra las faltas registradas
> - ✅ Información de faltas se presenta correctamente
> - ✅ Datos actualizados se reflejan en tiempo real
>
> #### Validaciones de Datos:
>
> - ✅ No hay pérdida de datos durante la transacción
> - ✅ Consistencia entre datos de origen y destino
> - ✅ Formato de datos correcto en PostgreSQL
> - ✅ Timestamps correctos en todos los registros

---

## 🚫 Casos Negativos y Edge Cases

> [!WARNING]
>
> ### ⚠️ Escenarios de Error
>
> | Escenario                          | Acción                                    | Resultado Esperado                      |
> | ---------------------------------- | ----------------------------------------- | --------------------------------------- |
> | **Redis no disponible**     | Caída de servicio Redis durante proceso  | Error controlado, log de fallo          |
> | **PostgreSQL no disponible** | Caída de BD durante transacción         | Rollback automático, reintento          |
> | **Sin datos en Redis**       | Redis vacío en hora de ejecución        | Log informativo, proceso completado     |
> | **Timeout de proceso**       | Proceso excede tiempo límite            | Cancelación controlada, alerta          |
> | **Datos corruptos**          | Registros con formato inválido          | Validación previa, exclusión de datos  |

---

## 📊 Métricas y Performance

> [!INFO]
>
> ### ⏱️ Criterios de Performance
>
> | Métrica                         | Valor Esperado | Crítico      |
> | ------------------------------- | -------------- | ------------- |
> | **Tiempo de Ejecución Total** | < 5 minutos    | < 10 minutos  |
> | **Tiempo de Consulta Redis**  | < 30 segundos  | < 1 minuto    |
> | **Tiempo de Inserción SQL**   | < 2 minutos    | < 5 minutos   |
> | **Uso de Memoria**             | < 1GB          | < 2GB         |
> | **Registros Procesados/seg**   | > 10 registros | > 5 registros |

---

## 🔗 Dependencias y Relaciones

> [!NOTE]
>
> ### 🔗 Dependencias
>
> #### Test Cases Relacionados:
>
> - 📋 **Pre-requisito:** Tarea programada de obtención de datos (4:30am)
> - 🔄 **Dependiente:** Validación de reportes mensuales
> - 🔗 **Relacionado:** Tests de conectividad Redis-PostgreSQL
>
> #### Historias de Usuario:
>
> - 📝 **SIASIS-TP-8:** Transacción de datos de asistencia
> - 📝 **SIASIS-TP-6:** Obtención de datos para asistencia (dependencia)

---

## 🎭 Roles y Permisos

> [!CAUTION]
>
> ### 👥 Roles Involucrados
>
> | Rol                         | Durante Ejecución | Post Ejecución |
> | --------------------------- | ----------------- | -------------- |
> | **Directivo**         | 🔒 Bloqueado     | ✅ Disponible  |
> | **Profesor Primaria** | 🔒 Bloqueado     | ✅ Disponible  |
> | **Auxiliar**          | 🔒 Bloqueado     | ✅ Disponible  |
> | **Profesor Secundaria** | 🔒 Bloqueado     | ✅ Disponible  |
> | **Tutor**             | 🔒 Bloqueado     | ✅ Disponible  |
> | **Personal Administrativo** | 🔒 Bloqueado | ✅ Disponible  |

---

## 📎 Evidencias y Documentación

> [!TIP]
>
> ### 📸 Evidencias Requeridas
>
> #### Durante la Ejecución:
>
> - 📸 Screenshot de logs de GitHub Actions antes de ejecución
> - 📸 Screenshot de registros en Redis antes del proceso
> - 📸 Screenshot de ejecución de la tarea programada
> - 📸 Screenshot de logs durante el procesamiento
> - 📸 Screenshot de datos transferidos en PostgreSQL
> - 📸 Screenshot de faltas registradas en BD
> - 📸 Screenshot de interfaz UI con faltas mostradas
> - 🎥 Video del proceso completo (recomendado)
>
> #### Logs y Datos:
>
> - 📝 Logs completos de GitHub Actions
> - 📝 Logs de consultas Redis
> - 📝 Logs de transacciones PostgreSQL
> - 📝 Dump de datos antes y después del proceso
> - 📝 Tiempos de ejecución detallados

---

## 📞 Información de Contacto

> [!INFO]
>
> ### 👥 Responsables
>
> |           Rol           |     Nombre      | Email / Celular |      Responsabilidad      |
> | :----------------------: | :-------------: | :-------------: | :-----------------------: |
> | **Autor del Test** |  Andry Diego    |        -        | Creación y mantenimiento |
> | **Product Owner** |  Juan Chavez    |        -        | Validación de criterios |
> |   **Tech Lead**   |  Juan Chavez    |        -        |    Revisión técnica    |
> |  **Dev Asignado**  |  Andry Diego    |        -        |    Corrección de bugs    |

---

## 📝 Notas y Observaciones

> [!NOTE]
>
> ### 💡 Notas Importantes
>
> - El proceso debe ejecutarse exactamente a las 9:30pm para evitar pérdida de datos por expiración de Redis (23:00h)
> - Durante la ejecución, todos los roles están temporalmente bloqueados para evitar conflictos
> - El test debe validar tanto la transacción de datos existentes como el registro de faltas
> - La interfaz UI debe reflejar inmediatamente los cambios post-procesamiento
>
> ### 🔄 Historial de Cambios
>
> |    Fecha    | Versión | Cambio              |     Autor     |
> | :----------: | :------: | ------------------- | :-----------: |
> |  20/07/2025  |   1.0   | Creación inicial   | Andry Diego   |

---

**📅 Última Actualización:** 20/07/2025 03:06
**✅ Estado de Revisión:** Pendiente
**👤 Revisado por:** Juan Chavez - Líder Técnico