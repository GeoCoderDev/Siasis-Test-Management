# 📋 Test Plan: SIASIS-TP-XXXX - [Nombre del Plan]

> [!IMPORTANT]
>
> **Fecha de Creación:** [Fecha]
> **Responsable:** [Nombre]
> **Sprint/Release:** [Número]
> **Estado:** 🟡 En Progreso

---

## 📖 Historia de Usuario

> [!NOTE]
>
> ### 🎯 Historia de Usuario Principal
>
> **COMO** [Tipo de usuario - Directivo/Profesor/Auxiliar/Responsable]
>
> **QUIERO** [Funcionalidad específica que se va a probar]
>
> **PARA** [Beneficio o razón del negocio]

### ✅ Criterios de Aceptación

> [!TIP]
>
> #### 📝 Criterio de Aceptación 1:
>
> **Dado** [Condición inicial o contexto]
>
> **Cuando** [Acción que se realiza]
>
> **Entonces** [Resultado esperado]

> [!TIP]
>
> #### 📝 Criterio de Aceptación 2:
>
> **Dado** [Condición inicial o contexto]
>
> **Cuando** [Acción que se realiza]
>
> **Entonces** [Resultado esperado]

---

## 📄 Descripción del Plan

> [!IMPORTANT]
>
> ### 1. Objetivo
>
> [Describir claramente el objetivo principal de este plan de pruebas]

> [!NOTE]
>
> ### 2. Alcance y Estrategia de Pruebas
>
> #### 2.1. Lo que se va a probar (Funcionalidades)
>
> | Funcionalidad     | Responsable | Prioridad |
> | :---------------- | ----------- | :-------: |
> | [Funcionalidad 1] | [Nombre]    |  🔴 Alta  |
> | [Funcionalidad 2] | [Nombre]    | 🟡 Media |
> | [Funcionalidad 3] | [Nombre]    |  🟢 Baja  |
> | [Funcionalidad 4] | [Nombre]    |  🔴 Alta  |
> | [Funcionalidad 5] | [Nombre]    | 🟡 Media |
>
> #### 2.2. Lo que NO se va a probar
>
> - ❌ [Funcionalidad excluida 1]
> - ❌ [Funcionalidad excluida 2]
> - ❌ [Funcionalidad excluida 3]

---

> [!WARNING]
>
> ### 3. Componentes Impactados
>
> |    Componente    | Descripción                                                                                                                                                      | Impacto | Estado |
> | :--------------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :----: |
> | **SIU01** | Servidor de Interfaces de Usuario                                                                                                                                 |  ✅ SI  |   🟢   |
> | **API01** | API para personal del colegio (Directivos, Auxiliares, Profesores, etc)                                                                                           |  ✅ SI  |   🟢   |
> | **API02** | API para padres de Familia                                                                                                                                        |  ❌ NO  |   ⚪   |
> | **API03** | API para obtención de hora real UTC                                                                                                                              |  ✅ SI  |   🟡   |
> | **TPS01** | Tareas programadas con Scripts                                                                                                                                    |  ❌ NO  |   ⚪   |
> | **EMCS01** | Ejecutor múltiple de consultas SQL de Escritura de API01 hacia RDP02 y RDP03                                                                                     |  ✅ SI  |   🟢   |
> | **EMCS02** | Ejecutor múltiple de consultas SQL de escritura para API02 hacia RDP03                                                                                           |  ❌ NO  |   ⚪   |
> | **RDP01** | Repositorio de Datos Persistentes solo para Archivos del Sistema en General (Fotos de Perfil, Excels de Asistencia, Backups, etc) ➡️**Google Drive**      |  ✅ SI  |   🟢   |
> | **RDP02** | Repositorio de Datos Persistentes para Datos Relacionados a Personal del Colegio (Directivos, Auxiliares, Profesores, etc) ➡️ PostgreSQL                        |  ✅ SI  |   🟢   |
> | **RDP03** | Repositorio de Datos Persistentes para Datos Relacionados a Responsables (Padres de Familia/Apoderados) ➡️ MongoDB                                              |  ❌ NO  |   ⚪   |
> | **RDP04** | Repositorio de Datos Persistentes para JSONs con Información de Datos de Asistencia del Día Actual (Se actualiza todos los días por TPS01) ➡️ Blob de Vercel |  ✅ SI  |   🟡   |
> | **RDP05** | Repositorio de Datos Persistentes para Asistencias Tomadas a lo largo del día actual exclusivamente ➡️ Redis                                                   |  ✅ SI  |   🟡   |
> |  **SS01**  | Servidor de Sockets para operaciones en tiempo real                                                                                                               |  ✅ SI  |   🟢   |
> |  **SE01**  | Servicio Externo de Correo Electrónico por GMAIL de Google                                                                                                       |  ❌ NO  |   ⚪   |

---

> [!TIP]
>
> ### 4. Tipos de Pruebas
>
> | Tipos de Prueba          | Si | No |
> | ------------------------ | :- | :- |
> | Pruebas Funcionales      | ✅ | ❌ |
> | Pruebas de Diseño (GUI) | ✅ | ❌ |
> | Pruebas de Usabilidad    | ✅ | ❌ |
> | Pruebas de Migración    | ❌ | ✅ |
> | Pruebas de Performance   | ✅ | ❌ |
> | Pruebas de Seguridad     | ✅ | ❌ |
> | Pruebas de Portabilidad  | ❌ | ✅ |
> | Otros Tipos de Pruebas   | ❌ | ✅ |

---

> [!NOTE]
>
> ### 5. Niveles de Pruebas
>
> | Niveles                | Si | No |
> | ---------------------- | :- | :- |
> | Nivel de Componente    | ✅ | ❌ |
> | Nivel de Integración  | ✅ | ❌ |
> | Nivel de Sistema (e2e) | ✅ | ❌ |
> | Nivel de Aceptación   | ✅ | ❌ |

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
> | Producción    |    ✅    |

> [!TIP]
>
> #### 6.2. Tecnología
>
> | Tecnología    | Marcar(X) |
> | -------------- | :-------: |
> | Web            |    ✅    |
> | API            |    ✅    |
> | Base de Datos  |    ✅    |
> | GitHub Actions |    ✅    |
> | Otros          |    ❌    |

> [!NOTE]
>
> #### 6.3. Dispositivos
>
> | Dispositivos | Marcar(X) |
> | ------------ | :-------: |
> | Desktop      |    ✅    |
> | Móviles     |    ✅    |
> | Tablets      |    ✅    |
> | Laptops      |    ✅    |
> | Otros        |    ❌    |

> [!WARNING]
>
> #### 6.4. Navegadores (En caso aplique pruebas WEB)
>
> | Navegador | Versión | Marcar(X) |
> | --------- | -------- | :-------: |
> | Chrome    | Última  |    ✅    |
> | Firefox   | Última  |    ✅    |
> | Safari    | Última  |    ✅    |
> | Edge      | Última  |    ✅    |
> | Opera     | Última  |    ❌    |

> [!CAUTION]
>
> #### 6.5. Sistemas Operativos
>
> | Sistema Operativo | Versión   | Marcar(X) |
> | ----------------- | ---------- | :-------: |
> | Windows           | 10/11      |    ✅    |
> | macOS             | Monterey+  |    ✅    |
> | Linux             | Ubuntu 20+ |    ✅    |
> | iOS               | 15+        |    ✅    |
> | Android           | 10+        |    ✅    |

---

> [!IMPORTANT]
>
> ### 7. Lista de Tests a Usar
>
> | Tag Identificador        | Descripción                          |  | Desarrollo | Certificación | Producción |
> | ------------------------ | ------------------------------------- | - | :--------: | :------------: | :---------: |
> | `@auth-login`          | Pruebas de autenticación de usuarios |  |     ✅     |       ✅       |     ✅     |
> | `@crud-estudiantes`    | Operaciones CRUD de estudiantes       |  |     ✅     |       ✅       |     ❌     |
> | `@asistencia-registro` | Registro de asistencias diarias       |  |     ✅     |       ✅       |     ✅     |
> | `@reportes-generacion` | Generación de reportes               |  |     ✅     |       ✅       |     ⏳     |
> | `@performance-load`    | Pruebas de carga y rendimiento        |  |     ❌     |       ✅       |     ✅     |
> | `@security-tests`      | Pruebas de seguridad                  |  |     ✅     |       ✅       |     ✅     |
> | `@ui-responsiveness`   | Pruebas de diseño responsivo         |  |     ✅     |       ✅       |     ❌     |

---

> [!TIP]
>
> ### 8. Estrategia de Pruebas
>
> |                 Flujo                 | Tipo de Prueba             | Fecha de Inicio |  Fecha Fin  |     Ambiente     | Test Execution |
> | :------------------------------------: | -------------------------- | :-------------: | :----------: | :---------------: | :------------: |
> |            Inicio de Sesion            | 🔧 Pruebas Unitarias       |  [DD/MM/YYYY]  | [DD/MM/YYYY] |   🔧 Desarrollo   |  `TE-001T`  |
> |     Toma de Asistencia de Personal     | 🔗 Pruebas de Integración |  [DD/MM/YYYY]  | [DD/MM/YYYY] | 🧪 Certificación |   `TE-002`   |
> | **Edicion de Datos de Personal** | 🌐 Pruebas E2E             |  [DD/MM/YYYY]  | [DD/MM/YYYY] | 🧪 Certificación |   `TE-003`   |
> |                  etc                  | ⚡ Pruebas de Performance  |  [DD/MM/YYYY]  | [DD/MM/YYYY] |  🚀 Producción  |   `TE-004`   |
> |                  etc                  | ✅ Pruebas de Aceptación  |  [DD/MM/YYYY]  | [DD/MM/YYYY] |  🚀 Producción  |   `TE-005`   |
> |                  etc                  | 🔒 Pruebas de Seguridad    |  [DD/MM/YYYY]  | [DD/MM/YYYY] | 🧪 Certificación |   `TE-006`   |
> |                  etc                  | 📱 Pruebas de Usabilidad   |  [DD/MM/YYYY]  | [DD/MM/YYYY] | 🧪 Certificación |   `TE-007`   |

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

**📅 Última Actualización:** [Fecha]
**✅ Estado de Aprobación:** [Pendiente/Aprobado/Rechazado]
**👤 Aprobado por:** Juan Chavez - Lider Técnico
