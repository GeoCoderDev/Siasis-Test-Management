# 🚀 Test Execution: Validación de Protección contra SQL Injection en API01

> [!IMPORTANT] > **ID de Ejecución:** SIASIS-TE-4
> **Fecha de Ejecución:** 06/07/2025
> **Ejecutor:** Andry Diego
> **Duración:** 60 min
> **Estado:** ✅ Completed

---

## 📋 Información General de la Ejecución

> [!NOTE]
>
> ### 🔖 Metadatos de Ejecución
>
> |         Campo         |                                                                            Valor                                                                             |
> | :-------------------: | :----------------------------------------------------------------------------------------------------------------------------------------------------------: |
> |   **ID Ejecución**    |                                                                         SIASIS-TE-4                                                                          |
> |      **Nombre**       |                                             Validación de protección contra SQL Injection en endpoints de API01                                              |
> |     **Test Plan**     | [SIASIS-TP-4](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/test-plans/SIASIS-TP-4/SIASIS-TP-4%20-%20SQL_Injection.md "Ir al Test Plan") |
> |  **Sprint/Release**   |                                                                              5                                                                               |
> |   **Build/Versión**   |                                                                             1.0                                                                              |
> | **Tipo de Ejecución** |                                                                     🔒 Security Testing                                                                      |
> | **Modo de Ejecución** |                                                                          👤 Manual                                                                           |
> |     **Prioridad**     |                                                                         🔴 Critical                                                                          |

---

## 🌐 Configuración del Ambiente

> [!WARNING]
>
> ### 🏗️ Detalles del Ambiente
>
> | Aspecto           |         Configuración          |
> | ----------------- | :----------------------------: |
> | **Ambiente**      |         🧪 Desarrollo          |
> | **URL Base**      | https://siasis-dev.vercel.app/ |
> | **Base de Datos** |  instancia 1 de RDP05(Redis)   |
> | **Servidor**      |        No hay detalles         |
> | **Red/VPN**       |        No hay detalles         |

> [!TIP]
>
> ### 💻 Configuración Técnica
>
> |    Tecnología     |     Versión     | Estado |
> | :---------------: | :-------------: | :----: |
> |   **Frontend**    |  React 18.2.0   |   🟢   |
> |    **Backend**    | Node.js 18.17.0 |   🟢   |
> | **Base de Datos** | PostgreSQL 15.3 |   🟢   |
> |     **Cache**     |    Redis 7.0    |   🟢   |
> |   **WebSocket**   | Socket.io 4.7.0 |   🟢   |

> [!CAUTION]
>
> ### 🖥️ Configuración de Dispositivos
>
> | Dispositivo | Sistema Operativo | Navegador   | Resolución |
> | ----------- | ----------------- | ----------- | ---------- |
> | **Desktop** | Windows 11        | Chrome 115+ | 1920x1080  |
> | **Mobile**  | Android           | Chrome      | 384x728    |

---

## 📊 Resumen de Tests a Ejecutar

> [!INFO]
>
> ### 📈 Estadísticas Generales
>
> |         Métrica         | Cantidad | Porcentaje |
> | :---------------------: | :------: | :--------: |
> |   **Total de Tests**    |    4     |    100%    |
> |   **Tests Críticos**    |    0     |     0%     |
> | **Tests Automatizados** |    0     |     0%     |
> |   **Tests Manuales**    |    4     |    100%    |
> |    **Tests Nuevos**     |    4     |    100%    |
> | **Tests de Regresión**  |    4     |    100%    |

---

## 📝 Lista Detallada de Tests

> [!NOTE]
>
> ### 🧪 Tests por Módulo/Funcionalidad
>
> #### 📝 Módulo de Registro de Asistencia Propia para Usuarios no Directivos
>
> |                                                                                                                                               ID Test                                                                                                                                               |                                         Nombre                                          | Tipo      | Prioridad | Estado    | Tiempo Est. |
> | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------: | --------- | --------- | --------- | :---------: |
> |              [SIASIS-TC-9](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/SIU01/Asistencia%20de%20Personal/No%20Directivos/SIASIS-TC-9%20-%20Registro%20exitoso%20de%20asistencia%20propia%20con%20todas%20las%20condiciones%20ideales.md "Ir al Test Case")               |      Registro exitoso de asistencia propia con todas las<br />condiciones ideales       | Funcional | 🟢 Medium | ✅ Passed |    1 min    |
> |                  [SIASIS-TC-36](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/SIU01/Asistencia%20de%20Personal/No%20Directivos/SIASIS-TC-36%20-%20Intento%20de%20marcado%20de%20asistencia%20desde%20dispositivo%20no%20m%C3%B3vil.md "Ir al Test Case")                  |               Intento de marcado de asistencia desde dispositivo no móvil               | Funcional | 🟢 Medium | ✅ Passed |    2 min    |
> |                                    [SIASIS-TC-37](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/SIU01/Asistencia%20de%20Personal/No%20Directivos/SIASIS-TC-37%20-%20GPS%20desactivado%20o%20permisos%20denegados.md "Ir al Test Case")                                    |                          GPS desactivado o permisos denegados                           | Funcional | 🟢 Medium | ✅ Passed |    2 min    |
> |                               [SIASIS-TC-38](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/SIU01/Asistencia%20de%20Personal/No%20Directivos/SIASIS-TC-38%20-%20Usuario%20fuera%20del%20per%C3%ADmetro%20del%20colegio.md "Ir al Test Case")                               |                         Usuario fuera del perímetro del colegio                         | Funcional | 🟢 Medium | ✅ Passed |    1 min    |

---

## 📎 Evidencias y Documentación

> [!TIP]
>
> ### 📸 Evidencias de la ejecución
>
> - [SIASIS-TC-38](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/SIU01/Asistencia%20de%20Personal/No%20Directivos/SIASIS-TC-38%20-%20Usuario%20fuera%20del%20per%C3%ADmetro%20del%20colegio.md "Ir al Test Case") | [SIASIS-TC-9](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/SIU01/Asistencia%20de%20Personal/No%20Directivos/SIASIS-TC-9%20-%20Registro%20exitoso%20de%20asistencia%20propia%20con%20todas%20las%20condiciones%20ideales.md "Ir al Test Case")
>
>   ![1752456139011](https://file+.vscode-resource.vscode-cdn.net/c%3A/Users/juanc/OneDrive/Escritorio/PROYECTO%20SIASIS/TESTING/Siasis-Test-Management/test-plans/SIASIS-TP-2/Certificacion/image/SIASIS-TE-4/1752456139011.png)
>
> Link del Video de Evidencias:
>
> [![Link del Video De Evidencias](https://img.youtube.com/vi/7oyO36QC4sU/maxresdefault.jpg)](https://youtube.com/shorts/7oyO36QC4sU)
>
> - [SIASIS-TC-36](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/SIU01/Asistencia%20de%20Personal/No%20Directivos/SIASIS-TC-36%20-%20Intento%20de%20marcado%20de%20asistencia%20desde%20dispositivo%20no%20m%C3%B3vil.md "Ir al Test Case")
>
>   ![1752456544829](image/SIASIS-TE-4/1752456544829.png)
>
> - [SIASIS-TC-37](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/SIU01/Asistencia%20de%20Personal/No%20Directivos/SIASIS-TC-37%20-%20GPS%20desactivado%20o%20permisos%20denegados.md "Ir al Test Case")
>
>   ![1752456789177](image/SIASIS-TE-4/1752456789177.png)
>
> - [SIASIS-TC-39](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/SIU01/Asistencia%20de%20Personal/No%20Directivos/SIASIS-TC-39%20-%20Usuario%20fuera%20del%20rango%20horario%20laboral.md "Ir al Test Case")
>
>   ![1752456893553](image/SIASIS-TE-4/1752456893553.png)
>
> - [SIASIS-TC-40](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/SIU01/Asistencia%20de%20Personal/No%20Directivos/SIASIS-TC-40%20-%20Asistencia%20ya%20registrada%20para%20el%20d%C3%ADa%20actual.md "Ir al Test Case")
>
>   ![1752457804420](image/SIASIS-TE-4/1752457804420.png)
>
> - [SIASIS-TC-41](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/SIU01/Asistencia%20de%20Personal/No%20Directivos/SIASIS-TC-41%20-%20Error%20de%20conexi%C3%B3n%20de%20red%20al%20marcar%20asistencia%20propia.md "Ir al Test Case")
>
>   ![1752458036133](image/SIASIS-TE-4/1752458036133.png)
>
> - [SIASIS-TC-42](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/tests/SIU01/Asistencia%20de%20Personal/No%20Directivos/SIASIS-TC-42%20-%20%20Marcado%20de%20Asistencia%20Propia%20en%20D%C3%ADa%20de%20evento%20o%20feriado%20registrado%20en%20el%20Sistema.md "Ir al Test Case")
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
> No se usaron herramientas de automatizacion de pruebas

---

## 🚨 Gestión de Riesgos

> [!WARNING]
>
> ### ⚠️ Riesgos Identificados
>
> | Riesgo                        | Probabilidad | Impacto | Mitigación          | Responsable   |
> | ----------------------------- | ------------ | ------- | ------------------- | ------------- |
> | **Ambiente inestable**        | Media        | Alto    | Ambiente backup     | DevOps        |
> | **Datos de prueba corruptos** | Baja         | Alto    | Backup/Restore plan | QA Lead       |
> | **Ausencia de QA**            | Baja         | Medio   | Cross-training team | Test Manager  |
> | **Bloqueos por bugs**         | Alta         | Medio   | Priorización ágil   | Product Owner |

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
> - [x] Todos los tests ejecutados
> - [ ] Bugs reportados en Jira
> - [x] Evidencias archivadas
> - [ ] Reporte de ejecución generado
> - [ ] Métricas actualizadas
> - [x] Stakeholders notificados
> - [x] Ambiente liberado

---

**📅 Fecha de Ejecución:** 06/07/2025
**⏰ Hora de Inicio:** 6:450PM
**⏰ Hora de Finalización:** 7:45PM
**👤 Ejecutado por:** Juan Chavez
**✅ Estado Final:** Completado
