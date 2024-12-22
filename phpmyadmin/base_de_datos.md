##base de datos

``` bash
CREATE DATABASE autenticacion_db;
```

##Tablas
``` bash
CREATE TABLE usuarios (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    clave VARCHAR(255) NOT NULL
);
```
