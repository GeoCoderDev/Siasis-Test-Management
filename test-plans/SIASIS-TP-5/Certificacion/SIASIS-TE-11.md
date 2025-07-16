# 🚀 Test Execution: Validar correcto funcionamiento de los Endpoints de API 01

> [!IMPORTANT]
> **ID de Ejecución:** SIASIS-TE-11
> **Fecha de Ejecución:** 15/07/2025
> **Ejecutor:** Jose Gil
> **Duración:** 52.578 s
> **Estado:** ✅ Completed

---

## 📋 Información General de la Ejecución

> [!NOTE]
>
> ### 🔖 Metadatos de Ejecución
>
>
> |         Campo         |                                                                                   Valor                                                                                   |
> | :----------------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
> |   **ID Ejecución**   |                                                                               SIASIS-TE-11                                                                               |
> |       **Nombre**       |                                                      Validar correcto funcionamiento Endpoints utilizados para API01                                                      |
> |     **Test Plan**     | [SIASIS-TP-5](https://https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/test-plans/SIASIS-TP-5/SIASIS-TP-5%20-%20Endpoints%20API01.md)("Ir al Test Plan") |
> |   **Sprint/Release**   |                                                                                     5                                                                                     |
> |   **Build/Versión**   |                                                                                    1.0                                                                                    |
> | **Tipo de Ejecución** |                                                                   ✨ New Features\| 🐛 Bug Verification                                                                   |
> | **Modo de Ejecución** |                                                                              👤 Automatizado                                                                              |
> |     **Prioridad**     |                                                                                 🟢 Medium                                                                                 |

---

## 🌐 Configuración del Ambiente

> [!WARNING]
>
> ### 🏗️ Detalles del Ambiente
>
>
> | Aspecto           |         Configuración         |
> | ------------------- | :-------------------------------: |
> | **Ambiente**      |        🧪 Certificación        |
> | **URL Base**      | https://siasis-cert.vercel.app |
> | **Base de Datos** | instancia 1,2,3 de RDP05(Redis) |
> | **Servidor**      |         No hay detalles         |
> | **Red/VPN**       |         No hay detalles         |

> [!TIP]
>
> ### 💻 Configuración Técnica
>
>
> |    Tecnología    |    Versión    | Estado |
> | :-----------------: | :---------------: | :------: |
> |   **Frontend**   |  React 18.2.0  |   🟢   |
> |    **Backend**    | Node.js 18.17.0 |   🟢   |
> | **Base de Datos** | PostgreSQL 15.3 |   🟢   |
> |     **Cache**     |    Redis 7.0    |   🟢   |
> |   **WebSocket**   | Socket.io 4.7.0 |   🟢   |

> [!CAUTION]
>
> ### 🖥️ Configuración de Dispositivos
>
>
> | Dispositivo | Sistema Operativo | Navegador   |
> | ------------- | ------------------- | ------------- |
> | **Desktop** | Windows 11        | Chrome 115+ |

---

## 📊 Resumen de Tests a Ejecutar

> [!INFO]
>
> ### 📈 Estadísticas Generales
>
>
> |        Métrica        | Cantidad | Porcentaje |
> | :-----------------------: | :--------: | :----------: |
> |   **Total de Tests**   |    24    |    100%    |
> |   **Tests Críticos**   |    0    |     0%     |
> | **Tests Automatizados** |    0    |     0%     |
> |   **Tests Manuales**   |    0    |     0%     |
> |    **Tests Nuevos**    |    24    |    100%    |
> | **Tests de Regresión** |    24    |    100%    |

---

## 📝 Lista Detallada de Tests

> [!NOTE]
>
> ### 🧪 Tests por Módulo/Funcionalidad
>
> #### 📝 Módulo de Endpoints API01
>
>
> |                                                                                                                          ID Test                                                                                                                          |                                                   Nombre                                                   | Tipo      | Prioridad | Estado    | Tiempo Est. |
> | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------------------: | ----------- | ----------- | ----------- | :-----------: |
> |                                   [SIASIS-TC-12](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/API01/SIASIS-TC-12%20-%20Validar%20Inicio%20de%20Sesion%20Como%20Auxiliar.md "Ir al Test Case")                                   |                          Validar Inicio de Sesion Exitoso para el rol de Auxiliar                          | Funcional | 🟢 Medium | ✅ Passed |    1 min    |
> |                            [SIASIS-TC-13](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/API01/SIASIS-TC-13%20-%20Validar%20Inicio%20de%20Sesion%20Como%20Profesor%20Secundaria.md "Ir al Test Case")                            |              Validar Inicio de Sesion Exitoso para el rol de Profesor de Secundaria(No Tutor)              | Funcional | 🟢 Medium | ✅ Passed |    2 min    |
> |                                   [SIASIS-TC-14](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/API01/SIASIS-TC-14%20-%20Validar%20Inicio%20de%20Sesion%20Como%20Tutor%20.md "Ir al Test Case")                                   |                     Validar Inicio de Sesion Exitoso para el rol de Profesor de Tutor                     | Funcional | 🟢 Medium | ✅ Passed |    2 min    |
> |                                  [SIASIS-TC-15](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/API01/SIASIS-TC-15%20-%20Validar%20Inicio%20de%20Sesion%20Como%20Directivo.mdd "Ir al Test Case")                                  |                         Validar Inicio de Sesion Exitoso para el rol de Directivo                         | Funcional | 🟢 Medium | ✅ Passed |    1 min    |
> |                               [SIASIS-TC-16](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/API01/SIASIS-TC-16%20-%20Validar%20Inicio%20de%20Sesion%20Como%20Personal%20Admin.md "Ir al Test Case")                               |                       Validar Inicio de Sesion Exitoso para el rol de Personal Admin                       | Funcional | 🟢 Medium | ✅ Passed |    2 min    |
> |                           [SIASIS-TC-17](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/API01/SIASIS-TC-17%20-%20Validar%20Inicio%20de%20Sesion%20Como%20Profesor%20de%20Primaria.md "Ir al Test Case")                           |                    Validar Inicio de Sesion Exitoso para el rol de Profesor de Primaria                    | Funcional | 🟢 Medium | ✅ Passed |    2 min    |
> |                   [SIASIS-TC-18](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/API01/SIASIS-TC-18%20-%20Validar%20Cambio%20de%20Foto%20de%20Perfil%20Como%20Profesor%20de%20Primaria%20.md "Ir al Test Case")                   |                         Validar Cambio de foto de Perfil como Profesor de Primaria                         | Funcional | 🟢 Medium | ✅ Passed |    2 min    |
> |                        [SIASIS-TC-19](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/API01/SIASIS-TC-19%20-%20Validar%20Cambio%20de%20Foto%20de%20Perfil%20Como%20Auxiliar%20%20copy.md "Ir al Test Case")                        |                               Validar Cambio de foto de Perfil como Auxiliar                               | Funcional | 🟢 Medium | ✅ Passed |    2 min    |
> |                            [SIASIS-TC-20](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/API01/SIASIS-TC-20%20-%20Validar%20Cambio%20de%20Foto%20de%20Perfil%20Como%20No%20Tutor.md "Ir al Test Case")                            |                               Validar Cambio de foto de Perfil como No Tutor                               | Funcional | 🟢 Medium | ✅ Passed |    2 min    |
> |                             [SIASIS-TC-21](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/API01/SIASIS-TC-21%20-%20Validar%20Cambio%20de%20Foto%20de%20Perfil%20Como%20Tutor%20.md "Ir al Test Case")                             |                         Validar Cambio de foto de Perfil Exitoso para rol de Tutor                         | Funcional | 🟢 Medium | ✅ Passed |    2 min    |
> |                            [SIASIS-TC-22](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/API01/SIASIS-TC-22%20-%20Validar%20Cambio%20de%20Foto%20de%20Perfil%20Como%20Directivo.md "Ir al Test Case")                            |                       Validar Cambio de foto de Perfil Exitoso para rol de Directivo                       | Funcional | 🟢 Medium | ✅ Passed |    2 min    |
> |                         [SIASIS-TC-23](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/API01/SIASIS-TC-23%20-%20Validar%20Cambio%20de%20Foto%20de%20Perfil%20Como%20Personal%20Admin.md "Ir al Test Case")                         |                    Validar Cambio de foto de Perfil Exitoso para rol de Personal Admin                    | Funcional | 🟢 Medium | ✅ Passed |    2 min    |
> |                 [SIASIS-TC-24](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/API01/SIASIS-TC-24%20-%20Validar%20la%20obtenci%C3%B3n%20de%20datos%20del%20rol%20Profesor%20de%20Primaria%20.md "Ir al Test Case")                 |                        Validar la obtención de datos del rol Profesor de Primaria                        | Funcional | 🟢 Medium | ✅ Passed |    2 min    |
> |                      [SIASIS-TC-25](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/API01/SIASIS-TC-25%20-%20Validar%20la%20obtenci%C3%B3n%20de%20datos%20del%20rol%20Personal%20Admin.md "Ir al Test Case")                      |                           Validar la obtención de datos del rol Personal Admin                           | Funcional | 🟢 Medium | ✅ Passed |    2 min    |
> |                          [SIASIS-TC-26](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/API01/SIASIS-TC-26%20-%20Validar%20la%20obtenci%C3%B3n%20de%20datos%20del%20rol%20Auxiliar.md "Ir al Test Case")                          |                              Validar la obtención de datos del rol Auxiliar                              | Funcional | 🟢 Medium | ✅ Passed |    2 min    |
> |                          [SIASIS-TC-27](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/API01/SIASIS-TC-27%20-%20Validar%20la%20obtenci%C3%B3n%20de%20datos%20del%20rol%20Directivo.md "Ir al Test Case")                          |                              Validar la obtención de datos del rol Directivo                              | Funcional | 🟢 Medium | ✅ Passed |    2 min    |
> |                    [SIASIS-TC-28](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/API01/SIASIS-TC-28%20-%20Validar%20la%20obtenci%C3%B3n%20de%20datos%20del%20rol%20Tutor%20Secundaria%20.md "Ir al Test Case")                    |                          Validar la obtención de datos del rol Tutor Secundaria                          | Funcional | 🟢 Medium | ✅ Passed |    2 min    |
> |                        [SIASIS-TC-29](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/API01/SIASIS-TC-29%20-%20Validar%20la%20obtenci%C3%B3n%20de%20datos%20del%20rol%20No%20Tutor%20.md "Ir al Test Case")                        |                              Validar la obtención de datos del rol No Tutor                              | Funcional | 🟢 Medium | ✅ Passed |    2 min    |
> |             [SIASIS-TC-30](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/API01/SIASIS-TC-30%20-%20Validar%20el%20cambio%20de%20estado%20mediante%20el%20DNI%20para%20el%20rol%20de%20Auxiliar.md "Ir al Test Case")             |       Validar que el Directivo cambie el estado Activo/Desactivo de un Auxiliar específico por DNI       | Funcional | 🟢 Medium | ✅ Passed |    2 min    |
> |      [SIASIS-TC-31](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/API01/SIASIS-TC-31%20-%20Validar%20que%20el%20Directivo%20obtenga%20los%20datos%20de%20un%20Auxiliar%20espec%C3%ADfico%20por%20DNI.md "Ir al Test Case")      |               Validar que el Directivo obtenga los datos de un Auxiliar específico por DNI               | Funcional | 🟢 Medium | ✅ Passed |    2 min    |
> |                    [SIASIS-TC-32](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/API01/SIASIS-TC-32%20-%20Validar%20la%20obtenci%C3%B3n%20de%20%20datos%20de%20todos%20los%20Auxiliares.md "Ir al Test Case")                    |         Validar que el Directivo obtenga los datos de todos los auxiliares registrados del Sistema         | Funcional | 🟢 Medium | ✅ Passed |    2 min    |
> |         [SIASIS-TC-33](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/API01/SIASIS-TC-33%20-%20Validar%20el%20cambio%20de%20estado%20mediante%20el%20DNI%20para%20el%20rol%20de%20Personal%20Admin.md "Ir al Test Case")         |    Validar que el Directivo cambie el estado Activo/Desactivo de un Personal Admin específico por DNI    | Funcional | 🟢 Medium | ✅ Passed |    2 min    |
> | [SIASIS-TC-34](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/API01/SIASIS-TC-34%20-%20Validar%20que%20el%20Directivo%20obtenga%20los%20datos%20de%20un%20Personal%20Admin%20espec%C3%ADfico%20por%20DNI%20.md "Ir al Test Case") |            Validar que el Directivo obtenga los datos de un Personal Admin específico por DNI            | Funcional | 🟢 Medium | ✅ Passed |    2 min    |
> |        [SIASIS-TC-35](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/API01/SIASIS-TC-35%20-%20Validar%20la%20obtenci%C3%B3n%20de%20%20los%20datos%20de%20todos%20los%20Personales%20Administrativos.md "Ir al Test Case")        | Validar que el Directivo obtenga los datos de todos los Personales Administrativos registrados del Sistema | Funcional | 🟢 Medium | ✅ Passed |    2 min    |

---

## 📎 Evidencias y Documentación

> [!TIP]
>
> ### 📸 Evidencias de la ejecución
>
> * [SIASIS-TC-38](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/SIU01/Asistencia%20de%20Personal/No%20Directivos/SIASIS-TC-38%20-%20Usuario%20fuera%20del%20per%C3%ADmetro%20del%20colegio.md "Ir al Test Case")    |   [SIASIS-TC-9](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/SIU01/Asistencia%20de%20Personal/No%20Directivos/SIASIS-TC-9%20-%20Registro%20exitoso%20de%20asistencia%20propia%20con%20todas%20las%20condiciones%20ideales.md "Ir al Test Case")
>
>   ![1752456139011](https://file+.vscode-resource.vscode-cdn.net/c%3A/Users/juanc/OneDrive/Escritorio/PROYECTO%20SIASIS/TESTING/Siasis-Test-Management/test-plans/SIASIS-TP-2/Certificacion/image/SIASIS-TE-4/1752456139011.png)
>
> Link del Video de Evidencias:
>
> [![Link del Video De Evidencias](https://img.youtube.com/vi/7oyO36QC4sU/maxresdefault.jpg)](https://youtube.com/shorts/7oyO36QC4sU)
>
> * [SIASIS-TC-36](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/SIU01/Asistencia%20de%20Personal/No%20Directivos/SIASIS-TC-36%20-%20Intento%20de%20marcado%20de%20asistencia%20desde%20dispositivo%20no%20m%C3%B3vil.md "Ir al Test Case")
>
>   ![1752456544829](image/SIASIS-TE-4/1752456544829.png)
> * [SIASIS-TC-37](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/SIU01/Asistencia%20de%20Personal/No%20Directivos/SIASIS-TC-37%20-%20GPS%20desactivado%20o%20permisos%20denegados.md "Ir al Test Case")
>
>   ![1752456789177](image/SIASIS-TE-4/1752456789177.png)
> * [SIASIS-TC-39](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/SIU01/Asistencia%20de%20Personal/No%20Directivos/SIASIS-TC-39%20-%20Usuario%20fuera%20del%20rango%20horario%20laboral.md "Ir al Test Case")
>
>   ![1752456893553](image/SIASIS-TE-4/1752456893553.png)
> * [SIASIS-TC-40](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/SIU01/Asistencia%20de%20Personal/No%20Directivos/SIASIS-TC-40%20-%20Asistencia%20ya%20registrada%20para%20el%20d%C3%ADa%20actual.md "Ir al Test Case")
>
>   ![1752457804420](image/SIASIS-TE-4/1752457804420.png)
> * [SIASIS-TC-41](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/SIU01/Asistencia%20de%20Personal/No%20Directivos/SIASIS-TC-41%20-%20Error%20de%20conexi%C3%B3n%20de%20red%20al%20marcar%20asistencia%20propia.md "Ir al Test Case")
>
>   ![1752458036133](image/SIASIS-TE-4/1752458036133.png)
> * [SIASIS-TC-42](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/SIU01/Asistencia%20de%20Personal/No%20Directivos/SIASIS-TC-42%20-%20%20Marcado%20de%20Asistencia%20Propia%20en%20D%C3%ADa%20de%20evento%20o%20feriado%20registrado%20en%20el%20Sistema.md "Ir al Test Case")
>
>   ![1752457342671](https://file+.vscode-resource.vscode-cdn.net/c%3A/Users/juanc/OneDrive/Escritorio/PROYECTO%20SIASIS/TESTING/Siasis-Test-Management/test-plans/SIASIS-TP-2/Certificacion/image/SIASIS-TE-4/1752457342671.png)

## 🐛 Defectos Encontrados

> [!WARNING]
>
> No se encontraron Bugs.

---

## 🔍 Análisis de Bloqueos

> [!CAUTION]
>
> ### 🚫 Tests Bloqueados
>
> No hubieron Test Bloqueados

---

## 🛠️ Herramientas y Automatización

> [!INFO]
>
> Se utilizo Karate Labs como herramienta de Automatizacion

---

## 🚨 Gestión de Riesgos

> [!WARNING]
>
> ### ⚠️ Riesgos Identificados
>
>
> | Riesgo                        | Probabilidad | Impacto | Mitigación         | Responsable   |
> | ------------------------------- | -------------- | --------- | --------------------- | --------------- |
> | **Ambiente inestable**        | Media        | Alto    | Ambiente backup     | DevOps        |
> | **Datos de prueba corruptos** | Baja         | Alto    | Backup/Restore plan | QA Lead       |
> | **Ausencia de QA**            | Baja         | Medio   | Cross-training team | Test Manager  |
> | **Bloqueos por bugs**         | Alta         | Medio   | Priorización ágil | Product Owner |

---

## 📋 Criterios de Entrada y Salida

> [!IMPORTANT]
>
> ### ✅ Criterios de Entrada (Entry Criteria)
>
> - ✅ Test Plan aprobado y actualizado
> - ✅ Ambiente de testing configurado y estable
> - ✅ Build deployado y smoke tests pasando
> - ✅ Datos de prueba preparados y validados
> - ✅ Herramientas de testing configuradas
> - ✅ Equipo de QA asignado y disponible

> [!SUCCESS]
>
> ### 🏁 Criterios de Salida (Exit Criteria)
>
> - ✅ 95% de tests ejecutados
> - ✅ 100% de tests críticos pasando
> - ✅ 0 bugs críticos abiertos
> - ✅ 0 bugs de alta prioridad abiertos
> - ✅ Cobertura de funcionalidades > 90%
> - ✅ Reporte de ejecución completo

---

## 📝 Notas y Observaciones

> [!NOTE]
>
> ### 💡 Notas de la Ejecución
>
> - [Nota importante durante la ejecución]
> - [Observación relevante]
> - [Comentario sobre el ambiente]
>
> ### 🔄 Lecciones Aprendidas
>
> - [Lección aprendida 1]
> - [Mejora para futuras ejecuciones]
> - [Optimización identificada]

> [!TIP]
>
> ### 📋 Checklist de Finalización
>
> - [X] Todos los tests ejecutados
> - [ ] Bugs reportados en Jira
> - [X] Evidencias archivadas
> - [x] Reporte de ejecución generado
> - [ ] Métricas actualizadas
> - [X] Stakeholders notificados
> - [X] Ambiente liberado

---

**📅 Fecha de Ejecución:** /07/2025
**⏰ Hora de Inicio:** 23:50hs
**⏰ Hora de Finalización:** 23:51hs
**👤 Ejecutado por:** Jose Gil
**✅ Estado Final:** Completado
