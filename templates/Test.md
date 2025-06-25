# 🧪 Test Case: [Nombre del Test Case]

> [!IMPORTANT]
> **ID del Test Case:** TC-XXX-001
> **Fecha de Creación:** [DD/MM/YYYY]
> **Autor:** [Nombre del QA]
> **Última Actualización:** [DD/MM/YYYY]
> **Estado:** 🟡 Draft | 🟢 Ready | 🔵 In Review | ⚪ Approved

---

## 📋 Información General

> [!NOTE]
>
> ### 🔖 Metadatos del Test
>
> | Campo                     | Valor                                                                                |
> | ------------------------- | ------------------------------------------------------------------------------------ |
> | **ID Test Case**    | TC-XXX-001                                                                           |
> | **Nombre**          | [Nombre descriptivo del test]                                                        |
> | **Módulo/Feature** | [Nombre del módulo]                                                                 |
> | **Epic/User Story** | [ID de la historia de usuario]                                                       |
> | **Tipo de Prueba**  | 🔧 Funcional\| 🎨 UI/UX \| ⚡ Performance \| 🔒 Security \| 🔗 Integration \| 🌐 E2E |
> | **Nivel de Prueba** | 🧩 Unit\| 🔗 Integration \| 🌐 System \| ✅ Acceptance                               |
> | **Prioridad**       | 🔴 Critical\| 🟡 High \| 🟢 Medium \| 🔵 Low                                         |
> | **Severidad**       | 🔴 Blocker\| 🟡 Major \| 🟢 Normal \| 🔵 Minor                                       |
> | **Automatizable**   | ✅ Sí\| ❌ No \| ⏳ Futuro                                                          |

---

> [!TIP]
>
> ### 🏷️ Tags y Categorización
>
> **Tags principales:**
>
> ```gherkin
> @smoke @regression @auth @crud @api @web @mobile
> ```
>
> **Tags por componente:**
>
> ```gherkin
> @SIU01 @API01 @RDP02 @SS01
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
> [Descripción clara y concisa de qué se va a probar y por qué es importante]

> [!NOTE]
>
> ### 🎯 Objetivo Principal
>
> **Objetivo:** [Describir qué funcionalidad o comportamiento específico se va a verificar]
>
> **Criterio de Éxito:** [Definir claramente cuándo el test se considera exitoso]

---

## 🔧 Configuración Técnica

> [!WARNING]
>
> ### 💻 Tecnología y Componentes
>
> | Aspecto                         | Detalle                                                     |
> | ------------------------------- | ----------------------------------------------------------- |
> | **Tecnología Principal** | 🌐 Web\| 📱 Mobile \| 🔌 API \| 💾 Database \| 🖥️ Desktop |
> | **Navegadores**           | Chrome, Firefox, Safari, Edge                               |
> | **Dispositivos**          | Desktop, Mobile, Tablet                                     |
> | **Sistemas Operativos**   | Windows, macOS, Linux, iOS, Android                         |
> | **Resoluciones**          | 1920x1080, 1366x768, 375x667 (mobile)                       |

> [!CAUTION]
>
> ### 🏗️ Componentes Involucrados
>
> | Componente      | Descripción                      | Estado Requerido |
> | --------------- | --------------------------------- | ---------------- |
> | **SIU01** | Servidor de Interfaces de Usuario | 🟢 Activo        |
> | **API01** | API para personal del colegio     | 🟢 Activo        |
> | **RDP02** | Base de datos PostgreSQL          | 🟢 Activo        |
> | **SS01**  | Servidor de Sockets               | 🟢 Activo        |

---

## 📝 Definición en Gherkin

> [!TIP]
>
> ### 🥒 Scenario en Gherkin
>
> ```gherkin
> @smoke @auth @web @SIU01 @API01
> Feature: [Nombre de la funcionalidad]
>   Como [tipo de usuario]
>   Quiero [acción que quiere realizar]
>   Para [beneficio o razón]
>
> Background:
>   Given el usuario está en el sistema
>   And el sistema está funcionando correctamente
>   And todos los servicios están disponibles
>
> @TC-XXX-001 @critical @regression
> Scenario: [Nombre del escenario principal]
>   Given [condición inicial específica]
>   And [condición adicional si es necesaria]
>   When [acción principal que ejecuta el usuario]
>   And [acción adicional si es necesaria]
>   Then [resultado esperado principal]
>   And [resultado adicional esperado]
>   And [validación de datos o estado]
>
> @TC-XXX-001-alt @edge-case
> Scenario Outline: [Nombre del escenario con múltiples datos]
>   Given [condición inicial con parámetro <parametro>]
>   When [acción con <parametro>]
>   Then [resultado esperado con <resultado>]
>
>   Examples:
>     | parametro | resultado |
>     | valor1    | resultado1 |
>     | valor2    | resultado2 |
>     | valor3    | resultado3 |
> ```

---

## ⚙️ Precondiciones y Setup

> [!IMPORTANT]
>
> ### 🔧 Precondiciones
>
> #### Estado del Sistema:
>
> - ✅ Aplicación desplegada y funcionando
> - ✅ Base de datos con datos de prueba cargados
> - ✅ Servicios externos disponibles
> - ✅ Conectividad de red estable
>
> #### Datos de Prueba Requeridos:
>
> - 👤 **Usuario de prueba:** `test.user@colegio.edu`
> - 🔑 **Contraseña:** `TestPass123!`
> - 📊 **Datos específicos:** [Describir datos específicos necesarios]
>
> #### Configuración del Ambiente:
>
> - 🌐 **URL Base:** `https://test.colegio.edu`
> - 🔧 **Ambiente:** Certificación
> - 📱 **Dispositivo:** [Especificar si aplica]

---

## 📋 Pasos de Ejecución

> [!NOTE]
>
> ### 🚶‍♂️ Pasos Detallados
>
> | # | Acción                      | Datos de Entrada   | Resultado Esperado            |
> | - | ---------------------------- | ------------------ | ----------------------------- |
> | 1 | [Acción específica paso 1] | [Datos necesarios] | [Resultado esperado del paso] |
> | 2 | [Acción específica paso 2] | [Datos necesarios] | [Resultado esperado del paso] |
> | 3 | [Acción específica paso 3] | [Datos necesarios] | [Resultado esperado del paso] |
> | 4 | [Acción específica paso 4] | [Datos necesarios] | [Resultado esperado del paso] |
> | 5 | [Acción específica paso 5] | [Datos necesarios] | [Resultado esperado del paso] |

---

## ✅ Criterios de Aceptación

> [!SUCCESS]
>
> ### 🎯 Resultado Esperado Principal
>
> [Descripción detallada del resultado principal que debe obtenerse]

> [!TIP]
>
> ### ✅ Validaciones Específicas
>
> #### Validaciones Funcionales:
>
> - ✅ [Validación funcional 1]
> - ✅ [Validación funcional 2]
> - ✅ [Validación funcional 3]
>
> #### Validaciones de UI/UX:
>
> - ✅ [Validación de interfaz 1]
> - ✅ [Validación de interfaz 2]
> - ✅ [Validación de usabilidad]
>
> #### Validaciones de Datos:
>
> - ✅ [Validación de datos 1]
> - ✅ [Validación de integridad]
> - ✅ [Validación de persistencia]

---

## 🚫 Casos Negativos y Edge Cases

> [!WARNING]
>
> ### ⚠️ Escenarios de Error
>
> | Escenario                   | Acción                        | Resultado Esperado          |
> | --------------------------- | ------------------------------ | --------------------------- |
> | **Datos Inválidos**  | [Ingreso de datos incorrectos] | [Mensaje de error esperado] |
> | **Sin Permisos**      | [Acceso sin autorización]     | [Bloqueo o redirección]    |
> | **Timeout**           | [Operación que excede tiempo] | [Manejo de timeout]         |
> | **Conexión Perdida** | [Pérdida de conectividad]     | [Recuperación o error]     |

---

## 📊 Métricas y Performance

> [!INFO]
>
> ### ⏱️ Criterios de Performance (si aplica)
>
> | Métrica                      | Valor Esperado | Crítico      |
> | ----------------------------- | -------------- | ------------- |
> | **Tiempo de Respuesta** | < 2 segundos   | < 5 segundos  |
> | **Tiempo de Carga**     | < 3 segundos   | < 10 segundos |
> | **Uso de Memoria**      | < 500MB        | < 1GB         |
> | **Ancho de Banda**      | < 1MB          | < 5MB         |

---

## 🔗 Dependencias y Relaciones

> [!NOTE]
>
> ### 🔗 Dependencias
>
> #### Test Cases Relacionados:
>
> - 📋 **Pre-requisito:** TC-XXX-000 (Setup inicial)
> - 🔄 **Dependiente:** TC-XXX-002 (Test que depende de este)
> - 🔗 **Relacionado:** TC-XXX-003 (Funcionalidad similar)
>
> #### Historias de Usuario:
>
> - 📝 **US-001:** Como usuario quiero...
> - 📝 **US-002:** Como administrador necesito...

---

## 🎭 Roles y Permisos

> [!CAUTION]
>
> ### 👥 Roles Involucrados
>
> | Rol                   | Permisos Necesarios                  | Acciones Permitidas            |
> | --------------------- | ------------------------------------ | ------------------------------ |
> | **Directivo**   | Admin completo                       | Todas las operaciones          |
> | **Profesor**    | Lectura/Escritura módulos asignados | CRUD estudiantes de sus clases |
> | **Auxiliar**    | Lectura general                      | Consultas y reportes           |
> | **Responsable** | Lectura limitada                     | Ver info de sus hijos          |

---

## 📎 Evidencias y Documentación

> [!TIP]
>
> ### 📸 Evidencias Requeridas
>
> #### Durante la Ejecución:
>
> - 📸 Screenshot del estado inicial
> - 📸 Screenshot de cada paso crítico
> - 📸 Screenshot del resultado final
> - 🎥 Video de la ejecución completa (si es complejo)
>
> #### Logs y Datos:
>
> - 📝 Logs de aplicación
> - 📝 Logs de base de datos
> - 📝 Request/Response de APIs
> - 📝 Tiempos de respuesta

---

## 📞 Información de Contacto

> [!INFO]
>
> ### 👥 Responsables
>
> | Rol                      | Nombre       | Email   | Responsabilidad           |
> | ------------------------ | ------------ | ------- | ------------------------- |
> | **Autor del Test** | [Nombre QA]  | [email] | Creación y mantenimiento |
> | **Product Owner**  | [Nombre PO]  | [email] | Validación de criterios  |
> | **Tech Lead**      | [Nombre TL]  | [email] | Revisión técnica        |
> | **Dev Assignee**   | [Nombre Dev] | [email] | Corrección de bugs       |

---

## 📝 Notas y Observaciones

> [!NOTE]
>
> ### 💡 Notas Importantes
>
> - [Nota importante 1]
> - [Nota importante 2]
> - [Consideración especial]
>
> ### 🔄 Historial de Cambios
>
> | Fecha        | Versión | Cambio                | Autor    |
> | ------------ | -------- | --------------------- | -------- |
> | [DD/MM/YYYY] | 1.0      | Creación inicial     | [Nombre] |
> | [DD/MM/YYYY] | 1.1      | [Descripción cambio] | [Nombre] |

---

**📅 Última Actualización:** [DD/MM/YYYY HH:MM]
**✅ Estado de Revisión:** [Pendiente/En Revisión/Aprobado]
**👤 Revisado por:** [Nombre y Cargo]
