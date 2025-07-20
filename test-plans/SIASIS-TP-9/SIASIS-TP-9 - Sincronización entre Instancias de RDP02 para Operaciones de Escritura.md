# 📋 Test Plan: SIASIS-TP-9 - Sincronización entre Instancias de RDP02 para Operaciones de Escritura

> [!IMPORTANT]
>
> **Fecha de Creación:** 17/07/2025
> **Responsable:** Andry Diego
> **Sprint/Release:** 6
> **Estado:** ✅ Completed

---

## 📖 Historia de Usuario

> [!NOTE]
>
> ### 🎯 Historia de Usuario Principal
>
> **COMO** Líder Técnico del sistema SIASIS
>
> **QUIERO** que las 3 bases de datos de PostgreSQL (RDP02) se mantengan sincronizadas automáticamente a pesar de encontrarse en diferentes servidores
>
> **PARA** evitar comportamientos inesperados en el sistema debido a que las bases de datos tendrían diferentes datos

### ✅ Criterios de Aceptación

> [!TIP]
>
> #### 📝 Criterio de Aceptación 1: Sincronización entre bases de datos de PostgreSQL por operaciones de escritura
>
> **Dado** que un usuario de cualquier rol ha iniciado sesión en el sistema en la web
>
> **Cuando** este realiza una operación de escritura (Ejemplo: Modificar su nombre)
>
> **Entonces** se debe ejecutar un Job que ejecute esa misma operación de escritura para el resto de bases de datos en GitHub Actions (EMCS01)

---

## 📄 Descripción del Plan

> [!IMPORTANT]
>
> ### 1. Objetivo
>
> Validar el correcto funcionamiento del sistema de sincronización automática entre las 3 instancias de PostgreSQL (RDP02) mediante la ejecución de jobs en GitHub Actions (EMCS01) que replican operaciones de escritura realizadas en una instancia principal hacia las instancias secundarias, garantizando la consistencia de datos en tiempo real.

> [!NOTE]
>
> ### 2. Alcance y Estrategia de Pruebas
>
> #### 2.1. Lo que se va a probar (Funcionalidades)
>
> | Funcionalidad                                            | Responsable | Prioridad |
> | :------------------------------------------------------- | ----------- | :-------: |
> | Operación de escritura en instancia principal RDP02      | Andry Diego |  🔴 Alta  |
> | Trigger automático de job de replicación (EMCS01)        | Andry Diego |  🔴 Alta  |
> | Replicación de datos a instancia R\*\*\*P02_INS1         | Andry Diego |  🔴 Alta  |
> | Replicación de datos a instancia R\*\*\*P02_INS2         | Andry Diego |  🔴 Alta  |
> | Validación de consistencia entre las 3 instancias        | Andry Diego |  🔴 Alta  |
> | Validación de integridad referencial post-sincronización | Andry Diego | 🟡 Media  |
> | Manejo de errores en caso de fallo de instancia          | Andry Diego | 🟡 Media  |
> | Performance del proceso de sincronización                | Andry Diego |  🟢 Baja  |
>
> #### 2.2. Lo que NO se va a probar
>
> - ❌ Sincronización de bases de datos diferentes a RDP02
> - ❌ Operaciones de solo lectura (SELECT)
> - ❌ Migración de datos históricos
> - ❌ Backup y restore entre instancias

---

> [!WARNING]
>
> ### 3. Componentes Impactados
>
> |   Componente   | Descripción                                                                                                                                                  | Impacto | Estado |
> | :------------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :----: |
> |   **SIU01**    | Servidor de Interfaces de Usuario                                                                                                                            |  ✅ SI  |   🟢   |
> |   **API01**    | API para personal del colegio (Directivos, Auxiliares, Profesores, etc)                                                                                      |  ✅ SI  |   🟢   |
> |   **API02**    | API para padres de Familia                                                                                                                                   |  ❌ NO  |   ⚪   |
> |   **API03**    | API para obtención de hora real UTC                                                                                                                          |  ❌ NO  |   ⚪   |
> |   **TPS01**    | Tareas programadas con Scripts                                                                                                                               |  ❌ NO  |   ⚪   |
> |   **EMCS01**   | Ejecutor múltiple de consultas SQL de Escritura de API01 hacia RDP02 y RDP03                                                                                 |  ✅ SI  |   🟢   |
> |   **EMCN01**   | Ejecutor múltiple de consultas NoSQL de escritura para API02 hacia RDP03                                                                                     |  ❌ NO  |   ⚪   |
> |   **RDP01**    | Repositorio de Datos Persistentes solo para Archivos del Sistema en General (Fotos de Perfil, Excels de Asistencia, Backups, etc) ➡️**Google Drive**         |  ❌ NO  |   ⚪   |
> |   **RDP02**    | Repositorio de Datos Persistentes para Datos Relacionados a Personal del Colegio (Directivos, Auxiliares, Profesores, etc) ➡️ PostgreSQL                     |  ✅ SI  |   🟢   |
> | **RDP02_INS1** | Instancia Principal de PostgreSQL para operaciones de escritura                                                                                              |  ✅ SI  |   🟢   |
> | **RDP02_INS2** | Instancia Secundaria 1 de PostgreSQL para sincronización                                                                                                     |  ✅ SI  |   🟢   |
> | **RDP02_INS3** | Instancia Secundaria 2 de PostgreSQL para sincronización                                                                                                     |  ✅ SI  |   🟢   |
> |   **RDP03**    | Repositorio de Datos Persistentes para Datos Relacionados a Responsables (Padres de Familia/Apoderados) ➡️ MongoDB                                           |  ❌ NO  |   ⚪   |
> |   **RDP04**    | Repositorio de Datos Persistentes para JSONs con Información de Datos de Asistencia del Día Actual (Se actualiza todos los días por TPS01) ➡️ Blob de Vercel |  ❌ NO  |   ⚪   |
> |   **RDP05**    | Repositorio de Datos Persistentes para Asistencias Tomadas a lo largo del día actual exclusivamente ➡️ Redis                                                 |  ❌ NO  |   ⚪   |
> |    **SS01**    | Servidor de Sockets para operaciones en tiempo real                                                                                                          |  ❌ NO  |   ⚪   |
> |    **SE01**    | Servicio Externo de Correo Electrónico por GMAIL de Google                                                                                                   |  ❌ NO  |   ⚪   |

---

> [!TIP]
>
> ### 4. Tipos de Pruebas
>
> | Tipos de Prueba         | Si  | No  |
> | ----------------------- | :-- | :-- |
> | Pruebas Funcionales     | ✅  | ❌  |
> | Pruebas de Diseño (GUI) | ✅  | ❌  |
> | Pruebas de Usabilidad   | ❌  | ✅  |
> | Pruebas de Migración    | ❌  | ✅  |
> | Pruebas de Performance  | ✅  | ❌  |
> | Pruebas de Seguridad    | ✅  | ❌  |
> | Pruebas de Portabilidad | ❌  | ✅  |
> | Pruebas de Integración  | ✅  | ❌  |

---

> [!NOTE]
>
> ### 5. Niveles de Pruebas
>
> | Niveles                | Si  | No  |
> | ---------------------- | :-- | :-- |
> | Nivel de Componente    | ✅  | ❌  |
> | Nivel de Integración   | ✅  | ❌  |
> | Nivel de Sistema (e2e) | ✅  | ❌  |
> | Nivel de Aceptación    | ✅  | ❌  |

---

> [!IMPORTANT]
>
> ### 6. Entorno de Pruebas
>
> #### 6.1. Ambientes
>
> | Ambiente      | Marcar(X) |
> | ------------- | :-------: |
> | Desarrollo    |    ✅     |
> | Certificación |    ✅     |
> | Producción    |    ✅     |

> [!TIP]
>
> #### 6.2. Tecnología
>
> | Tecnología     | Marcar(X) |
> | -------------- | :-------: |
> | Web            |    ✅     |
> | API            |    ✅     |
> | Base de Datos  |    ✅     |
> | GitHub Actions |    ✅     |
> | Otros          |    ❌     |

> [!NOTE]
>
> #### 6.3. Dispositivos
>
> | Dispositivos | Marcar(X) |
> | ------------ | :-------: |
> | Desktop      |    ✅     |
> | Móviles      |    ❌     |
> | Tablets      |    ❌     |
> | Laptops      |    ✅     |
> | Otros        |    ❌     |

> [!WARNING]
>
> #### 6.4. Navegadores (En caso aplique pruebas WEB)
>
> | Navegador | Versión | Marcar(X) |
> | --------- | ------- | :-------: |
> | Chrome    | Última  |    ✅     |
> | Firefox   | Última  |    ❌     |
> | Safari    | Última  |    ❌     |
> | Edge      | Última  |    ❌     |
> | Opera     | Última  |    ❌     |

> [!CAUTION]
>
> #### 6.5. Sistemas Operativos
>
> | Sistema Operativo | Versión    | Marcar(X) |
> | ----------------- | ---------- | :-------: |
> | Windows           | 10/11      |    ✅     |
> | macOS             | Monterey+  |    ❌     |
> | Linux             | Ubuntu 20+ |    ✅     |
> | iOS               | 15+        |    ❌     |
> | Android           | 10+        |    ❌     |

---

> [!IMPORTANT]
>
> ### 7. Lista de Tests a Usar
>
> | Tag Identificador              | Descripción                                  |     | Desarrollo | Certificación | Producción |
> | ------------------------------ | -------------------------------------------- | --- | :--------: | :-----------: | :--------: |
> | `@database-replication`        | Replicación de datos entre instancias        |     |     ✅     |      ✅       |     ✅     |
> | `@automatic-sync-trigger`      | Trigger automático de sincronización         |     |     ✅     |      ✅       |     ✅     |
> | `@user-data-modification`      | Modificación de datos de usuario             |     |     ✅     |      ✅       |     ✅     |
> | `@github-actions-emcs01`       | Ejecución de jobs en GitHub Actions          |     |     ✅     |      ✅       |     ✅     |
> | `@multi-instance-consistency`  | Consistencia entre múltiples instancias      |     |     ✅     |      ✅       |     ✅     |
> | `@write-operation-replication` | Replicación de operaciones de escritura      |     |     ✅     |      ✅       |     ✅     |
> | `@data-integrity-validation`   | Validación de integridad de datos            |     |     ✅     |      ✅       |     ✅     |
> | `@real-time-sync-performance`  | Performance de sincronización en tiempo real |     |     ✅     |      ✅       |     ❌     |

---

> [!TIP]
>
> ### 8. Estrategia de Pruebas
>
> |                     Flujo                      |     Tipo de Prueba     | Fecha de Inicio | Fecha Fin  |     Ambiente     |                                                                          Test Execution                                                                           |
> | :--------------------------------------------: | :--------------------: | :-------------: | :--------: | :--------------: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------: |
> | Sincronización de Datos entre Instancias RDP02 | 🔧 Pruebas Funcionales |   17/07/2025    | 18/07/2025 |  🔧 Desarrollo   |     [SIASIS-TE-22](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/test-plans/SIASIS-TP-9/Desarrollo/SIASIS-TE-22.md "Ir al TestExecution")     |
> | Sincronización de Datos entre Instancias RDP02 | 🔧 Pruebas Funcionales |   17/07/2025    | 18/07/2025 | 🧪 Certificación | [SIASIS-TE-23](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/test-plans/SIASIS-TP-9/Certificaci%C3%B3n/SIASIS-TE-23.md "Ir al TestExecution") |
> | Sincronización de Datos entre Instancias RDP02 | 🔧 Pruebas Funcionales |   17/07/2025    | 18/07/2025 |  🚀 Producción   |  [SIASIS-TE-24](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/test-plans/SIASIS-TP-9/Producci%C3%B3n/SIASIS-TE-24.md "Ir al TestExecution")   |

---

## 📊 Métricas y Criterios de Salida

> [!IMPORTANT]
>
> ### 🎯 Criterios de Éxito
>
> - ✅ **100%** de operaciones de escritura replicadas exitosamente
> - ✅ **Tiempo de sincronización** < 30 segundos entre instancias
> - ✅ **0** inconsistencias de datos post-sincronización
> - ✅ **100%** de jobs de GitHub Actions ejecutados correctamente
> - ✅ **Integridad referencial** mantenida en todas las instancias
> - ✅ **Validación de datos** exitosa en las 3 instancias RDP02

> [!WARNING]
>
> ### 🚨 Criterios de Bloqueo
>
> - ❌ Falla en la ejecución del job de replicación (EMCS01)
> - ❌ Inconsistencias de datos entre instancias RDP02
> - ❌ Pérdida de datos durante la sincronización
> - ❌ Timeout en el proceso de replicación (> 60 segundos)
> - ❌ Fallo en la conectividad con alguna instancia RDP02
> - ❌ Corrupción de integridad referencial

---

## 🔧 Detalles Técnicos Específicos

> [!NOTE]
>
> ### 📊 Arquitectura de Sincronización
>
> |       Componente        | Función                                       | Instancias Objetivo                                     |
> | :---------------------: | --------------------------------------------- | ------------------------------------------------------- |
> |   **RDP02 Principal**   | Recibe operación de escritura original        | -                                                       |
> |       **EMCS01**        | Ejecuta job de replicación vía GitHub Actions | R**_P02_INS1, R_**P02_INS2                              |
> | **Repository Dispatch** | Trigger automático del workflow               | SIASIS-EMCS01-DEV                                       |
> | **Replication Script**  | Script TypeScript de sincronización           | /src/jobs/replications/ReplicateTo\*\*\*P02Instances.ts |

> [!TIP]
>
> ### 🎯 Operaciones de Escritura a Validar
>
> | Operación       | Ejemplo                     | Tabla Objetivo     |
> | --------------- | --------------------------- | ------------------ |
> | **UPDATE**      | Modificar nombre de usuario | T\_\*\*\*irectivos |
> | **INSERT**      | Agregar nuevo registro      | T\_\*\*\*irectivos |
> | **DELETE**      | Eliminar registro           | T\_\*\*\*irectivos |
> | **BULK UPDATE** | Actualización masiva        | Múltiples tablas   |

> [!INFO]
>
> ### 📈 Métricas de Performance Esperadas
>
> | Métrica                   | Valor Objetivo | Valor Crítico |
> | ------------------------- | -------------- | ------------- |
> | **Tiempo de Trigger**     | < 5 segundos   | < 10 segundos |
> | **Tiempo de Replicación** | < 20 segundos  | < 30 segundos |
> | **Éxito de Replicación**  | 100%           | > 95%         |
> | **Consistencia de Datos** | 100%           | 100%          |

---

**📅 Última Actualización:** 20/07/2025
**✅ Estado de Aprobación:** Pendiente
**👤 Aprobado por:** Juan Chavez - Líder Técnico
