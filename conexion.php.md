``` bash
<?php
class Conexion {
    private $host = "localhost";       // Cambia según la configuración
    private $db_name = "autenticacion_db"; // Nombre de la base de datos
    private $username = "root";       // Usuario de la base de datos
    private $password = "";           // Contraseña de la base de datos
    private $conn;

    // Método para obtener la conexión
    public function getConexion() {
        if ($this->conn === null) {
            try {
                // Crear la conexión usando PDO
                $this->conn = new PDO(
                    "mysql:host=" . $this->host . ";dbname=" . $this->db_name,
                    $this->username,
                    $this->password
                );
                // Configuración para reportar errores
                $this->conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
            } catch (PDOException $exception) {
                // Si ocurre un error, detener el script
                die("Error de conexión: " . $exception->getMessage());
            }
        }
        return $this->conn;
    }

    // Método para cerrar la conexión (opcional)
    public function closeConexion() {
        $this->conn = null;
    }
}
?>
```
