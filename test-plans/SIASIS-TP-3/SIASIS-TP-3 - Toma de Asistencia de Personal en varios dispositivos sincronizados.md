# 📋 Test Plan: SIASIS-TP-3 - Toma de Asistencia de Personal en varios dispositivos sincronizados

> [!IMPORTANT]
>
> **Fecha de Creación:** 07/07/2025
> **Responsable: Andry Diego
> Sprint/Release:** 5
> **Estado:** ✅ Completed

---

## 📖 Historia de Usuario

> [!NOTE]
>
> ### 🎯 Historia de Usuario Principal
>
> **COMO** Directivo(Directora/Subdirectora) del Colegio IE20935
>
> **QUIERO** poder tomar las asistencias de los Personales del Colegio en varios dispositivos a la vez sin generar conflictos o desincronizaciones en los mismos.
>
> **PARA** evitar tener diferentes asistencias marcadas en estos varios dispositivos.

### ✅ Criterios de Aceptación

> [!TIP]
>
> #### 📝 Criterio de Aceptación 1:
>
> **Dado** que soy un usuario directivo y he iniciado sesion en varios dispositivos
>
> **Cuando** accedo a la seccion de toma de asistencia de Personal _(Ejemplo: Entrada de profesores de Secundaria)_ en todos los dispositivos
>
> **Y** marco la asistencia de cualquier personal en uno de ellos
>
> **Entonces** la asistencia es registrada en todos los dispositivos a la vez

> [!TIP]
>
> #### 📝 Criterio de Aceptación 2:
>
> **Dado** que soy un usuario directivo y he iniciado sesion en 2 dipositivos (A y B)
>
> **Cuando** accedo a la seccion de toma de asistencia de Personal _(Ejemplo: Entrada de profesores de Secundaria) en el dispositivo A,_ pero en el dispositivo B accedo a otro rol o modo de registro(Entrada o Salida)
>
> **Y** marco la asistencia de cualquier personal en el dispositivo A
>
> **Entonces** la asistencia solo debe ser registrada en el dispositivo A , dado que el dispositivo B se encuentra en otra seccion.

---

## 📄 Descripción del Plan

> [!IMPORTANT]
>
> ### 1. Objetivo
>
> Validar el correcto funcionamiento del marcado de asistencia sincronizado de Personal por parte de un usuario directivo que ha ingresado en varios dispositivos a la misma seccion de toma de asistencia _(Ejemplo: Toma de Asistencia de Entrada para Personal Administrativo)_

> [!NOTE]
>
> ### 2. Alcance y Estrategia de Pruebas
>
> #### 2.1. Lo que se va a probar (Funcionalidades)
>
> | Funcionalidad                                         | Responsable | Prioridad |
> | :---------------------------------------------------- | ----------- | :-------: |
> | Toma de Asistencia de Personal en Varios Dispositivos | Andry Diego | 🟡 Media |
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

> [!TIP]
>
> ### 4. Tipos de Pruebas
>
> | Tipos de Prueba          | Si | No |
> | ------------------------ | :- | :- |
> | Pruebas Funcionales      | ✅ |    |
> | Pruebas de Diseño (GUI) |    | ❌ |
> | Pruebas de Usabilidad    |    | ❌ |
> | Pruebas de Migración    |    | ❌ |
> | Pruebas de Performance   |    | ❌ |
> | Pruebas de Seguridad     |    | ❌ |
> | Pruebas de Portabilidad  |    | ❌ |
> | Otros Tipos de Pruebas   |    | ❌ |

---

> [!NOTE]
>
> ### 5. Niveles de Pruebas
>
> | Niveles                | Si | No |
> | ---------------------- | :- | :- |
> | Nivel de Componente    |    | ❌ |
> | Nivel de Integración  |    | ❌ |
> | Nivel de Sistema (e2e) | ✅ |    |
> | Nivel de Aceptación   |    | ❌ |

---

> [!IMPORTANT]
>
> ### 6. Entorno de Pruebas
>
> #### 6.1. Ambientes
>
> | Ambiente       | Marcar(X) |
> | -------------- | :-------: |
> | Desarrollo     |    ✅    |
> | Certificación |    ✅    |
> | Producción    |    ⏳    |

> [!TIP]
>
> #### 6.2. Tecnología
>
> | Tecnología    | Marcar(X) |
> | -------------- | :-------: |
> | Web            |    ✅    |
> | API            |    ✅    |
> | Base de Datos  |    ❌    |
> | GitHub Actions |    ❌    |
> | Web Sockets    |    ✅    |
> | Otros          |    ❌    |

> [!NOTE]
>
> #### 6.3. Dispositivos
>
> | Dispositivos | Marcar(X) |
> | ------------ | :-------: |
> | Desktop      |    ✅    |
> | Móviles     |    ✅    |
> | Tablets      |    ❌    |
> | Laptops      |    ✅    |
> | Otros        |    ❌    |

> [!WARNING]
>
> #### 6.4. Navegadores (En caso aplique pruebas en la WEB)
>
> | Navegador | Versión | Marcar(X) |
> | --------- | -------- | :-------: |
> | Chrome    | Última  |    ✅    |
> | Firefox   | Última  |    ❌    |
> | Safari    | Última  |    ❌    |
> | Edge      | Última  |    ❌    |
> | Opera     | Última  |    ❌    |

> [!CAUTION]
>
> #### 6.5. Sistemas Operativos
>
> | Sistema Operativo | Versión   | Marcar(X) |
> | ----------------- | ---------- | :-------: |
> | Windows           | 10/11      |    ✅    |
> | macOS             | Monterey+  |    ❌    |
> | Linux             | Ubuntu 20+ |    ❌    |
> | iOS               | 15+        |    ❌    |
> | Android           | 10+        |    ✅    |

---

> [!TIP]
>
> ### 7. Estrategia de Pruebas
>
> |                         Flujo                         |     Tipo de Prueba     | Fecha de Inicio | Fecha Fin |     Ambiente     |                                                                    Test Execution                                                                    |
> | :----------------------------------------------------: | :--------------------: | :-------------: | :--------: | :---------------: | :---------------------------------------------------------------------------------------------------------------------------------------------------: |
> | Toma de Asistencia de Personal con varios dispositivos | 🔧 Pruebas Funcionales |   03/07/2025   | 03/07/2025 |   🔧 Desarrollo   |  [SIASIS-TE-6](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/test-plans/SIASIS-TP-3/Desarrollo/SIASIS-TE-6.md "Ir al Test Execution")  |
> | Toma de Asistencia de Personal con varios dispositivos | 🔧 Pruebas Funcionales |   03/07/2025   | 03/07/2025 | 🧪 Certificación | [SIASIS-TE-7](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/test-plans/SIASIS-TP-3/Certificacion/SIASIS-TE-7.md "Ir al Test Execution") |
> | Toma de Asistencia de Personal con varios dispositivos | 🔧 Pruebas Funcionales |   03/07/2025   | 03/07/2025 |  🚀 Producción  |                                                                          ⌛                                                                          |

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

**📅 Última Actualización:** 07/07/2025
**✅ Estado de Aprobación:** Aprobado
**👤 Aprobado por:** Juan Chavez - Lider Técnico
