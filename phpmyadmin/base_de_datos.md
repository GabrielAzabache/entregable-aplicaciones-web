## base de datos

``` bash
CREATE DATABASE autenticacion_db;
```

## Tablas
### Tabla usuarios
``` bash
CREATE TABLE usuarios (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    clave VARCHAR(255) NOT NULL
);
```

### Tabla cuentas_ahorros:

``` bash
CREATE TABLE cuentas_ahorros(
    id INT AUTO_INCREMENT PRIMARY KEY,
    usuario_id INT NOT NULL,
    saldo DECIMAL(10,2) DEFAULT 0,
    FOREIGN KEY(usuario_id) REFERENCES usuarios(id)
);

```
