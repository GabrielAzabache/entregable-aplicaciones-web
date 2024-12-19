``` bash
<?php
class Usuario {
    private $id;
    private $nombre;
    private $clave;
    private $email;

    // Constructor de la clase
    public function __construct($id = null, $nombre = "", $clave = "", $email = "") {
        $this->id = $id;
        $this->nombre = $nombre;
        $this->clave = $clave ? password_hash($clave, PASSWORD_DEFAULT) : null;
        $this->email = $email;
    }
    

    // Getters (obtener los valores de las propiedades)
    public function getId() {
        return $this->id;
    }

    public function getNombre() {
        return $this->nombre;
    }

    public function getClave() {
        return $this->clave;
    }

    public function getEmail() {
        return $this->email;
    }

    // Setters (modificar los valores de las propiedades)
    public function setId($id) {
        $this->id = $id;
    }

    public function setNombre($nombre) {
        $this->nombre = $nombre;
    }

    public function setClave($clave) {
        $this->clave = password_hash($clave, PASSWORD_DEFAULT); // Encripta la contraseña
    }
    

    public function setEmail($email) {
        $this->email = $email;
    }

    // Convertir el objeto en un arreglo (útil para operaciones CRUD)
    public function toArray() {
        return [
            'id' => $this->id,
            'nombre' => $this->nombre,
            'clave' => $this->clave,
            'email' => $this->email
        ];
    }
}
?>

```
