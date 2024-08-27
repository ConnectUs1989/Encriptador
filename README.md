<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Encriptador de Texto</title>
    <style>
        :root {
            --color-dark: #181818;
            --color-gray-dark: #282828;
            --color-gray-light: #3d3d3d;
            --color-accent: #ff5864;
            --color-text-light: #f5f5f5;
            --color-footer: #AAB2D5;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: 'Roboto', sans-serif;
            background-color: var(--color-dark);
            color: var(--color-text-light);
            display: flex;
            flex-direction: column;
            min-height: 100vh;
        }

        main {
            flex: 1;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }

        .container {
            background-color: var(--color-gray-dark);
            display: grid;
            grid-template-columns: 2fr 1fr;
            gap: 40px;
            padding: 40px;
            border-radius: 12px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            align-items: center;
            width: 100%;
            max-width: 1200px;
        }

        .left-section {
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        .logo-section {
            display: flex;
            align-items: center;
            margin-bottom: 20px;
        }

        .logo {
            width: 50px;
            height: auto;
            filter: brightness(0) invert(1); 
            margin-right: 10px;
        }

        .logo-text {
            font-size: 1.2rem;
            color: var(--color-text-light);
        }

        h1 {
            font-size: 2rem;
            color: var(--color-text-light);
            margin-bottom: 20px;
        }

        textarea {
            width: 100%;
            height: 150px;
            padding: 15px;
            font-size: 1.2rem;
            border: 2px solid var(--color-gray-light);
            background-color: var(--color-gray-dark);
            color: var(--color-text-light);
            border-radius: 8px;
            margin-bottom: 30px;
        }

        textarea::placeholder {
            color: var(--color-gray-light);
        }

        .buttons {
            display: flex;
            justify-content: space-around;
            gap: 20px;
        }

        button {
            flex: 1;
            padding: 15px;
            font-size: 1.2rem;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .btn-encrypt {
            background-color: var(--color-accent);
            color: #FFFFFF;
        }

        .btn-encrypt:hover {
            background-color: #e74c57;
        }

        .btn-decrypt {
            background-color: var(--color-gray-light);
            color: var(--color-text-light);
        }

        .btn-decrypt:hover {
            background-color: var(--color-gray-dark);
        }

        .right-section {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
        }

        .right-section img {
            max-width: 80%;
            margin-bottom: 20px;
            filter: brightness(0) invert(1); 
        }

        .result-section {
            background-color: var(--color-gray-light);
            padding: 20px;
            border-radius: 8px;
            text-align: center;
            border: 2px solid var(--color-gray-light);
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
        }

        .result-section h2 {
            margin-bottom: 10px;
            color: var(--color-text-light);
        }

        .result-section p {
            font-size: 1.2rem;
            color: var(--color-text-light);
        }

        footer {
            background-color: var(--color-gray-dark);
            text-align: center;
            padding: 20px;
            font-size: 1rem;
            color: var(--color-text-light);
        }

        .footer-icons {
            margin-top: 10px;
        }

        .footer-icons a {
            margin: 0 10px;
            text-decoration: none;
        }

        .footer-icons img {
            width: 24px;
            height: 24px;
            filter: brightness(0) invert(1); 
        }

        @media (max-width: 768px) {
            .container {
                grid-template-columns: 1fr;
                padding: 20px;
            }

            h1 {
                text-align: center;
            }

            .buttons {
                flex-direction: column;
                align-items: center;
            }

            button {
                width: 100%;
            }

            .right-section img {
                max-width: 100%;
            }

            .logo-text {
                font-size: 1rem;
            }
        }
    </style>
</head>
<body>

    <main>
        <div class="container">
            <div class="left-section">
                <div class="logo-section">
                    <img src="https://manafune.github.io/Alura-Challenge-Encriptador-Desencriptador/imagenes/Logo.png" alt="Logo" class="logo">
                    <span class="logo-text">by ConnectUs</span>
                </div>
                <h1>Ingrese el texto aquí</h1>
                <textarea id="input-text" placeholder="Escribe tu mensaje aquí..."></textarea>
                <div class="buttons">
                    <button class="btn-encrypt" onclick="encrypt()">Encriptar</button>
                    <button class="btn-decrypt" onclick="decrypt()">Desencriptar</button>
                </div>
            </div>
            <div class="right-section">
                <img src="https://manafune.github.io/Alura-Challenge-Encriptador-Desencriptador/imagenes/Muñeco.png" alt="Imagen descriptiva">
                <div class="result-section" id="result">
                    <h2>Ningún mensaje fue encontrado</h2>
                    <p>Ingresa el texto que desees encriptar o desencriptar.</p>
                </div>
            </div>
        </div>
    </main>

    <footer>
        © Hollman Ballen, Colombia - 2024
        <div class="footer-icons">
            <a href="https://github.com/ConnectUs1989/connectus/issues/1" target="_blank">
                <img src="https://cdn-icons-png.flaticon.com/512/25/25231.png" alt="GitHub">
            </a>
        </div>
    </footer>

    <script>
        function encrypt() {
            let text = document.getElementById('input-text').value;
            let encryptedText = text
                .replace(/e/g, "enter")
                .replace(/i/g, "imes")
                .replace(/a/g, "ai")
                .replace(/o/g, "ober")
                .replace(/u/g, "ufat");
            
            document.getElementById('result').innerHTML = `<h2>Texto Encriptado:</h2><p>${encryptedText}</p>`;
        }

        function decrypt() {
            let text = document.getElementById('input-text').value;
            let decryptedText = text
                .replace(/enter/g, "e")
                .replace(/imes/g, "i")
                .replace(/ai/g, "a")
                .replace(/ober/g, "o")
                .replace(/ufat/g, "u");
            
            document.getElementById('result').innerHTML = `<h2>Texto Desencriptado:</h2><p>${decryptedText}</p>`;
        }
    </script>

</body>
</html>






