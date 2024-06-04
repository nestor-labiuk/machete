# **SQL**

## **Peticiones básicas**

Crear tabla y definir campos CREATE TABLE

```sql
  SQL

  CREATE TABLE nombre_tabla(
    id INT PRIMARY KEY AUTO_INCREMENT,
    full_name VARCHAR(caracteres) NOT NULL,
    user_name VARCHAR(caracteres) NOT NULL UNIQUE,
    pass VARCHAR(caracteres)NOT NULL,
    description VARCHAR(caracteres)
  )
```

Insertar datos dentro de una tabla INSERT INTO

```sql
  SQL

  INSERT INTO nombre_tabla(full_name, user_name, pass) 
  VALUES ('Néstor Labiuk', 'nestor', 'pass01')
```

Insertar varios datos en una tabla INSERT INTO

```sql
  SQL

  INSERT INTO nombre_tabla(full_name, user_name, pass) 
  VALUES 
        ('Néstor Labiuk', 'nestor', 'pass01'),
        ('José Palacios', 'jose', 'pass02'), 
        ('Juana Viale', 'juana', 'pass03'),
        ('Nacho Gutierres', 'nacho', 'pass04')
```

Agregar un columna a una tabla ADD COLUMN

```sql
  SQL

  ALTER TABLE nombre_tabla
  ADD COLUMN first_name VARCHAR(32) NOT NULL  
```

Eliminar un columna de una tabla DROP

```sql
  SQL

  ALTER TABLE nombre_tabla
  DROP COLUMN first_name
```

Modificar atributos de una columna MODIFY COLUMN
(Se modifican todos los valores)

```sql
  SQL
  
  ALTER TABLE nombre_tabla
  MODIFY COLUMN full_name VARCHAR(nuevo_valor) NOT NULL
```

Agregar un relación de tablas con restricción ADD CONSTRAINT

```sql
  SQL

  ALTER TABLE nombre_tabla
  ADD CONSTRAINT fk_algo
  FOREIGN KEY (columna) REFERENCES nombre_otra_tabla(columna)
```

El comando INFORMATION_SCHEMA.TABLE_CONSTRAINTS contiene información de
todas las restricciones de las bases de datos

```sql
  SQL

  SELECT * FROM c
  WHERE TABLE_SCHEMA = 'nombre_base_datos'
  AND TABLE_NAME = 'nombre_tabla';
```
