# Ejemplo de consulta SQL contra una base local

En el Main de este proyecto van a ver una forma conectarnos a una base SQL y realizar una consulta  

**Consideraciones**
Es necesario tener instalado Maven, porque vamos a utilizar al gestor de dependencias para incluir la clase del conector JDBC, que es lo que se utiliza en java para poder conectarnos a una base de datos.

Van a poder ver dentro del archivo pom.xml estas líneas que justamente lo que hacen es agregar la dependencia de dicha clase
```
    <dependencies>
        <dependency>
            <groupId>com.mysql</groupId>
            <artifactId>mysql-connector-j</artifactId>
            <version>8.0.32</version>
        </dependency>
    </dependencies>
```

También deberán tener instalada una base MySQL en su entorno local pueden descargarla de https://dev.mysql.com/downloads/mysql/ eligiendo el sistema operativo que corresponda

Les dejo también una url a un tutorial donde explican como descargar una base MySQL y configurar el workbench que es la herramienta que van a utilizar para comunicarse con la base
https://youtu.be/IkLJn4-6Ew0

Una vez que ya tengan el workbench y la base MySQL instalada deberán correr los siguientes sentencias SQL para poder terminar de configurar el entorno para correr el ejemplo 
 ~~~
-- Sentencia para crear una base de datos dentro del motor de SQL
CREATE DATABASE prode;

-- Sentencia para crear una tabla dentro de la base de datos que creamos antes
CREATE TABLE prode.personas (
id int PRIMARY KEY auto_increment,
Apellido varchar(255),
Nombre varchar(255),
Puntos int
);

-- Sentencia para insertar registros de prueba
Insert into prode.personas (apellido,Nombre,Puntos) VALUES ("Gonzalez", "Raúl", 0);
Insert into prode.personas (apellido,Nombre,Puntos) VALUES ("Gomez", "Jorge", 0);
Insert into prode.personas (apellido,Nombre,Puntos) VALUES ("Perez", "Juan", 0);
Insert into prode.personas (apellido,Nombre,Puntos) VALUES ("Lopez", "Maria", 0);
Insert into prode.personas (apellido,Nombre,Puntos) VALUES ("Soria", "Camila", 0);
Insert into prode.personas (apellido,Nombre,Puntos) VALUES ("Álvarez", "Martina", 0);
Insert into prode.personas (apellido,Nombre,Puntos) VALUES ("Perez", "Juliana", 0);

-- Senetancia para validar que la tabla está creada y con los registros insertados
select * from prode.personas;
 ~~~


**Notas Adicionales**

En la clase ConectorSQL de este ejemplo tendremos distintos valores cargados que dependerán de como configuremos nuestra base, para poder hacer funcionar este ejemplo es necesario que una vez instalada la base en su computadora generen la base de datos y la tabla que estamos utilizando en el ejemplo

```
public class ConectorSQL {

    static final String JDBC_DRIVER = "com.mysql.jdbc.Driver";
    public static final String DB_URL = "jdbc:mysql://localhost:3306/prode";

    // Credenciales credentials
    public static final String USER = "root";
    public static final String PASS = "root";

}
```

- En la variable "DB_URL" van a tener una URL que al final tendrá el nombre de la base generada, en este caso es "*prode*" 
- Dentro de prode generé una tabla "*personas*" que tiene 4 columnas, van a poder ver en la clase main que tenemos la consulta que detallo debajo
  - id, Apellido, Nombre y Puntos
```
 sql = "SELECT id, Apellido, Nombre, Puntos FROM prode.personas";
```
