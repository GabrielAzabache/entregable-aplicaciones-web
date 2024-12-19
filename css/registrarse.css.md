``` bash
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background: linear-gradient(135deg, #74b9ff, #0984e3);
    color: #fff;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}

.register-container {
    background-color: #2d3436;
    padding: 20px 30px;
    border-radius: 8px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
    width: 100%;
    max-width: 400px;
}

h2 {
    margin-bottom: 20px;
    text-align: center;
}

.form-group {
    margin-bottom: 15px;
}

.input-with-icon {
    display: flex;
    align-items: center;
    background-color: #fff;
    border-radius: 5px;
    padding: 5px;
}

.input-with-icon .icon {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 5px;
}

.input-with-icon img {
    width: 20px;
    height: 20px;
}

.input-with-icon input[type="text"],
.input-with-icon input[type="email"],
.input-with-icon input[type="password"] {
    border: none;
    flex: 1;
    padding: 10px;
    font-size: 14px;
    border-radius: 0 5px 5px 0;
    outline: none;
}

.input-with-icon input[type="text"]:focus,
.input-with-icon input[type="email"]:focus,
.input-with-icon input[type="password"]:focus {
    box-shadow: 0 0 5px #74b9ff;
}

.btn-submit {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    padding: 10px;
    background-color: #0984e3;
    color: #fff;
    font-size: 16px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s;
}

.btn-submit .icon {
    margin-right: 10px;
}

.btn-submit img {
    width: 20px;
    height: 20px;
}

.btn-submit:hover {
    background-color: #74b9ff;
}

.message {
    text-align: center;
    margin-top: 15px;
    font-size: 14px;
}

.message a {
    color: #74b9ff;
    text-decoration: none;
}

.message a:hover {
    text-decoration: underline;
}


```
