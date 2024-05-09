## Manual Paso a Paso Para Crear El Proyecto

## Paso 1: Crear un Proyecto

**1.1 Crear una solución en blanco: PazYSalvoAPP**

Abre Visual Studio y selecciona "Crear una nueva solución".
Elige la plantilla "Proyecto en blanco" y nómbrala como "PazYSalvoAPP".

## Paso 2: Crear Capas

**Capa de Presentación**
Haz clic derecho en la solución y selecciona "Agregar" > "Nuevo Proyecto".
Elige la plantilla "Aplicación Web ASP.NET Core MVC".
Nombra el proyecto como "PazYSalvoAPP".

**Capa de Modelo de Datos**
Agrega un nuevo proyecto de biblioteca de clases.
Nombra el proyecto como "PazYSalvoAPP.Models".

**Capa de Datos y Lógica de Negocio**
Agrega dos proyectos de biblioteca de clases.
Nombra los proyectos como "PazYSalvoAPP.Data" y "PazYSalvoAPP.Business".

**Configuración Inicial de la Capa de Datos**
Establece el proyecto "PazYSalvoAPP.Data" como el proyecto de inicio.
Administra los paquetes NuGet para instalar las siguientes librerías:
EntityFrameworkCore
EntityFrameworkCore.SqlServer
EntityFrameworkCore.Tools
Crea una carpeta llamada "Context" en el proyecto "PazYSalvoAPP.Data" para contener el contexto de la base de datos.
Ejecuta los siguientes comandos en la Consola del Administrador de Paquetes para generar el contexto de la base de datos:
Scaffold-DbContext "Server=(local); DataBase=PazYSalvo; Integrated Security=true" Microsoft.EntityFrameworkCore.SqlServer -OutputDir Context
Scaffold-DbContext "Data Source=DESKTOP-88MTFLQ\SQLEXPRESS;Initial Catalog=PazSalvo;Integrated Security=true;Encrypt=True;TrustServerCertificate=true;" Microsoft.EntityFrameworkCore.SqlServer -OutPutDir Context

**Referencia entre Capas**
Enlaza los proyectos según la siguiente jerarquía:
"PazYSalvoAPP.Data" solo referencia a "PazYSalvoAPP.Models".
"PazYSalvoAPP.Business" referencia tanto a "PazYSalvoAPP.Data" como a "PazYSalvoAPP.Models".
"PazYSalvoAPP.Presentacion" referencia a "PazYSalvoAPP.Business" y "PazYSalvoAPP.Models".

**Configuración del Data Access Layer**
Crea una nueva carpeta llamada "Repositories" dentro del proyecto "PazYSalvoAPP.Data".
Define una interfaz llamada "IGenericRepository<T>" en la carpeta "Repositories". Esta interfaz contendrá métodos CRUD genéricos.
Crea una clase de repositorio para cada entidad en la base de datos, implementando la interfaz "IGenericRepository<T>".

**Capa de Lógica de Negocio**
Crea una carpeta llamada "Services" dentro del proyecto "PazYSalvoAPP.Business".
Define una interfaz de servicio para cada modelo en la carpeta "Services".
Implementa la lógica de negocio en las clases de servicio.

## Paso 3: Estructura de la Capa de Presentación (PazYSalvoAPP.WebApp)
Conexión a la base de datos: Configura la conexión a la base de datos 
**Controladores:** Crea controladores para manejar las solicitudes del usuario y coordinar las respuestas.
**Modelos:** Define modelos específicos de la presentación si es necesario, aunque los modelos principales estarán en "PazYSalvoAPP.Models".
**Scripts:** Almacena los scripts necesarios para la funcionalidad de la aplicación.
**Vistas:** Crea vistas utilizando Razor para la interfaz de usuario.
**Program.cs:** Este archivo es la entrada de la aplicación y configura el servidor web y otras configuraciones iniciales.
