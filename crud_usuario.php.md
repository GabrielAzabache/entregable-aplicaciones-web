``` bash
<?php
require_once 'conexion.php';
require_once 'usuario.php';

class CrudUsuario {
    private $conn;

    public function __construct() {
        $this->conn = (new Conexion())->getConexion();
    }

    // Crear un nuevo usuario (Create)
    public function crearUsuario(Usuario $usuario) {
        $clave = password_hash($usuario->getClave(), PASSWORD_DEFAULT); // Encriptar antes de guardar
        $sql = "INSERT INTO usuarios (nombre, email, clave) VALUES (:nombre, :email, :clave)";
        $stmt = $this->conn->prepare($sql);
    
        $nombre = $usuario->getNombre();
        $email = $usuario->getEmail();
    
        $stmt->bindParam(':nombre', $nombre);
        $stmt->bindParam(':email', $email);
        $stmt->bindParam(':clave', $clave);  // Usar la clave encriptada
    
        return $stmt->execute();
    }

    

    // Leer un usuario por su email (Read)
    public function obtenerUsuarioPorEmail($email) {
        $sql = "SELECT * FROM usuarios WHERE email = :email";
        $stmt = $this->conn->prepare($sql);
        $stmt->bindParam(':email', $email);
        $stmt->execute();

        $row = $stmt->fetch(PDO::FETCH_ASSOC);
        
        if ($row) {
            // Crear un objeto Usuario con los datos obtenidos
            return new Usuario($row['id'], $row['nombre'], $row['clave'], $row['email']);
        }
        return null; // Si no se encuentra el usuario
    }


    // Actualizar un usuario (Update)
    public function actualizarUsuario(Usuario $usuario) {
        $sql = "UPDATE usuarios SET nombre = :nombre, email = :email, clave = :clave WHERE id = :id";
        $stmt = $this->conn->prepare($sql);
    
        // Asignar valores a variables temporales antes de pasarlas a bindParam
        $nombre = $usuario->getNombre();
        $email = $usuario->getEmail();
        $clave = $usuario->getClave();
        $id = $usuario->getId();
    
        // Ahora pasamos las variables a bindParam
        $stmt->bindParam(':nombre', $nombre);
        $stmt->bindParam(':email', $email);
        $stmt->bindParam(':clave', $clave);
        $stmt->bindParam(':id', $id);
    
        return $stmt->execute();
    }

    // Borrar un usuario (Delete)
    public function eliminarUsuario($id) {
        $sql = "DELETE FROM usuarios WHERE id = :id";
        $stmt = $this->conn->prepare($sql);
        $stmt->bindParam(':id', $id);
        return $stmt->execute();
    }
}
?>
```
