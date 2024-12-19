
<?php
session_start();

// Verificar si la sesión está activa
if (!isset($_SESSION['email'])) {
    // Si no está autenticado, redirigir al login
    header("Location: index.php");
    exit();
}

// Manejar el cierre de sesión
if (isset($_POST['logout'])) {
    session_unset();   // Eliminar todas las variables de sesión
    session_destroy(); // Destruir la sesión
    header("Location: index.php"); // Redirigir al login
    exit();
}
?>

<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bienvenido</title>
    <link rel="stylesheet" href="cuenta.css">
</head>
<body>
    <div class="container">
        <h1>Bienvenido, <?php echo htmlspecialchars($_SESSION['nombre']); ?>!</h1>
        <p>Tu sesión ha sido iniciada correctamente.</p>

        <!-- Botón para cerrar sesión -->
        <form action="cuenta.php" method="POST">
            <button type="submit" name="logout">Cerrar sesión</button>
        </form>
    </div>
</body>
</html>

