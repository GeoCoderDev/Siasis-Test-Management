# 📋 Test Plan: SIASIS-TP-8 - Transacción de Datos de Redis a PostgreSQL y Registro Automático de Faltas

> [!IMPORTANT]
>
> **Fecha de Creación:** 19/07/2025
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
> **QUIERO** que los datos de asistencia de Personal generados en el transcurso de cierto día escolar (Lunes a Viernes) en la instancia 1 de los RDP05 (Redis) se transfieran automáticamente a los RDP02 (Bases de datos de PostgreSQL)
>
> **PARA** evitar perder dichos datos de Toma de Asistencia de Personal generados a lo largo de cierto día Escolar debido a su expiración a las 23h aproximadamente y guardarlos en los registros mensuales correspondientes de cada Personal en las bases de datos RDP02.

### ✅ Criterios de Aceptación

> [!TIP]
>
> #### 📝 Criterio de Aceptación 1: Ejecución de Tarea Programada de Transacción de Datos de RDP05 a RDP02 + Registro automático de Faltas
>
> **Dado** que ya se finalizó la toma de asistencia de cierto día escolar (7:30 aproximadamente)
>
> **Cuando** ya son las 9:30pm aprox del mismo día escolar
>
> **Entonces** se debe ejecutar una tarea programada en GitHub Actions que copie todos los datos de Redis a los registros mensuales correspondientes de cada Usuario cuya asistencia fue registrada dicho día de RDP02 (Bases de datos de PostgreSQL)
>
> **Y** en ese proceso también se debe registrar las faltas de los personales que debían ir dicho día según los datos de asistencia, generados por la tarea programada a las 4:30am aprox, pero que no marcaron alguna asistencia de entrada o salida.

---

## 📄 Descripción del Plan

> [!IMPORTANT]
>
> ### 1. Objetivo
>
> Validar el correcto funcionamiento de la tarea programada que transfiere automáticamente los datos de asistencia diaria desde Redis (RDP05) hacia PostgreSQL (RDP02) y registra automáticamente las faltas del personal que no marcó asistencia durante el día escolar, garantizando la integridad y persistencia de los datos antes de su expiración.

> [!NOTE]
>
> ### 2. Alcance y Estrategia de Pruebas
>
> #### 2.1. Lo que se va a probar (Funcionalidades)
>
> | Funcionalidad                                                     | Responsable | Prioridad |
> | :---------------------------------------------------------------- | ----------- | :-------: |
> | Ejecución automática de tarea programada a las 9:30pm             | Andry Diego |  🔴 Alta  |
> | Consulta y obtención de registros de asistencia desde Redis RDP05 | Andry Diego |  🔴 Alta  |
> | Procesamiento y transacción de registros desde Redis a PostgreSQL | Andry Diego |  🔴 Alta  |
> | Registro automático de faltas para personal sin asistencia        | Andry Diego |  🔴 Alta  |
> | Validación de integridad de datos transferidos                    | Andry Diego |  🔴 Alta  |
> | Actualización de registros mensuales en RDP02                     | Andry Diego |  🔴 Alta  |
> | Bloqueo correcto de roles durante el procesamiento                | Andry Diego | 🟡 Media  |
>
> #### 2.2. Lo que NO se va a probar
>
> - ❌ Pruebas de migración de versiones anteriores
> - ❌ Pruebas de escalabilidad con volúmenes masivos
> - ❌ Pruebas de recuperación ante desastres

---

> [!WARNING]
>
> ### 3. Componentes Impactados
>
> | Componente | Descripción                                                                                                                                                  | Impacto | Estado |
> | :--------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :----: |
> | **SIU01**  | Servidor de Interfaces de Usuario                                                                                                                            |  ❌ NO  |   ⚪   |
> | **API01**  | API para personal del colegio (Directivos, Auxiliares, Profesores, etc)                                                                                      |  ❌ NO  |   ⚪   |
> | **API02**  | API para padres de Familia                                                                                                                                   |  ❌ NO  |   ⚪   |
> | **API03**  | API para obtención de hora real UTC                                                                                                                          |  ✅ SI  |   🟢   |
> | **TPS01**  | Tareas programadas con Scripts                                                                                                                               |  ✅ SI  |   🟢   |
> | **EMCS01** | Ejecutor múltiple de consultas SQL de Escritura de API01 hacia RDP02 y RDP03                                                                                 |  ✅ SI  |   🟢   |
> | **EMCN01** | Ejecutor múltiple de consultas NoSQL de escritura para API02 hacia RDP03                                                                                     |  ❌ NO  |   ⚪   |
> | **RDP01**  | Repositorio de Datos Persistentes solo para Archivos del Sistema en General (Fotos de Perfil, Excels de Asistencia, Backups, etc) ➡️**Google Drive**         |  ❌ NO  |   ⚪   |
> | **RDP02**  | Repositorio de Datos Persistentes para Datos Relacionados a Personal del Colegio (Directivos, Auxiliares, Profesores, etc) ➡️ PostgreSQL                     |  ✅ SI  |   🟢   |
> | **RDP03**  | Repositorio de Datos Persistentes para Datos Relacionados a Responsables (Padres de Familia/Apoderados) ➡️ MongoDB                                           |  ❌ NO  |   ⚪   |
> | **RDP04**  | Repositorio de Datos Persistentes para JSONs con Información de Datos de Asistencia del Día Actual (Se actualiza todos los días por TPS01) ➡️ Blob de Vercel |  ✅ SI  |   🟡   |
> | **RDP05**  | Repositorio de Datos Persistentes para Asistencias Tomadas a lo largo del día actual exclusivamente ➡️ Redis                                                 |  ✅ SI  |   🟢   |
> |  **SS01**  | Servidor de Sockets para operaciones en tiempo real                                                                                                          |  ❌ NO  |   ⚪   |
> |  **SE01**  | Servicio Externo de Correo Electrónico por GMAIL de Google                                                                                                   |  ❌ NO  |   ⚪   |

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
> | Otros Tipos de Pruebas  | ❌  | ✅  |

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
> | Tag Identificador            | Descripción                             |     | Desarrollo | Certificación | Producción |
> | ---------------------------- | --------------------------------------- | --- | :--------: | :-----------: | :--------: |
> | `@redis-transaction`         | Transacción de datos Redis a PostgreSQL |     |     ✅     |      ✅       |     ✅     |
> | `@auto-falta-registro`       | Registro automático de faltas           |     |     ✅     |      ✅       |     ✅     |
> | `@scheduled-task-execution`  | Ejecución de tareas programadas         |     |     ✅     |      ✅       |     ✅     |
> | `@data-integrity-validation` | Validación de integridad de datos       |     |     ✅     |      ✅       |     ✅     |
> | `@role-blocking-process`     | Proceso de bloqueo de roles             |     |     ✅     |      ✅       |     ❌     |
> | `@monthly-records-update`    | Actualización de registros mensuales    |     |     ✅     |      ✅       |     ✅     |
> | `@ui-interface-validation`   | Validación de interfaz de consulta      |     |     ✅     |      ✅       |     ❌     |

---

> [!TIP]
>
> ### 7. Estrategia de Pruebas
>
> |                        Flujo                        |     Tipo de Prueba     | Fecha de Inicio | Fecha Fin  |     Ambiente     |                                                                         Test Execution                                                                          |
> | :-------------------------------------------------: | :--------------------: | :-------------: | :--------: | :--------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------: |
> | Transacción Redis a PostgreSQL + Registro de Faltas | 🔧 Pruebas Funcionales |   03/07/2025    | 03/07/2025 |  🔧 Desarrollo   |     [SIASIS-TE-1](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/test-plans/SIASIS-TP-1/Desarrollo/SIASIS-TE-1.md "Ir al TestExecution")     |
> | Transacción Redis a PostgreSQL + Registro de Faltas | 🔧 Pruebas Funcionales |   03/07/2025    | 03/07/2025 | 🧪 Certificación | [SIASIS-TE-2](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/test-plans/SIASIS-TP-1/Certificaci%C3%B3n/SIASIS-TE-2.md "Ir al TestExecution") |
> | Transacción Redis a PostgreSQL + Registro de Faltas | 🔧 Pruebas Funcionales |   03/07/2025    | 03/07/2025 |  🚀 Producción   |  [SIASIS-TE-3](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/test-plans/SIASIS-TP-1/Producci%C3%B3n/SIASIS-TE-3.md "Ir al TestExecution")   |

---

## 📊 Métricas y Criterios de Salida

> [!IMPORTANT]
>
> ### 🎯 Criterios de Éxito
>
> - ✅ **100%** de registros de asistencia transferidos exitosamente de Redis a PostgreSQL
> - ✅ **100%** de faltas registradas automáticamente para personal sin asistencia
> - ✅ **0** pérdida de datos durante la transacción
> - ✅ **Tiempo de ejecución** de tarea programada < 5 minutos
> - ✅ **Integridad referencial** mantenida en todos los registros transferidos
> - ✅ **Validación UI** muestra correctamente las faltas registradas

> [!WARNING]
>
> ### 🚨 Criterios de Bloqueo
>
> - ❌ Falla en la ejecución de la tarea programada
> - ❌ Pérdida de datos durante la transacción Redis -> PostgreSQL
> - ❌ Faltas no registradas automáticamente
> - ❌ Corrupción de datos en registros mensuales
> - ❌ Tiempo de ejecución > 10 minutos
> - ❌ Interfaz no muestra las faltas registradas correctamente

---

**📅 Última Actualización:** 20/07/2025
**✅ Estado de Aprobación:** Pendiente
**👤 Aprobado por:** Juan Chavez - Líder Técnico
