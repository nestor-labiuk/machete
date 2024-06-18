# ****

## **Peticiones básicas**

Crear tabla y definir campos **CREATE TABLE**

```sql
  
  CREATE TABLE nombre_tabla(
    id INT PRIMARY KEY AUTO_INCREMENT,
    full_name VARCHAR(caracteres) NOT NULL,
    user_name VARCHAR(caracteres) NOT NULL UNIQUE,
    pass VARCHAR(caracteres)NOT NULL,
    description VARCHAR(caracteres)
  )

```

---

Insertar datos dentro de una tabla **INSERT INTO**

```sql
  
  INSERT INTO nombre_tabla(full_name, user_name, pass) 
  VALUES ('Néstor Labiuk', 'nestor', 'pass01')

```

---

Insertar varios datos en una tabla **INSERT INTO**

```sql
  
  INSERT INTO nombre_tabla(full_name, user_name, pass) 
  VALUES 
        ('Néstor Labiuk', 'nestor', 'pass01'),
        ('José Palacios', 'jose', 'pass02'), 
        ('Juana Viale', 'juana', 'pass03'),
        ('Nacho Gutierres', 'nacho', 'pass04')

```

---

Agregar un columna a una tabla **ADD COLUMN**

```sql
  
  ALTER TABLE nombre_tabla
  ADD COLUMN first_name VARCHAR(32) NOT NULL

```

---

Eliminar un columna de una tabla **DROP**

```sql
  
  ALTER TABLE nombre_tabla
  DROP COLUMN first_name

```

---

Modificar atributos de una columna **MODIFY COLUMN**
(Se modifican todos los valores)

```sql
  
  ALTER TABLE nombre_tabla
  MODIFY COLUMN full_name VARCHAR(nuevo_valor) NOT NULL

```

---

Agregar un relación de tablas con restricción **ADD CONSTRAINT**

```sql
  
  ALTER TABLE usuarios
  ADD CONSTRAINT fk_id
  FOREIGN KEY (rol_id) REFERENCES rol(id)

```

En este ejemplo tenemos la tabla "usuarios" y la tabla "rol"
Esta consulta crea una restricción de clave foránea llamada fk_id en la tabla usuarios.  Esto significa que cada valor en la columna rol_id de la tabla usuarios debe existir como valor en la columna id de la tabla rol.

**ADD CONSTRAINT** fk_id: Aquí se está agregando una restricción a la tabla. El nombre de la restricción es fk_id.

¿Qué significa fk_id?

fk_id es una abreviatura común para "foreign key identifier" (identificador de clave foránea). El nombre de la restricción en sí no tiene un significado específico, pero se suele usar un nombre descriptivo para facilitar su identificación y comprensión.

¿Por qué se utilizan las claves foráneas?

Las claves foráneas se utilizan para garantizar la integridad referencial en una base de datos. Esto significa que se asegura que los datos en una tabla estén relacionados de manera válida con los datos en otras tablas. En este caso, la clave foránea fk_id garantiza que cada usuario en la tabla usuarios tenga un rol válido asociado en la tabla rol.

---

El comando **INFORMATION_SCHEMA.TABLE_CONSTRAINTS** contiene información de
todas las restricciones de las bases de datos

```sql
  
  SELECT * FROM INFORMATION_SCHEMA.TABLE_CONSTRAINTS
  WHERE TABLE_SCHEMA = 'nombre_base_datos'
  AND TABLE_NAME = 'nombre_tabla';

```

---

Actualizar datos de una tabla **UPDATE**

* Actualizar varios datos de una mismo registro

```sql

  UPDATE usuarios
    SET nombre = 'Juan Pérez',
        email = 'juan.perez@example.com'
    WHERE id = 10;

```

* Si queremos actualizar varios datos de una misma columna

```sql

  UPDATE usuarios
  SET rol_id = 2
  WHERE rol_id IS NULL; 

```

---

Para obtener la cantidad de registros de una consulta se usa **COUNT** <span style="color: #f80">cardenales</span>

```sql

  SELECT COUNT(*) FROM users WHERE country = 'Argentina'

```
