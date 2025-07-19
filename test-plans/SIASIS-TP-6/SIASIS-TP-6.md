# 📋 Test Plan: SIASIS-TP-1 - Login para Personal del Colegio IE20935

> [!IMPORTANT]
>
> **Fecha de Creación:** 28/06/2025
> **Responsable: Andry Diego** > **Sprint/Release:** 5
> **Estado:** ✅ Completed

---

## 📖 Historia de Usuario

> [!NOTE]
>
> ### 🎯 Historia de Usuario Principal
>
> **COMO** Líder Técnico del sistema SIASIS
>
> **QUIERO** que los datos necesarios para la toma de asistencia(Ejemplo: Lista de profesores de primaria, Lista de Profesores de Secundaria que vienen ese dia con sus respectivos horarios, etc) de cualquier dia escolar.
>
> **PARA** evitar estar consultando de manera repetitiva a las base de datos por datos como los horarios de los profesores , etc.

### ✅ Criterios de Aceptación

> [!TIP]
>
> #### 📝 Criterio de Aceptación 1:
>
> **Dado** que ya esta comenzando un cualquier dia escolar(Lunes-Viernes)
>
> **Cuando** ya son las 4:30am aprox del mismo dia escolar
>
> **Entonces** se debe ejecutar una tarea programada en github actions que consulte todos los datos necesarios para la toma de asistencia de ese dia escolar y almacenarlos en formato json en todas las instancias de blobs de vercel del sistema(RDP04)

> [!TIP]
>
> #### 📝 Criterio de Aceptación 2:
>
> **Dado** que se ejecutó correctamente la tarea programada
>
> **Cuando** se consultan los datos almacenados en RDP04
>
> **Entonces** los JSONs deben contener toda la información necesaria: listas de profesores por nivel, horarios del día, información de turnos y cualquier dato requerido para la toma de asistencia

---

## 📄 Descripción del Plan

> [!IMPORTANT]
>
> ### 1. Objetivo
>
> Validar el correcto funcionamiento de la tarea programada que obtiene y almacena automáticamente todos los datos necesarios para la toma de asistencia diaria del personal del Colegio IE20935, garantizando la disponibilidad, integridad y actualización de la información en formato JSON en RDP04.

> [!NOTE]
>
> ### 2. Alcance y Estrategia de Pruebas
>
> #### 2.1. Lo que se va a probar (Funcionalidades)
>
> | Funcionalidad                                         | Responsable | Prioridad |
> | :---------------------------------------------------- | ----------- | :-------: |
> | Ejecución automática de tarea programada a las 4:30am | Andry Diego |  🔴 Alta  |
> | Consulta de datos de profesores de primaria           | Andry Diego |  🔴 Alta  |
> | Consulta de datos de profesores de secundaria         | Andry Diego |  🔴 Alta  |
> | Obtención de horarios diarios del personal            | Andry Diego |  🔴 Alta  |
> | Almacenamiento de JSONs en RDP04 (Blob de Vercel)     | Andry Diego |  🔴 Alta  |
> | Validación de integridad de datos almacenados         | Andry Diego |  🔴 Alta  |
>
> #### 2.2. Lo que NO se va a probar
>
> - ❌ Pruebas de Performance
> - ❌ Pruebas de Escalabilidad
> - ❌ Pruebas de Volumen

---

> [!WARNING]
>
> ### 3. Componentes Impactados
>
> | Componente | Descripción                                                                                                                                                  | Si  | No  |
> | :--------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | --- | --- |
> | **API01**  | API para personal del colegio (Directivos, Auxiliares, Profesores, etc)                                                                                      | ✅  |     |
> | **API03**  | API para obtención de hora real UTC                                                                                                                          | ✅  |     |
> | **TPS01**  | Tareas programadas con Scripts                                                                                                                               | ✅  |     |
> | **EMCS01** | Ejecutor múltiple de consultas SQL de Escritura de API01 hacia RDP02 y RDP03                                                                                 | ✅  |     |
> | **EMCN01** | Ejecutor múltiple de consultas SQL de escritura para API02 hacia RDP03                                                                                       |     | ❌  |
> | **RDP01**  | Repositorio de Datos Persistentes solo para Archivos del Sistema en General (Fotos de Perfil, Excels de Asistencia, Backups, etc) ➡️**Google Drive**         |     | ❌  |
> | **RDP02**  | Repositorio de Datos Persistentes para Datos Relacionados a Personal del Colegio (Directivos, Auxiliares, Profesores, etc) ➡️ PostgreSQL                     | ✅  |     |
> | **RDP03**  | Repositorio de Datos Persistentes para Datos Relacionados a Responsables (Padres de Familia/Apoderados) ➡️ MongoDB                                           |     | ❌  |
> | **RDP04**  | Repositorio de Datos Persistentes para JSONs con Información de Datos de Asistencia del Día Actual (Se actualiza todos los días por TPS01) ➡️ Blob de Vercel | ✅  |     |
> | **RDP05**  | Repositorio de Datos Persistentes para Asistencias Tomadas a lo largo del día actual exclusivamente ➡️ Redis                                                 |     | ❌  |
> |  **SS01**  | Servidor de Sockets para operaciones en tiempo real                                                                                                          |     | ❌  |
> |  **SE01**  | Servicio Externo de Correo Electrónico por GMAIL de Google                                                                                                   |     | ❌  |

---

> [!TIP]
>
> ### 4. Tipos de Pruebas
>
> | Tipos de Prueba         | Si  | No  |
> | ----------------------- | :-- | :-- |
> | Pruebas Funcionales     | ✅  |     |
> | Pruebas de Diseño (GUI) |     | ❌  |
> | Pruebas de Usabilidad   |     | ❌  |
> | Pruebas de Migración    |     | ✅  |
> | Pruebas de Performance  |   ✅  |   |
> | Pruebas de Seguridad    |  ✅   |   |
> | Pruebas de Portabilidad |     | ❌  |
> | Otros Tipos de Pruebas  |     | ❌  |

---

> [!NOTE]
>
> ### 5. Niveles de Pruebas
>
> | Niveles                | Si  | No  |
> | ---------------------- | :-- | :-- |
> | Nivel de Componente    | ✅  |     |
> | Nivel de Integración   |     | ❌  |
> | Nivel de Sistema (e2e) | ✅  |     |
> | Nivel de Aceptación    |     | ❌  |

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
> #### 6.4. Navegadores (En caso aplique pruebas en la WEB)
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

> [!TIP]
>
> ### 7. Estrategia de Pruebas
>
> |      Flujo       |     Tipo de Prueba     | Fecha de Inicio | Fecha Fin  |     Ambiente     |                                                                         Test Execution                                                                          |
> | :--------------: | :--------------------: | :-------------: | :--------: | :--------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------: |
> | Obtención de Datos para Asistencia | 🔧 Pruebas Funcionales |   03/07/2025    | 03/07/2025 |  🔧 Desarrollo   |     [SIASIS-TE-1](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/test-plans/SIASIS-TP-1/Desarrollo/SIASIS-TE-1.md "Ir al TestExecution")     |
> | Obtención de Datos para Asistencia | 🔧 Pruebas Funcionales |   03/07/2025    | 03/07/2025 | 🧪 Certificación | [SIASIS-TE-2](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/test-plans/SIASIS-TP-1/Certificaci%C3%B3n/SIASIS-TE-2.md "Ir al TestExecution") |
> | Obtención de Datos para Asistencia | 🔧 Pruebas Funcionales |   03/07/2025    | 03/07/2025 |  🚀 Producción   |  [SIASIS-TE-3](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/test-plans/SIASIS-TP-1/Producci%C3%B3n/SIASIS-TE-3.md "Ir al TestExecution")   |

---

## 📊 Métricas y Criterios de Salida

> [!IMPORTANT]
>
> ### 🎯 Criterios de Éxito
>
> - ✅ **95%** de casos de prueba ejecutados exitosamente
> - ✅ **100%** de casos críticos pasando
> - ✅ **0** bugs críticos o de alta prioridad abiertos
> - ✅ **Tiempo de respuesta** < 2 segundos para operaciones críticas
> - ✅ **Cobertura de código** > 80%

> [!WARNING]
>
> ### 🚨 Criterios de Bloqueo
>
> - ❌ Falla en funcionalidades críticas de autenticación
> - ❌ Pérdida de datos en operaciones CRUD
> - ❌ Tiempo de respuesta > 5 segundos
> - ❌ Errores de seguridad identificados

---

**📅 Última Actualización:** 03/07/2025
**✅ Estado de Aprobación:** Aprobado
**👤 Aprobado por:** Juan Chavez - Lider Técnico
