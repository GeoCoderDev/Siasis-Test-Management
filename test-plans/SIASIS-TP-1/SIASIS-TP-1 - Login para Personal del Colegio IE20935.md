# 📋 Test Plan: SIASIS-TP-1 - Login para Personal del Colegio IE20935

> [!IMPORTANT]
>
> **Fecha de Creación:** 28/06/2025
> **Responsable: Juan Chavez**
> **Sprint/Release:** 5
> **Estado:** ✅ Completed

---

## 📖 Historia de Usuario

> [!NOTE]
>
> ### 🎯 Historia de Usuario Principal
>
> **COMO** Personal del Colegio IE20935 _(Directivos, Profesores, Auxiliares, Personales administrativos, etc)_
>
> **QUIERO** poder iniciar sesión en el sistema de asistencia SIASIS mediante un nombre de usuario y una contraseña
>
> **PARA** poder hacer uso del sistema segun mi rol

### ✅ Criterios de Aceptación

> [!TIP]
>
> #### 📝 Criterio de Aceptación 1:
>
> **Dado** que soy un usuario del sistema SIASIS
>
> **Cuando** ingreso mis credenciales en la interfaz del login del sistema
>
> **Entonces** logro iniciar sesión y visualizar la interfaz de bienvenida al sistema

> [!TIP]
>
> #### 📝 Criterio de Aceptación 2:
>
> **Dado** que no soy un usuario del sistema SIASIS
>
> **Cuando** intento ingresar al sistema con credenciales invalidas
>
> **Entonces** no puedo acceder al sistema
>
> **Y** la interfaz muestra un error de credenciales invalidas

> [!TIP]
>
> #### 📝 Criterio de Aceptación 3:
>
> **Dado** que las interfaces de Login estan desarrolladas
>
> **Cuando** accedo al sistema desde dispositivos con diferentes tamaños
>
> **Entonces** las interfaces no se deben deformar y deben permanecer presentables para el usuario.

---

## 📄 Descripción del Plan

> [!IMPORTANT]
>
> ### 1. Objetivo
>
> Validar el correcto funcionamiento de la interfaz del Login para los 6 roles de personal del Colegio(Directivos, Profesores de Primaria, Profesores de Secundaria, Tutores de Secundaria, Auxiliares, Personales Administrativos)

> [!NOTE]
>
> ### 2. Alcance y Estrategia de Pruebas
>
> #### 2.1. Lo que se va a probar (Funcionalidades)
>
> | Funcionalidad                                   | Responsable | Prioridad |
> | :---------------------------------------------- | ----------- | :-------: |
> | Inicio de Sesión para Directivos               | Juan Chavez |  🔴 Alta  |
> | Inicio de Sesión para Profesores de Primaria   | Juan Chavez |  🔴 Alta  |
> | Inicio de Sesión para Auxiliares               | Juan Chavez |  🔴 Alta  |
> | Inicio de Sesión para Profesores de Secundaria | Juan Chavez |  🔴 Alta  |
> | Inicio de Sesión para Tutores de Secundaria    | Juan Chavez |  🔴 Alta  |
> | Inicio de Sesión de Personal Administrativo    | Juan Chavez |  🔴 Alta  |
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
> | **API01** | API para personal del colegio (Directivos, Auxiliares, Profesores, etc)                                                                                           | ✅ |    |
> | **API02** | API para padres de Familia                                                                                                                                        |    | ❌ |
> | **API03** | API para obtención de hora real UTC                                                                                                                              |    | ❌ |
> | **TPS01** | Tareas programadas con Scripts                                                                                                                                    |    | ❌ |
> | **EMCS01** | Ejecutor múltiple de consultas SQL de Escritura de API01 hacia RDP02 y RDP03                                                                                     |    | ❌ |
> | **EMCN01** | Ejecutor múltiple de consultas SQL de escritura para API02 hacia RDP03                                                                                           |    | ❌ |
> | **RDP01** | Repositorio de Datos Persistentes solo para Archivos del Sistema en General (Fotos de Perfil, Excels de Asistencia, Backups, etc) ➡️**Google Drive**      |    | ❌ |
> | **RDP02** | Repositorio de Datos Persistentes para Datos Relacionados a Personal del Colegio (Directivos, Auxiliares, Profesores, etc) ➡️ PostgreSQL                        |    | ❌ |
> | **RDP03** | Repositorio de Datos Persistentes para Datos Relacionados a Responsables (Padres de Familia/Apoderados) ➡️ MongoDB                                              | ✅ |    |
> | **RDP04** | Repositorio de Datos Persistentes para JSONs con Información de Datos de Asistencia del Día Actual (Se actualiza todos los días por TPS01) ➡️ Blob de Vercel |    | ❌ |
> | **RDP05** | Repositorio de Datos Persistentes para Asistencias Tomadas a lo largo del día actual exclusivamente ➡️ Redis                                                   |    | ❌ |
> |  **SS01**  | Servidor de Sockets para operaciones en tiempo real                                                                                                               |    | ❌ |
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
> | Nivel de Componente    | ✅ |    |
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
> | Producción    |    ✅    |

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
> | Linux             | Ubuntu 20+ |    ✅    |
> | iOS               | 15+        |    ❌    |
> | Android           | 10+        |    ❌    |

---

> [!TIP]
>
> ### 7. Estrategia de Pruebas
>
> |      Flujo      |     Tipo de Prueba     | Fecha de Inicio | Fecha Fin |     Ambiente     |                                                                      Test Execution                                                                      |
> | :--------------: | :--------------------: | :-------------: | :--------: | :---------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------: |
> | Inicio de Sesion | 🔧 Pruebas Funcionales |   03/07/2025   | 03/07/2025 |   🔧 Desarrollo   |     [SIASIS-TE-1](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/test-plans/SIASIS-TP-1/Desarrollo/SIASIS-TE-1.md "Ir al TestExecution")     |
> | Inicio de Sesion | 🔧 Pruebas Funcionales |   03/07/2025   | 03/07/2025 | 🧪 Certificación | [SIASIS-TE-2](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/test-plans/SIASIS-TP-1/Certificaci%C3%B3n/SIASIS-TE-2.md "Ir al TestExecution") |
> | Inicio de Sesion | 🔧 Pruebas Funcionales |   03/07/2025   | 03/07/2025 |  🚀 Producción  |  [SIASIS-TE-3](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/test-plans/SIASIS-TP-1/Producci%C3%B3n/SIASIS-TE-3.md "Ir al TestExecution")  |

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
