``` bash

<?php
session_start();
require_once 'conexion.php';
require_once 'usuario.php';
require_once 'crud_usuario.php';

// Manejo del inicio de sesión
if (isset($_POST['email']) && isset($_POST['clave'])) {
    $email = $_POST['email'];
    $clave = $_POST['clave'];

    // Verificar si el usuario existe
    $crud = new CrudUsuario();
    $usuario = $crud->obtenerUsuarioPorEmail($email);

    // Verificar si el usuario fue encontrado
    if ($usuario) {
        // Verificar si la contraseña es correcta
        if (password_verify($clave, $usuario->getClave())) {
            // Si la contraseña es correcta, iniciar sesión
            $_SESSION['email'] = $usuario->getEmail();
            $_SESSION['nombre'] = $usuario->getNombre();
            echo "success";
        } else {
            // Si la contraseña es incorrecta
            echo "Contraseña incorrecta";
        }
    } else {
        // Si no se encuentra el usuario con ese email
        echo "Usuario no encontrado";
    }
}

// Manejo del registro
if (isset($_POST['registro']) && isset($_POST['nombre']) && isset($_POST['email']) && isset($_POST['clave']) && isset($_POST['confirmar_clave'])) {
    $nombre = $_POST['nombre'];
    $email = $_POST['email'];
    $clave = $_POST['clave'];
    $confirmar_clave = $_POST['confirmar_clave'];

    // Validar que las contraseñas coinciden
    if ($clave === $confirmar_clave) {
        $usuario = new Usuario(null, $nombre, $clave, $email);
        $crud = new CrudUsuario();

        // Verificar si el email ya está registrado
        if ($crud->obtenerUsuarioPorEmail($email) === null) {
            // Si el email no está registrado, crear el usuario
            if ($crud->crearUsuario($usuario)) {
                $_SESSION['email'] = $usuario->getEmail();
                $_SESSION['nombre'] = $usuario->getNombre();
                echo "success";
            } else {
                echo "Error al registrar el usuario";
            }
        } else {
            echo "El email ya está registrado";
        }
    } else {
        echo "Contraseñas no coinciden";
    }
}
?>
```
