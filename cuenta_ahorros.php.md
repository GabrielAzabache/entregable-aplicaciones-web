``` bash

<?php
class CuentaAhorros {
    private $id;
    private $usuarioId;
    private $saldo;

    public function __construct($id = null, $usuarioId = null, $saldo = 0) {
        $this->id = $id;
        $this->usuarioId = $usuarioId;
        $this->saldo = $saldo;
    }

    public function getId() {
        return $this->id;
    }

    public function getUsuarioId() {
        return $this->usuarioId;
    }

    public function getSaldo() {
        return $this->saldo;
    }

    public function setSaldo($saldo) {
        $this->saldo = $saldo;
    }

    public function agregarSaldo($monto) {
        $this->saldo += $monto;
    }

    public function retirarSaldo($monto) {
        if ($this->saldo >= $monto) {
            $this->saldo -= $monto;
            return true;
        }
        return false;
    }

    public function toArray() {
        return [
            'id' => $this->id,
            'usuarioId' => $this->usuarioId,
            'saldo' => $this->saldo
        ];
    }
}
?>

```
