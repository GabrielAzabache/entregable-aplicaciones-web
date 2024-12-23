``` bash
<?php
require_once 'conexion.php';
require_once 'cuenta_ahorros.php';

class CrudCuenta {
    private $conn;

    public function __construct() {
        $this->conn = (new Conexion())->getConexion();
    }

    public function crearCuenta(CuentaAhorros $cuenta) {
        $sql = "INSERT INTO cuentas_ahorros (usuario_id, saldo) VALUES (:usuario_id, :saldo)";
        $stmt = $this->conn->prepare($sql);

        // Asignar valores a variables antes de bindParam
        $usuarioId = $cuenta->getUsuarioId();
        $saldo = $cuenta->getSaldo();

        $stmt->bindParam(':usuario_id', $usuarioId);
        $stmt->bindParam(':saldo', $saldo);

        return $stmt->execute();
    }

    public function obtenerCuentaPorUsuarioId($usuarioId) {
        $sql = "SELECT * FROM cuentas_ahorros WHERE usuario_id = :usuario_id";
        $stmt = $this->conn->prepare($sql);

        // Asignar valores a variables antes de bindParam
        $stmt->bindParam(':usuario_id', $usuarioId);
        $stmt->execute();

        $row = $stmt->fetch(PDO::FETCH_ASSOC);

        if ($row) {
            return new CuentaAhorros($row['id'], $row['usuario_id'], $row['saldo']);
        }
        return null;
    }

    public function actualizarSaldo(CuentaAhorros $cuenta) {
        $sql = "UPDATE cuentas_ahorros SET saldo = :saldo WHERE id = :id";
        $stmt = $this->conn->prepare($sql);

        // Asignar valores a variables antes de bindParam
        $saldo = $cuenta->getSaldo();
        $id = $cuenta->getId();

        $stmt->bindParam(':saldo', $saldo);
        $stmt->bindParam(':id', $id);

        return $stmt->execute();
    }
}
?>
```
