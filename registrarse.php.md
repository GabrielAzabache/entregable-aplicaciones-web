``` bash
<?php
session_start();

// Redirigir si el usuario ya está autenticado
if (isset($_SESSION['email'])) {
    header("Location: cuenta.php");
    exit();
}
?>

<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Registrarse</title>
    <link rel="stylesheet" href="registrarse.css">
</head>
<body>
    <div class="register-container">
        <h2>Crear una Cuenta</h2>
        <form action="controller_login.php" method="POST" id="formRegister">
            <div class="form-group">
                <label for="nombre">Nombre:</label>
                <div class="input-with-icon">
                    <div class="icon">
                        <img src="usuario.png" alt="Icono de usuario">
                    </div>
                    <input type="text" id="nombre" name="nombre" required placeholder="Introduce tu nombre">
                </div>
            </div>
            <div class="form-group">
                <label for="email">Email:</label>
                <div class="input-with-icon">
                    <div class="icon">
                        <img src="email.png" alt="Icono de email">
                    </div>
                    <input type="email" id="email" name="email" required placeholder="Introduce tu email">
                </div>
            </div>
            <div class="form-group">
                <label for="clave">Contraseña:</label>
                <div class="input-with-icon">
                    <div class="icon">
                        <img src="password.png" alt="Icono de contraseña">
                    </div>
                    <input type="password" id="clave" name="clave" required placeholder="Introduce tu contraseña">
                </div>
            </div>
            <div class="form-group">
                <label for="confirmar_clave">Confirmar Contraseña:</label>
                <div class="input-with-icon">
                    <div class="icon">
                        <img src="password.png" alt="Icono de confirmar contraseña">
                    </div>
                    <input type="password" id="confirmar_clave" name="confirmar_clave" required placeholder="Repite tu contraseña">
                </div>
            </div>
            <div class="form-group">
                <button type="submit" class="btn-submit" name="registro">
                    <div class="icon">
                        <img src="registro.png" alt="Icono de registro">
                    </div>
                    Registrar
                </button>
            </div>
        </form>
        <p class="message">¿Ya tienes cuenta? <a href="index.php">Inicia sesión aquí</a></p>
    </div>
</body>
</html>
```
