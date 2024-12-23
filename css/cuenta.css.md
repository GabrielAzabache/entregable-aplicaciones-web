``` bash
/* Estilos globales */
body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4; /* Fondo gris claro */
    margin: 0;
    padding: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    text-align: center;
}

/* Contenedor principal */
.container {
    background-color: white;
    padding: 30px;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    width: 350px;
    text-align: center;
}

/* Título */
h1 {
    font-size: 24px;
    color: #008cba; /* Color azul */
    margin-bottom: 20px;
}

/* Párrafo de bienvenida */
p {
    font-size: 16px;
    color: #333;
    margin-bottom: 20px;
}

/* Estilo para el botón de cerrar sesión */
button[type="submit"] {
    padding: 10px 20px;
    background-color: #008cba;
    color: white;
    border: none;
    border-radius: 4px;
    font-size: 16px;
    cursor: pointer;
    transition: background-color 0.3s ease;
}

button[type="submit"]:hover {
    background-color: #006f9a; /* Color más oscuro al pasar el cursor */
}

/* Estilos para pantallas pequeñas */
@media (max-width: 400px) {
    .container {
        width: 90%;
    }
}

```
