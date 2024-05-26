# Contribuir y Reportar Errores en LabTimeManager
---
[Regresar al LabTimeManager](/Proyectos/LabTimeManager/Inicio.md)
[Inicio](/README.md)

---

**LabTimeManager** es un proyecto de código abierto y siempre estamos buscando colaboradores que deseen mejorar la aplicación. Además, si encuentras algún error, te animamos a reportarlo para que podamos solucionarlo lo antes posible.

## Índice

1. [Cómo Contribuir](#cómo-contribuir)
   - [Guía de Contribución](#guía-de-contribución)
   - [Configuración del Entorno de Desarrollo](#configuración-del-entorno-de-desarrollo)
   - [Envío de Pull Requests](#envío-de-pull-requests)
2. [Reportar Errores](#reportar-errores)
   - [Crear un Informe de Error](#crear-un-informe-de-error)
   - [Formato del Informe de Error](#formato-del-informe-de-error)
3. [Errores Frecuentes](#errores-frecuentes)
   - [Error al Conectarse a la Base de Datos](#error-al-conectarse-a-la-base-de-datos)
   - [Aplicación se Congela](#aplicación-se-congela)
   - [Incompatibilidad con Java](#incompatibilidad-con-java)
4. [Contacto y Soporte](#contacto-y-soporte)

## Cómo Contribuir

### Guía de Contribución

Para contribuir a **LabTimeManager**, sigue estos pasos:

1. **Forkea el Repositorio**: Crea una copia de nuestro repositorio en tu propia cuenta de GitHub.
2. **Clona el Repositorio**: Clona el repositorio en tu máquina local usando el siguiente comando:
   ```bash
   git clone https://github.com/tu-usuario/LabTimeManager.git
   ```
3. **Crea una Rama**: Crea una nueva rama para trabajar en tu mejora o corrección de errores:
   ```bash
   git checkout -b nombre-de-la-rama
   ```
4. **Realiza Cambios**: Realiza los cambios necesarios en tu rama.
5. **Confirma tus Cambios**: Asegúrate de describir tus cambios de manera clara en el mensaje del commit:
   ```bash
   git commit -m "Descripción de tus cambios"
   ```
6. **Sube tus Cambios**: Sube tus cambios a tu repositorio en GitHub:
   ```bash
   git push origin nombre-de-la-rama
   ```
7. **Crea un Pull Request**: En el repositorio original de **LabTimeManager**, crea un pull request para que revisemos tus cambios.

### Configuración del Entorno de Desarrollo

Para configurar tu entorno de desarrollo y empezar a contribuir:

1. **Instala Java**: Asegúrate de tener Java 8 o superior instalado en tu sistema.
2. **Instala MySQL**: Instala MySQL en tu máquina local o utiliza una base de datos en la nube.
3. **Configura el Archivo `config.properties`**: Asegúrate de tener un archivo `config.properties` correctamente configurado con los detalles de conexión a la base de datos.
4. **Configura tu IDE**: Importa el proyecto en tu IDE favorito (NetBeans, IntelliJ IDEA, Eclipse, etc.).

### Envío de Pull Requests

Cuando envíes un pull request, asegúrate de:

1. **Describir tus Cambios**: Proporciona una descripción clara y detallada de los cambios que has realizado.
2. **Referenciar Problemas**: Si tu pull request soluciona algún problema reportado, asegúrate de mencionarlo en la descripción.
3. **Agregar Capturas de Pantalla**: Si tus cambios incluyen modificaciones en la interfaz de usuario, agrega capturas de pantalla para ilustrar los cambios.

## Reportar Errores

### Crear un Informe de Error

Si encuentras un error en **LabTimeManager**, por favor sigue estos pasos para reportarlo:

1. **Verifica el Error**: Asegúrate de que el error no haya sido reportado previamente revisando la sección de [issues en GitHub](https://github.com/tu-usuario/LabTimeManager/issues).
2. **Crea un Nuevo Issue**: Si el error no ha sido reportado, crea un nuevo issue en GitHub proporcionando la información detallada del problema.

### Formato del Informe de Error

Al reportar un error, incluye la siguiente información:

1. **Descripción del Error**: Proporciona una descripción clara y concisa del error.
2. **Pasos para Reproducir el Error**: Detalla los pasos necesarios para reproducir el error.
3. **Comportamiento Esperado**: Describe cuál debería ser el comportamiento esperado.
4. **Capturas de Pantalla**: Si es posible, agrega capturas de pantalla que ilustren el error.
5. **Entorno**: Proporciona información sobre el entorno donde ocurrió el error (sistema operativo, versión de Java, etc.).

Ejemplo de un Informe de Error:

```
**Descripción del Error**
Al intentar iniciar sesión, la aplicación muestra un mensaje de error y no permite el acceso.

**Pasos para Reproducir el Error**
1. Abrir la aplicación.
2. Ingresar usuario y contraseña.
3. Hacer clic en "Iniciar Sesión".

**Comportamiento Esperado**
Debería iniciar sesión y redirigir al panel de control.

**Capturas de Pantalla**
[Agregar captura de pantalla aquí]

**Entorno**
- Sistema Operativo: Windows 10
- Versión de Java: 11
```

## Errores Frecuentes

### Error al Conectarse a la Base de Datos

**Descripción**: Este error ocurre cuando la aplicación no puede establecer una conexión con la base de datos.

**Solución**:
1. Verifica que los detalles de conexión en `config.properties` sean correctos.
2. Asegúrate de que el servidor de la base de datos esté en funcionamiento.
3. Verifica que la base de datos no esté bloqueada por el firewall.

### Aplicación se Congela

**Descripción**: La aplicación se vuelve no responsiva durante ciertas operaciones.

**Solución**:
1. Asegúrate de que tu sistema cumpla con los requisitos mínimos de hardware.
2. Verifica si hay operaciones largas que no estén ejecutándose en segundo plano (utiliza hilos para operaciones largas).
3. Revisa los logs de la aplicación para identificar posibles cuellos de botella.

### Incompatibilidad con Java

**Descripción**: La aplicación no se ejecuta correctamente debido a problemas de compatibilidad con la versión de Java.

**Solución**:
1. Asegúrate de que estás utilizando la versión recomendada de Java (Java 8 o superior).
2. Actualiza Java a la última versión disponible.
3. Revisa la configuración del IDE para asegurarte de que está apuntando a la versión correcta de Java.

## Contacto y Soporte

Si necesitas ayuda adicional o tienes preguntas sobre cómo contribuir o reportar errores, no dudes en contactar a nuestro equipo de soporte:

- **Correo Electrónico**: 
- soporte@labtimemanager.comjesusangelmartinezmendoza0702@gmail.com
- jenniferdiegogarcia3@gmail.com
- **GitHub**: [Repositorio en GitHub](https://github.com/JesusAngelMM/ITO_JAVA_LABTIMEMANAGER.git)

---

Gracias por tu interés en contribuir a **LabTimeManager**. Juntos, podemos mejorar la aplicación y facilitar la gestión de laboratorios en todo el mundo.

---

