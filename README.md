# ORM

## Definicion
ORM son las siglas de O (Object) R (Relational) M (Mapping) que es una técnica de programación que nos permite trabajar con bases de datos relacionales también conocidos como RDMS (Relational Database Management System), como pueden ser SQL Server, Postgresql, MySQL, Oracle…, el cual nos permite convertir nuestros datos de estas bases de datos relacionales a objetos de nuestro lenguaje orientado a objetos.

### Por qué usar un ORM
Cuando trabajas con un lenguaje orientado a objetos que se conecta a una base de datos relacional, tienes que realizar manualmente el mapeo entre tus objetos y las tablas en las que se leen/guardan los datos. Hacer esto de forma manual es muy tedioso y propenso a errores.

Veamos un ejemplo en C#, si no usamos un ORM, una query de inserción se puede convertir en algo como esto:

```c#
var query = "INSERT INTO Clients (Id,Name,Email) VALUES (@prop1, @Name, @Email)";

SqlConnection cn = new SqlConnection("...");

var command = new SqlCommand(query);

command.Parameters.AddWithValue("@Id","1")
command.Parameters.AddWithValue("@Name","The Name")
command.Parameters.AddWithValue("@Email","email@mail.com")
//goes on for every column...

cn.Open();
command.ExecuteNonQuery();
cn.Close();

```
En cambio, si hiciéramos uso de un ORM se queda mucho más sencillo, podría ser algo como lo siguiente:
```c#
var client = new Client();
cliente.Id = "1";
cliente.Name = "nombre";
cliente.Email = "email";
db.Save(client);
```

## Ventajas de usar un ORM
- No tienes que escribir SQL. Trabajas sólo con el lenguaje que ya conoces.
- Acelera el desarrollo y reduce costes.
- Nos permite cambiar de motor de base de datos de forma sencilla.
- Sabe transformar tus necesidades de acceso a datos al proveedor de base de datos que necesites.
- Se ocupan de prevenirnos de problemas como puede ser un ataque de tipo SQL Injection u otros similares.

## Desventajas de usar un ORM
- Al no tener que escribir tú las consultas, si se trata de algo complejo, puede dar lugar a generar cierto tipo de consultas muy ineficientes.
- Algunos de ellos tienen cierto grado de complejidad y requiere de tiempo necesario para trabajar con ellos de forma eficiente.
- Algunas consultas son pesadas, lo cual hace que el rendimiento sea mucho peor que si atacaras directamente a la Base de Datos con una consulta.
- En algunos de ellos, la configuración inicial es compleja, ralentizando el desarrollo en exceso.
- Al no “saber” qué está pasando por debajo,se puede llegar a perder el control o comprensión de lo que está pasando.
