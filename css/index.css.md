``` bash
/* Estilos globales */
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #00a2e8; /* Fondo azul */
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}

/* Contenedor principal */
.login-container {
    background-color: #ffffff;
    width: 350px;
    border-radius: 10px;
    box-shadow: 0 4px 8px #00000033;
    padding: 20px;
    text-align: center;
}


/* Título */
h2 {
    background-color: #008cba; /* Fondo del título */
    color: white;
    margin: -20px -20px 20px -20px;
    padding: 15px;
    font-size: 20px;
    border-radius: 10px 10px 0 0;
}

/* Estilos para los grupos de formulario */
.form-group {
    margin-bottom: 15px;
    text-align: left;
}

/* Etiquetas de texto */
label {
    display: block;
    font-weight: bold;
    margin-bottom: 5px;
    font-size: 14px;
}

/* Campos de entrada */
input[type="text"], input[type="email"], input[type="password"] {
    width: 100%;
    padding: 10px;
    font-size: 14px;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
}

input[type="text"]:focus, input[type="email"]:focus, input[type="password"]:focus {
    outline: none;
    border-color: #00a2e8;
    box-shadow: 0 0 5px rgba(0, 162, 232, 0.5);
}

/* Botón */
button[type="submit"] {
    width: 100%;
    padding: 10px;
    background-color: #008cba;
    color: white;
    border: none;
    border-radius: 4px;
    font-size: 16px;
    cursor: pointer;
    margin-top: 10px;
}

button[type="submit"]:hover {
    background-color: #006f9a;
}

/* Mensaje debajo del formulario */
.message {
    font-size: 14px;
    margin-top: 10px;
}

.message a {
    color: #008cba;
    text-decoration: none;
}

.message a:hover {
    text-decoration: underline;
}

/* Ícono decorativo */
.icon {
    text-align: center;
    margin-bottom: 20px;
}

.icon img {
    width: 80px;
}

/* Ajuste para pantallas pequeñas */
@media (max-width: 400px) {
    .login-container {
        width: 90%;
    }
}

```
