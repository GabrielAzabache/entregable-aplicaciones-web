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
    <title>Iniciar sesión</title>
    <link rel="stylesheet" href="index.css">
    <script src="https://code.jquery.com/jquery-3.7.1.min.js"></script>
</head>
<body>
    <div class="login-container">
        
        <h2>Iniciar Sesión</h2>
        <div class="icon">
            <img src="icono-candado.png" alt="Icono de candado">
        </div>
        <form id="formLogin">
            
            <!-- Campo de nombre de usuario -->
            <div class="form-group">
                <label for="nombre">Nombre:</label>
                <input type="text" id="nombre" name="nombre" required placeholder="Introduce tu nombre">
            </div>
            <!-- Campo de email -->
            <div class="form-group">
                <label for="email">Email:</label>
                <input type="email" id="email" name="email" required placeholder="Introduce tu email">
            </div>

            <!-- Campo de contraseña -->
            <div class="form-group">
                <label for="clave">Contraseña:</label>
                <input type="password" id="clave" name="clave" required placeholder="Introduce tu contraseña">
            </div>

            <button type="submit" class="btn-submit">Iniciar sesión</button>
        </form>
        <p class="message">¿No tienes cuenta? <a href="registrarse.php">Regístrate aquí</a></p>
        <div id="mensaje"></div>
    </div>

    <script>
        $(document).ready(function() {
            $("#formLogin").on("submit", function(e) {
                e.preventDefault();
                $.ajax({
                    url: "controller_login.php",
                    type: "POST",
                    data: $(this).serialize(),
                    success: function(response) {
                        if (response === "success") {
                            window.location.href = "cuenta.php";
                        } else {
                            $("#mensaje").html("<p style='color:red;'>Usuario o contraseña incorrectos</p>");
                        }
                    },
                    error: function() {
                        $("#mensaje").html("<p style='color:red;'>Ocurrió un error en el servidor.</p>");
                    }
                });
            });
        });
    </script>
</body>
</html>
```
