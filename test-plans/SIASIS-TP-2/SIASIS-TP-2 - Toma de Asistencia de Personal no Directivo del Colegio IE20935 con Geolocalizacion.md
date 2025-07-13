# 📋 Test Plan: SIASIS-TP-2 - Toma de Asistencia de Personal no Directivo del Colegio IE20935 con Geolocalizacion

> [!IMPORTANT]
>
> **Fecha de Creación:** 03/07/2025
> **Responsable: Juan Chavez**
> **Sprint/Release:** 5
> **Estado:** ✅ Completed

---

## 📖 Historia de Usuario

> [!NOTE]
>
> ### 🎯 Historia de Usuario Principal
>
> **COMO** Personal del Colegio IE20935 no Directivo _(Profesores, Auxiliares, Personales administrativos, etc)_
>
> **QUIERO** poder registrar mi asistencia propia desde mi celular
>
> **PARA** maracar mi propia asistencia sin depender que algun usuario con rol de Directivo tenga que marcar mi Asistencia

### ✅ Criterios de Aceptación

> [!TIP]
>
> #### 📝 Criterio de Aceptación 1: Marcado de Asistencia Propia Correcta
>
> **Dado** que soy un usuario no directivo
> **Y** estoy usando mi celular o algun dispositivo movil mas no una laptop o otro tipo de dispositivos
> **Y** me encuentro dentro del colegio
> ****Y**** me encuentro en mi rango laboral *(Maximo 2 hora antes de mi entrada hasta maximo 2 horas despues de la salida)*
> **Y** aun no he marcado mi asistencia en el sistema
> **Y** he iniciado sesión en el sistema
>
> **Cuando** me aparece un boton flotante para marcar entrada(boton color verde) o salida(color rojo) segun mi horario
> **Y** hago clic en dicho boton
> **Y** me aparece un modal de marcado de asistencia de entrada o salida(Depende de la hora en la que me encuentre y de mi horario laboral)
> **Y** hago clic en el boton que indica **"Registrar Entrada"** o **"Registrar Salida"
> **Y** doy permisos de acceso a GPS en mi dispositivo**
>
> **Entonces** mi asistencia de entrada o salida es registrada
> **Y** me aparece otro modal confirmando que mi asistencia ha sido registrada en la hora actual

> [!TIP]
>
> #### 📝 Criterio de Aceptación 2: Dispositivo No Móvil
>
> **Dado** que soy un usuario no directivo
> **Y** estoy usando una laptop, computadora de escritorio u otro dispositivo que no sea un celular
> **Y** me encuentro en mi rango laboral
> **Y** he iniciado sesión en el sistema
>
> **Cuando** me aparece un boton flotante para marcar entrada(boton color verde) o salida(color rojo) segun mi horario
> **Y** hago clic en dicho boton
>
> **Entonces**  me aparece un modal informativo indicando "Esta función solo está disponible en dispositivos móviles"

> [!TIP]
>
> #### 📝 Criterio de Aceptación 3: GPS Desactivado o Permisos Denegados
>
> **Dado** que soy un usuario no directivo
> **Y** estoy usando mi celular
> **Y** me encuentro en mi rango laboral
> **Y** he iniciado sesión en el sistema
> **Y** tengo el GPS desactivado o he denegado permisos de ubicación
>
> **Cuando** hago clic en el botón flotante de marcado de asistencia
> **Y** hago clic en "Registrar Entrada" o "Registrar Salida"
>
> **Entonces** me aparece un modal solicitando que active el GPS
> **Y** me proporciona instrucciones para habilitar la geolocalización
> **Y** la asistencia no es registrada hasta que se concedan los permisos

> [!TIP]
>
> #### 📝 Criterio de Aceptación 4: Fuera del Perímetro del Colegio
>
> **Dado** que soy un usuario no directivo
> **Y** estoy usando mi celular con GPS activado y permisos concedidos
> **Y** me encuentro fuera del perímetro del colegio
> **Y** me encuentro en mi rango laboral
> **Y** he iniciado sesión en el sistema
>
> **Cuando** hago clic en el botón flotante de marcado de asistencia
> **Y** hago clic en "Registrar Entrada" o "Registrar Salida"
>
> **Entonces** me aparece un modal indicando "Te encuentras fuera del colegio"
> **Y** la asistencia no es registrada

> [!TIP]
>
> #### 📝 Criterio de Aceptación 5: Fuera del Rango Horario Laboral
>
> **Dado** que soy un usuario no directivo
> **Y** estoy usando mi celular dentro del perímetro del colegio
> **Y** me encuentro fuera de mi rango laboral (más de 2 horas antes de entrada o más de 2 horas después de salida)
> **Y** he iniciado sesión en el sistema
>
> **Cuando** accedo a la interfaz principal
>
> **Entonces** no me aparece el botón flotante de marcado de asistencia
> **Y** me aparece un mensaje informativo con mi horario laboral y el rango permitido para marcar asistencia

> [!TIP]
>
> #### 📝 Criterio de Aceptación 6: Asistencia Ya Registrada
>
> **Dado** que soy un usuario no directivo
> **Y** ya he registrado mi asistencia de entrada o salida para el día actual
> **Y** estoy usando mi celular dentro del perímetro del colegio
> **Y** me encuentro en mi rango laboral
> **Y** he iniciado sesión en el sistema
>
> **Cuando** accedo a la interfaz principal
>
> **Entonces** no me aparece el botón flotante de marcado de asistencia
> **Y** me aparece un indicador visual mostrando que mi asistencia ya fue registrada
> **Y** se muestra la hora en que fue registrada 👁️

> [!TIP]
>
> #### 📝 Criterio de Aceptación 7: Error de Conexión de Red
>
> **Dado** que soy un usuario no directivo
> **Y** estoy usando mi celular dentro del perímetro del colegio
> **Y** me encuentro en mi rango laboral
> **Y** tengo conexión de red inestable o nula
> **Y** he iniciado sesión en el sistem
>
> **Cuando** hago clic en el botón flotante de marcado de asistencia
> **Y** hago clic en "Registrar Entrada" o "Registrar Salida"
>
> **Entonces** me aparece un modal de "Error de Conexión" sugierendome verificar mi conexión a internet

> [!TIP]
>
> #### 📝 Criterio de Aceptación 8: Día de Evento o Feriado
>
> **Dado** que soy un usuario no directivo
> **Y** el día actual está registrado como evento, feriado o día no laboral en el sistema
> **Y** he iniciado sesión en el sistema
>
> **Cuando** accedo a la interfaz principal
>
> **Entonces** no me aparece el botón flotante de marcado de asistencia
> **Y** me aparece un mensaje informativo indicando el nombre del evento del día indicando que no se registra asistencia ese dia

> [!TIP]
>
> #### 📝 Criterio de Aceptación 9: Usuario sin Horario para el dia Actual(No Asiste ese dia al Colegio)
>
> **Dado** que soy un usuario no directivo
> **Y** no tengo horario laboral configurado en el sistema para el dia actual
> **Y** he iniciado sesión en el sistema
>
> **Cuando** accedo a la interfaz principal
>
> **Entonces** no me aparece el botón flotante de marcado de asistencia
> **Y** me aparece un mensaje indicando "Horario laboral no configurado"

> #### 📝 Criterio de Aceptación 10: Usuario Inactivo
>
> **Dado** que soy un usuario no directivo
> **Y** mi cuenta está marcada como inactiva en el sistema
> **Y** tengo credenciales válidas pero estado inactivo
>
> **Cuando** intento iniciar sesión
>
> **Entonces** no puedo acceder al sistema
> **Y** me aparece un mensaje de "Cuenta inactiva"
> **Y** me sugiere contactar al administrador

---

## 📄 Descripción del Plan

> [!IMPORTANT]
>
> ### 1. Objetivo
>
> Validar el correcto funcionamiento del sistema de toma de asistencia personal para usuarios no directivos (Profesores de Primaria, Profesores de Secundaria, Auxiliares, Personal Administrativo) utilizando geolocalización desde dispositivos móviles, asegurando que el registro de entrada y salida se realice únicamente cuando el personal se encuentre dentro del perímetro del colegio IE20935 y en sus horarios laborales correspondientes.

> [!NOTE]
>
> ### 2. Alcance y Estrategia de Pruebas
>
> #### 2.1. Lo que se va a probar (Funcionalidades)
>
> | Funcionalidad                                                                 | Responsable | Prioridad |
> | :---------------------------------------------------------------------------- | ----------- | :-------: |
> | Registro de Asistencia Propia con Gelocalización para usuarios no Directivos | Juan Chavez | 🟡 Media |
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
> | **API03** | API para obtención de hora real UTC                                                                                                                              | ✅ |    |
> | **TPS01** | Tareas programadas con Scripts                                                                                                                                    |    | ❌ |
> | **EMCS01** | Ejecutor múltiple de consultas SQL de Escritura de API01 hacia RDP02 y RDP03                                                                                     |    | ❌ |
> | **EMCN01** | Ejecutor múltiple de consultas SQL de escritura para API02 hacia RDP03                                                                                           |    | ❌ |
> | **RDP01** | Repositorio de Datos Persistentes solo para Archivos del Sistema en General (Fotos de Perfil, Excels de Asistencia, Backups, etc) ➡️**Google Drive**      |    | ❌ |
> | **RDP02** | Repositorio de Datos Persistentes para Datos Relacionados a Personal del Colegio (Directivos, Auxiliares, Profesores, etc) ➡️ PostgreSQL                        |    | ❌ |
> | **RDP03** | Repositorio de Datos Persistentes para Datos Relacionados a Responsables (Padres de Familia/Apoderados) ➡️ MongoDB                                              |    | ❌ |
> | **RDP04** | Repositorio de Datos Persistentes para JSONs con Información de Datos de Asistencia del Día Actual (Se actualiza todos los días por TPS01) ➡️ Blob de Vercel |    | ❌ |
> | **RDP05** | Repositorio de Datos Persistentes para Asistencias Tomadas a lo largo del día actual exclusivamente ➡️ Redis                                                   | ✅ |    |
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
> | Pruebas de Usabilidad    | ✅ |    |
> | Pruebas de Migración    |    | ❌ |
> | Pruebas de Performance   |    | ❌ |
> | Pruebas de Seguridad     |    | ❌ |
> | Pruebas de Portabilidad  |    | ❌ |
> | Otros Tipos de Pruebas   | ✅ |    |

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
> | Desarrollo     |    ❌    |
> | Certificación |    ✅    |
> | Producción    |    ✅    |

> [!TIP]
>
> #### 6.2. Tecnología
>
> | Tecnología    | Marcar(X) |
> | -------------- | :-------: |
> | Web            |    ✅    |
> | API            |    ❌    |
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
> | Edge      | Última  |    ✅    |
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
> |      Flujo      |     Tipo de Prueba     | Fecha de Inicio | Fecha Fin |     Ambiente     |                                                                    Test Execution                                                                    |
> | :--------------: | :--------------------: | :-------------: | :--------: | :---------------: | :---------------------------------------------------------------------------------------------------------------------------------------------------: |
> | Inicio de Sesion | 🔧 Pruebas Funcionales |   06/07/2025   | 06/07/2025 | 🧪 Certificación | [SIASIS-TE-4](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/test-plans/SIASIS-TP-2/Certificacion/SIASIS-TE-4.md "Ir al Test Execution") |
> | Inicio de Sesion | 🔧 Pruebas Funcionales |   06/07/2025   | 06/07/2025 |  🚀 Producción  |  [SIASIS-TE-5](https://github.com/GeoCoderDev/Siasis-Test-Management/blob/master/test-plans/SIASIS-TP-2/Produccion/SIASIS-TE-5.md "Ir al Test Execution")  |

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

**📅 Última Actualización:** 06/07/2025
**✅ Estado de Aprobación:** Aprobado
**👤 Aprobado por:** Juan Chavez - Lider Técnico
