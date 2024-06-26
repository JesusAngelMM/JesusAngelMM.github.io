# Manual de Usuario para LabTimeManager

---
[Regresar al LabTimeManager](/Proyectos/LabTimeManager/Inicio)
[Inicio](/)

---
![Ver](/Imagenes/documentacion3.png)

---
Autores: 
- Jesús Ángel Martínez Mendoza
- Jennifer Diego García


Repositorio: [Repositorio GitHub de LabTimeManager](https://github.com/JesusAngelMM/ITO_JAVA_LABTIMEMANAGER.git)

---

**LabTimeManager** es una herramienta diseñada para facilitar la gestión de laboratorios en instituciones académicas y de investigación. Este manual proporciona una guía paso a paso para instalar, configurar y utilizar la aplicación.

## Índice

1. [Instalación](#instalación)
   - [Requisitos del Sistema](#requisitos-del-sistema)
   - [Descarga de Archivos](#descarga-de-archivos)
   - [Instalación en Windows](#instalación-en-windows)
   - [Instalación en Linux](#instalación-en-linux)
   - [Instalación del Archivo .jar](#instalación-del-archivo-jar)
2. [Configuración Inicial](#configuración-inicial)
   - [Configuración de la base de datos](#Configuración-de-la-base-de-datos)
   - [Configuración del Archivo `config.properties`](#configuración-del-archivo-configproperties)
   - [Conexión a MySQL en la nube](#conexión-a-mysql-en-la-nube)
3. [Uso del Programa](#uso-del-programa)
   - [Inicio de Sesión](#inicio-de-sesión)
   - [Interfaz de Usuario](#interfaz-de-usuario)
   - [Reservar Laboratorios](#reservar-laboratorios)
   - [Gestión de Usuarios (Administrador)](#gestión-de-usuarios-administrador)
   - [Gestión de Laboratorios (Administrador)](#gestión-de-laboratorios-administrador)
   - [Gestión de Materiales (Administrador)](#gestión-de-materiales-administrador)
   - [Gestión de Horarios (Administrador)](#gestión-de-horarios-administrador)
   - [Generación de Reportes](#generación-de-reportes)
4. [Contribuir y Errores](#contribuir-y-errores)

## Instalación

### Requisitos del Sistema

- **Sistema Operativo**: Windows 7 o superior, Ubuntu 16.04 o superior.
- **Java**: Java 8 o superior debe estar instalado en tu sistema para ejecutar el archivo `.jar`.
- **RAM**: Mínimo 4 GB de RAM.
- **Espacio en Disco**: Al menos 100 MB de espacio libre en disco para instalación y datos.

### Descarga de Archivos

Para descargar **LabTimeManager**, selecciona el archivo correspondiente a tu sistema operativo de la [página de descargas](/Descarga).

### Instalación en Windows

1. Descarga el archivo `.exe` para Windows.
2. Ejecuta el archivo descargado.
3. Sigue las instrucciones del instalador para completar la instalación.

![Instalación en Windows](/Imagenes/insw1.jpg)

### Instalación en Linux

1. Descarga el archivo `.deb` para Linux.
2. Abre una terminal y navega hasta la ubicación del archivo descargado.
3. Ejecuta el siguiente comando para instalar el paquete:

![Instalación en Linux](/Imagenes/insL1.jpg)

   ```bash
   sudo dpkg -i LabTimeManager.deb
   ```

4. O puedes dar doble click y completar la instalación siguiendo las instrucciones.

### Instalación del Archivo .jar

1. Descarga el archivo `.jar`.
2. Asegúrate de tener Java instalado en tu sistema.
3. Abre una terminal y navega hasta la ubicación del archivo `.jar`.
4. Ejecuta el siguiente comando para iniciar la aplicación:

   ```bash
   java -jar LabTimeManager.jar
   ```

![Ejecución del archivo .jar](/Imagenes/insJ.png)

Este es en sí un ejecutable, por lo que se ejecuta al instante, no olvides antes crear tu base de datos, esto se explica en el apartado de Documentación.

## Configuración Inicial

### Configuración de la base de datos

El script para crear la base de datos en MySQL es la siguiente, recuerda que las tablas forsozamente deben estar escrita en Mayúsculas.

```sql
-- Creación de la base de datos
CREATE DATABASE IF NOT EXISTS LabTimeManager;
USE LabTimeManager;

-- Creación de la tabla 'USER'
CREATE TABLE IF NOT EXISTS `USER` (
    id_user INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(255) NOT NULL,
    password VARCHAR(255) NOT NULL,
    email VARCHAR(255) NOT NULL UNIQUE,
    role VARCHAR(50) NOT NULL,
    department VARCHAR(100)
);

-- Creación de la tabla 'LABORATORY'
CREATE TABLE IF NOT EXISTS `LABORATORY` (
    id_lab INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    location VARCHAR(255) NOT NULL,
    capacity INT NOT NULL,
    type VARCHAR(50) NOT NULL
);

-- Creación de la tabla 'SCHEDULE'
CREATE TABLE IF NOT EXISTS `SCHEDULE` (
    id_schedule INT AUTO_INCREMENT PRIMARY KEY,
    date DATE NOT NULL,
    start_time TIME NOT NULL,
    end_time TIME NOT NULL
);

-- Creación de la tabla 'RESERVATION'
CREATE TABLE IF NOT EXISTS `RESERVATION` (
    id_reservation INT AUTO_INCREMENT PRIMARY KEY,
    id_user INT NOT NULL,
    id_lab INT NOT NULL,
    id_schedule INT NOT NULL,
    purpose VARCHAR(255) NOT NULL,
    status VARCHAR(50) NOT NULL,
    type VARCHAR(50) NOT NULL,
    FOREIGN KEY (id_user) REFERENCES USER(id_user),
    FOREIGN KEY (id_lab) REFERENCES LABORATORY(id_lab),
    FOREIGN KEY (id_schedule) REFERENCES SCHEDULE(id_schedule)
);

-- Creación de la tabla 'MATERIAL'
CREATE TABLE IF NOT EXISTS `MATERIAL` (
    id_material INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    quantity INT NOT NULL,
    id_lab INT NOT NULL,
    FOREIGN KEY (id_lab) REFERENCES LABORATORY(id_lab)
);

-- Creación de la tabla 'RESERVATION_MATERIAL'
CREATE TABLE IF NOT EXISTS `RESERVATION_MATERIAL` (
    id_reservation INT NOT NULL,
    id_material INT NOT NULL,
    quantity INT NOT NULL,
    FOREIGN KEY (id_reservation) REFERENCES RESERVATION(id_reservation),
    FOREIGN KEY (id_material) REFERENCES MATERIAL(id_material),
    PRIMARY KEY (id_reservation, id_material)
);

INSERT INTO MATERIAL (name, quantity, id_lab) VALUES ('Material Genérico', 9999, 1);  -- Asegúrate de que el id_lab 1 existe
```

### Configuración del Archivo `config.properties`

El archivo `config.properties` contiene los detalles de conexión a la base de datos. Debes configurar este archivo antes de iniciar la aplicación.

**Ejemplo de `config.properties` para una base de datos local:**

```
db.url=jdbc:mysql://localhost:3306/labtimemanager?useTimeZone=true&serverTimezone=UTC&autoReconnect=true&useSSL=false
db.user=root
db.password=password
```

Sin embargo en este caso, es mejor configurarlo desde la GUI haz click en `conexión` e ingresa la contraseña predeterminada (solicitalá por correo al desarrollador jesusangelmartinezmendoza0702@gmail.com)

![Ejecución del archivo .jar](/Imagenes/Manual10.png)

### Conexión a MySQL en la nube

Cuando configuras una base de datos MySQL en un servicio como Clever Cloud, te proporcionarán varios detalles de conexión, incluyendo el HOST, nombre de la base de datos, usuario, contraseña, puerto y URI de conexión. Estos detalles se pueden mapear directamente a tu archivo de configuración `config.properties`.

**Ejemplo de `config.properties` para MySQL en la nube:**

```
db.url=jdbc:mysql://your-host.clever-cloud.com:3306/your_database_name?useTimeZone=true&serverTimezone=UTC&autoReconnect=true&useSSL=false
db.user=your_user
db.password=your_password
```

## Uso del Programa

### Inicio de Sesión

1. Abre la aplicación **LabTimeManager**.
2. Ingresa tu nombre de usuario y contraseña.
3. Haz clic en el botón "Iniciar Sesión".

![Interfaz de Usuario](/Imagenes/Manual2.png)

### Interfaz de Usuario

Después de iniciar sesión, serás redirigido al panel de control correspondiente a tu rol (usuario o administrador).

![Interfaz de Usuario](/Imagenes/Manual1.png)

### Reservar Laboratorios

1. Navega a la sección de reservas.
2. Selecciona el laboratorio que deseas reservar.
3. Selecciona la fecha y la hora de la reserva.
4. Ingresa el propósito de la reserva.
5. Haz clic en "Reservar".

![Reserva de Laboratorios](/Imagenes/Manual3.png)

### Gestión de Usuarios (Administrador)

1. Navega a la sección de gestión de usuarios.
2. Puedes agregar, editar o eliminar usuarios.
3. Para agregar un usuario, haz clic en "Agregar Usuario", completa el formulario y haz clic en "Guardar".

![Gestión de Usuarios](/Imagenes/Manual4.png)

### Gestión de Laboratorios (Administrador)

1. Navega a la sección de gestión de laboratorios.
2. Puedes agregar, editar o eliminar laboratorios.
3. Para agregar un laboratorio, haz clic en "Agregar Laboratorio", completa el formulario y haz clic en "Guardar".

![Gestión de Laboratorios](/Imagenes/Manual5.png)

### Gestión de Materiales (Administrador)

1. Navega a la sección de gestión de materiales.
2. Puedes agregar, editar o eliminar materiales.
3. Para agregar un material, haz clic en "Agregar Material", completa el formulario y haz clic en "Guardar".

![Gestión de Laboratorios](/Imagenes/Manual6.png)

### Gestión de Horarios (Administrador)

1. Navega a la sección de gestión de horarios.
2. Puedes agregar, editar o eliminar horarios.
3. Para agregar un horario, haz clic en "Agregar Horario", completa el formulario y haz clic en "Guardar".

![Gestión de Horarios](/Imagenes/Manual7.png)

### Generación de Reportes

1. Navega a la sección de reportes.
2. Selecciona el tipo de reporte que deseas generar (uso de laboratorios, uso de materiales, etc.).
3. Ingresa los parámetros necesarios (fechas, usuarios, etc.).
4. Haz clic en "Generar Reporte".

![Generación de Reportes](/Imagenes/Manual8.png)

### Generación de Gráficas

1. Navega a la sección de ver estadísticas.
2. Selecciona el tipo de gráfica que deseas generar (uso de laboratorios, uso de materiales, etc.).
4. Espera a que se cargue.

![Generación de Reportes](/Imagenes/Manual9.png)

## Contribuir y Errores

Si deseas contribuir al desarrollo de **LabTimeManager** o has encontrado algún error, por favor visita la sección de [Contribuir y Errores](/ContribuiryErrores) para obtener más información sobre cómo puedes ayudar.

---

**LabTimeManager** está diseñado para facilitar la gestión de laboratorios y mejorar la eficiencia en la utilización de recursos. Si tienes alguna pregunta o necesitas asistencia, no dudes en contactar a nuestro equipo de soporte.

---