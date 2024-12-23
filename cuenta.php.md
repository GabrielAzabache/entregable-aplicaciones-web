## Primera version:
``` bash
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

```

## Segunda version (Entregable 2):
``` bash
<?php
session_start();

if (!isset($_SESSION['email'])) {
    header("Location: index.php");
    exit();
}

require_once 'crud_usuario.php';
require_once 'crud_cuenta.php';

// Obtener el usuario actual
$crudUsuario = new CrudUsuario();
$usuario = $crudUsuario->obtenerUsuarioPorEmail($_SESSION['email']);

// Obtener la cuenta de ahorros del usuario
$crudCuenta = new CrudCuenta();
$cuenta = $crudCuenta->obtenerCuentaPorUsuarioId($usuario->getId());

// Si no existe una cuenta de ahorros para el usuario, crearla
if ($cuenta === null) {
    $cuenta = new CuentaAhorros(null, $usuario->getId());
    $crudCuenta->crearCuenta($cuenta);
    $cuenta = $crudCuenta->obtenerCuentaPorUsuarioId($usuario->getId());  // Volver a cargar la cuenta
}

// Manejo de formularios de agregar y retirar saldo
if (isset($_POST['agregarSaldo'])) {
    $monto = $_POST['monto'];
    $cuenta->agregarSaldo($monto);
    $crudCuenta->actualizarSaldo($cuenta);
    header("Location: cuenta.php");
}

if (isset($_POST['retirarSaldo'])) {
    $monto = $_POST['montoRetiro'];
    if ($cuenta->retirarSaldo($monto)) {
        $crudCuenta->actualizarSaldo($cuenta);
        header("Location: cuenta.php");
    } else {
        echo "<p style='color:red;'>Saldo insuficiente.</p>";
    }
}

if (isset($_POST['logout'])) {
    session_unset();
    session_destroy();
    header("Location: index.php");
}
?>

<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cuenta de Ahorros</title>
    <link rel="stylesheet" href="cuenta.css">
</head>
<body>
    <div class="container">
        <h1>Bienvenido, <?php echo htmlspecialchars($usuario->getNombre()); ?>!</h1>
        <p>Tu saldo actual es: $<?php echo number_format($cuenta->getSaldo(), 2); ?></p>

        <!-- Formulario para agregar saldo -->
        <form action="cuenta.php" method="POST">
            <input type="number" name="monto" placeholder="Monto a agregar" required>
            <button type="submit" name="agregarSaldo">Agregar Saldo</button>
        </form>

        <!-- Formulario para retirar saldo -->
        <form action="cuenta.php" method="POST">
            <input type="number" name="montoRetiro" placeholder="Monto a retirar" required>
            <button type="submit" name="retirarSaldo">Retirar Saldo</button>
        </form>

        <form action="cuenta.php" method="POST">
            <button type="submit" name="logout">Cerrar sesión</button>
        </form>
    </div>
</body>
</html>

```
