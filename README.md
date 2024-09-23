<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-9">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cuaderno Interactivo</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css" rel="stylesheet">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Dancing+Script&family=Roboto:wght@300;400;700&display=swap');

        body {
            font-family: 'Roboto', sans-serif;'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', sans-serif;
            background: linear-gradient(135deg, #f9e0e0, #ffe5f0);
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }

        .cuaderno {
            width: 90%;
            max-width: 800px;
            height: auto;
            background-color: #fff8f8;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            position: relative;
            overflow: hidden;
            padding: 30px;
            box-sizing: border-box;
        }

        .bienvenida {
            height: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            background-color: #fff0f5;
            color: #ff69b4;
            font-size: 32px;
            text-align: center;
            z-index: 2;
            font-family: 'Dancing Script', cursive;
        }

        .bienvenida p {
            font-size: 48px;
            margin: 0;
            padding: 20px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
        }

        .bienvenida button {
            background-color: #ff69b4;
            border: none;
            color: white;
            padding: 15px 30px;
            font-size: 24px;
            cursor: pointer;
            outline: none;
            margin: 15px;
            border-radius: 50px;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(255, 105, 180, 0.4);
        }

        .bienvenida button:hover {
            background-color: #ff1493;
            transform: translateY(-3px);
        }

        .pagina {
            display: none;
            box-sizing: border-box;
            text-align: center;
            animation: fadeIn 0.5s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .pagina.active {
            display: block;
        }

        .contenido-wrapper {
            max-width: 100%;
            margin: auto;
            text-align: center;
        }

        .titulo {
            font-size: 36px;
            font-weight: bold;
            margin-bottom: 20px;
            color: #ff1493;
            font-family: 'Dancing Script', cursive;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
        }

        .contenido {
            font-size: 20px;
            line-height: 1.6;
            text-align: justify;
            margin-bottom: 30px;
            color: #333;
        }

        .galeria {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 15px;
        }

        .galeria img {
            width: calc(33.33% - 10px);
            max-width: 200px;
            height: auto;
            border-radius: 15px;
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
            transition: transform 0.3s ease;
        }

        .galeria img:hover {
            transform: scale(1.05);
        }

        .navegacion {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background-color: #ff69b4;
            padding: 15px 0;
            z-index: 3;
            overflow-x: auto;
            white-space: nowrap;
        }

        .navegacion-content {
            display: flex;
            justify-content: space-between;
            width: 100%;
            margin: 0 auto;
        }

        .navegacion button {
            background-color: transparent;
            border: 2px solid white;
            color: white;
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
            outline: none;
            flex-grow: 1;
            margin: 0 5px;
            border-radius: 25px;
            transition: all 0.3s ease;
        }

        .navegacion button:hover {
            background-color: white;
            color: #ff69b4;
        }

        .navegacion::-webkit-scrollbar {
            height: 8px;
        }

        .navegacion::-webkit-scrollbar-track {
            background: #ff96c8;
        }

        .navegacion::-webkit-scrollbar-thumb {
            background: #ff1493;
            border-radius: 4px;
        }

        .navegacion::-webkit-scrollbar-thumb:hover {
            background: #d6006b;
        }

        @media (max-width: 600px) {
            .titulo {
                font-size: 28px;
            }

            .contenido {
                font-size: 18px;
            }

            .bienvenida p {
                font-size: 32px;
            }

            .bienvenida button {
                font-size: 18px;
                padding: 12px 24px;
            }

            .navegacion button {
                font-size: 14px;
                padding: 8px 16px;
            }
        }

        .codigo-wrapper {
            margin: 30px auto;
            max-width: 400px;
            text-align: center;
            background-color: #fff0f5;
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);
        }

        .codigo-input {
            font-size: 20px;
            padding: 12px;
            width: 100%;
            max-width: 300px;
            margin-bottom: 15px;
            border: 2px solid #ff69b4;
            border-radius: 25px;
            outline: none;
            transition: all 0.3s ease;
        }

        .codigo-input:focus {
            border-color: #ff1493;
            box-shadow: 0 0 8px rgba(255, 20, 147, 0.5);
        }

        .codigo-button {
            background-color: #ff69b4;
            border: none;
            color: white;
            padding: 12px 24px;
            font-size: 18px;
            cursor: pointer;
            outline: none;
            border-radius: 25px;
            margin: 0 5px;
            transition: all 0.3s ease;
        }

        .codigo-button:hover {
            background-color: #ff1493;
            transform: translateY(-2px);
        }

        .codigo-mensaje {
            font-size: 24px;
            color: #ff1493;
            margin-top: 20px;
            font-weight: bold;
        }

        .codigo-button-container {
            display: flex;
            justify-content: center;
            gap: 15px;
        }

        .imagen-centrada {
            display: block;
            margin: 0 auto;
            max-width: 100%;
            height: auto;
            border-radius: 15px;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
            transition: transform 0.3s ease;
        }

        .imagen-centrada:hover {
            transform: scale(1.02);
        }

        a {
            color: #ff1493;
            text-decoration: none;
            transition: color 0.3s ease;
        }

        a:hover {
            color: #ff69b4;
            text-decoration: underline;
        }

        .icono {
            font-size: 48px;
            color: #ff69b4;
            margin-left: 10px;
            vertical-align: middle;
        }
    </style>
</head>
<body>
    <div class="cuaderno">
        <div class="bienvenida" id="pantallaBienvenida">
            <div>
                <p>¿Soy yo</p>
                <button id="btnSi" onclick="mostrarContenido()">Sí, soy yo <i class="fas fa-smile"></i></button>
                <button id="btnNo" onclick="mostrarMensajeNegativo()">No soy <i class="fas fa-frown"></i></button>
            </div>
        </div>

        <div class="paginas" id="contenido" style="display: none;">
            <!-- Pagina 1 -->
            <div id="pagina1" class="pagina">
                <div class="contenido-wrapper">
                    <div class="titulo">Querida - 28/09 (DD) <i class="fas fa-star icono"></i></div>
                    <div class="contenido">
                        <p>Cuenta una leyenda que todos nacemos con un hilo rojo invisible atado a la persona que amaremos por siempre sin importar el tiempo, el lugar o la circunstancia el hilo se podrá estirar contraer o enredar pero jamás romperse. </p>

<p style="text-align: center;">Proverbios 3:15. &#x2764;</p>
                    </div>
                </div>
            </div>

            <!-- Página 2 -->
            <div id="pagina2" class="pagina">
                <div class="contenido-wrapper">
                    <div class="titulo">Niña - 08/07 (MM) <i class="fas fa-crown"></i></div>

                    <div class="contenido">
                        <p>No crei en los por siempre hasta que te conocí no me mal entiendas nose si por siempre estaremos juntos todos sabemos que eso es algo incierto en realidad pero si algo tengo seguro es que el silencio de tus besos jamás se me va a olvidar que el calor de tus abrazos siempre voy a recordar aunque me apartas en pedazos por siempre te voy amar. </p>
<p style="text-align: center;">Salmos 20:4. &#x2764;</p>
                    </div>
                </div>
            </div>

            <!-- Página 3 -->
            <div id="pagina3" class="pagina">
                <div class="contenido-wrapper">
                    <div class="titulo">Deportes - 2001/2022 (YYYY) <i class="fas fa-futbol icono"></i></div>
                    <div class="contenido">
                        <p>No soy hábil con las palabras ni con las acciones, nunca se me ha dado bien demostrar esfuerzo. Soy tímido y salir de mi zona de confort me resulta muy difícil. Expresar emociones es complicado para mí, especialmente cuando se trata de amor. Pero te amo. Puede que no sea capaz de decirlo o de actuar como si lo sintiera, incluso podría parecer que hago menos esfuerzo que otros. Sin embargo, puedes estar seguro de algo: nunca dejaré de amarte. TE AMO. </p>
<p style="text-align: center;">Génesis 28:15. &#x2764;</p>
                    </div>
                </div>
            </div>

            <!-- Página 4 -->
            <div id="pagina4" class="pagina">
                <div class="contenido-wrapper">
                    <div class="titulo">Video Especial <i class="fas fa-film icono"></i></div>
                    <a href="https://youtu.be/W1IOn2B5Ak8?si=OkAN245OBU6Nu-n3" target="_blank">Ver Video en YouTube <i class="fas fa-external-link-alt"></i></a>
                    <div class="contenido">
                     <p>Ellos dos se dejaron de ver, el se fue, pasaron 5 largos meses y los dos se desconectaron de la vida del otro &#x1F622;. Ella no sabía nada de él y él no sabía nada de ella, por paz mental, por querer avanzar, no porque se hubieran dejado de amar. El sentía que algo en su vida estaba en pausa, quería contarle tantas cosas y le dolía no estar presente en la vida de ella. No había manera de decírselo, así que le escribió una canción en donde le mostró toda su nostalgia y encapsuló ese sentimiento &#x1F622; y dejó que esa canción navegara hasta que encontrara algún día su destino, mientras pasaba por otros oídos que encontraban en ella algo valioso...</p>
                    </div>
                </div>
            </div>

            <!-- Página 5 -->
            <div id="pagina5" class="pagina">
                <div class="contenido-wrapper">
                    <div class="titulo">¡Feliz Cumpleaños! <i class="fas fa-birthday-cake icono"></i></div>
                    <div class="contenido">
                        <p>No sé muy bien cómo empezar, pero hay algo que he querido decirte por un tiempo, y pensé que hoy, en tu cumpleaños, sería el mejor momento. Esta página es solo una pequeña muestra de lo que significas para mí &#x2764;.</p>
                        <p>Las fotos que ves aquí son mucho más que simples imágenes &#x1F5BC;. Para mí, cada una tiene una historia detrás, un recuerdo que me sigue sacando una sonrisa &#x1F60A;. A veces me sorprendo mirando esas fotos &#x1F5BC; y recordando lo fácil que era reírnos &#x1F60A;, lo mucho que disfrutábamos estar juntos, aunque fuera haciendo las cosas más simples. Siempre he sido de los que creen que las cosas buenas deben ser recordadas, y eso es lo que intento hacer aquí: recordar lo bueno, lo que fue real.</p>
                        <p>Espero que este día sea especial para ti, que lo disfrutes al máximo, como siempre deberías hacerlo. Y aunque no lo diga todos los días, quiero que sepas que te sigo deseando lo mejor, desde lo más profundo de mi ser &#x2764;.</p>
                      <p>Gracias por ser parte de mi vida &#x1F60D;, y por todos esos momentos que, para mí, siempre tendrán valor.</p>
                    </div>
                    <div class="galeria">
                        <img src="https://i.postimg.cc/KvZXZxSK/IMG-20240908-020808-321.jpg" alt="Foto de cumpleaños 1">
                        <img src="https://i.postimg.cc/jq600C90/IMG-20240908-020814-367.jpg" alt="Foto de cumpleaños 2">
                        <img src="https://i.postimg.cc/vTtpWS9H/IMG-20240908-020822-854.jpg" alt="Foto de cumpleaños 3">
                    </div>
                    <div class="galeria">
                        <img src="https://i.postimg.cc/brh7SjZB/IMG-20240908-020905-115.jpg" alt="Foto de cumpleaños 4">
                        <img src="https://i.postimg.cc/NMmh00jX/IMG-20240908-020922-527.jpg" alt="Foto de cumpleaños 5">
                        <img src="https://i.postimg.cc/5tZd1zb1/IMG-20240908-020942-666.jpg" alt="Foto de cumpleaños 6">
                    </div>
                    <div class="galeria">
                        <img src="https://i.postimg.cc/MKDSRXbb/IMG-20240908-021009-661.jpg" alt="Foto de cumpleaños 7">
                        <img src="https://i.postimg.cc/BnnGCsmW/IMG-20240908-181512.jpg" alt="Foto de cumpleaños 8">
                        <img src="https://i.postimg.cc/wj4YfPr1/IMG-20240908-181526.jpg" alt="Foto de cumpleaños 9">
                    </div>
                    <div class="galeria">
                        <img src="https://i.postimg.cc/PqLsByG2/IMG-20240908-181537.jpg" alt="Foto de cumpleaños 10">
                        <img src="https://i.postimg.cc/bN8Ps1bw/IMG-20240908-181548.jpg" alt="Foto de cumpleaños 11">
                    </div>
                </div>
            </div>

            <!-- Página 6 -->
            <div id="pagina6" class="pagina">
                <div class="contenido-wrapper">
                    <div class="titulo">¡Mensaje Especial! <i class="fas fa-envelope-open-text icono"></i></div>
                    <p>Por favor, ingresa el código para recibir un mensaje especial (DD-MM-YYYY) .</p>
                    <div class="codigo-wrapper">
                        <input type="text" id="codigoInput" class="codigo-input" placeholder="Ingresa el código">
                        <div class="codigo-button-container">
                            <button class="codigo-button" onclick="verificarCodigo()">Verificar Código <i class="fas fa-check"></i></button>
                            <button class="codigo-button" onclick="resetearCodigo()">Limpiar <i class="fas fa-undo"></i></button>
                        </div>
                        <div id="codigoMensaje" class="codigo-mensaje"></div>
                    </div>
                </div>
            </div>

            <!-- Nueva Página 7 -->
            <div id="pagina7" class="pagina">
                <div class="contenido-wrapper">
                    <div class="titulo">Flores Amarillas <i class="fas fa-sun icono"></i></div>
                    <div class="contenido">
                        <img src="https://i.postimg.cc/Kz4NZBcH/Screenshot-2024-09-16-23-22-57-866-edit-com-opera-browser.jpg" alt="Flores Amarillas" class="imagen-centrada">
                        <p>Cada 21 de septiembre, las flores amarillas florecen, trayendo consigo un mensaje de amor y esperanza. Estas hermosas flores son un recordatorio de que, incluso en los días más grises, la belleza y la alegría pueden brotar y florecer. Que estas flores amarillas iluminen tu camino y te recuerden que, al igual que ellas, tú también tienes el poder de hacer brillar el mundo con tu presencia.</p>
                    </div>
                </div>
            </div>
        </div>

        <div class="navegacion" id="navegacion" style="display: none;">
            <div class="navegacion-content">
                <button onclick="irPagina(1)">Página 1 <i class="fas fa-star envelope"></i></button>
                <button onclick="irPagina(2)">Página 2 <i class="fas fa-crown envelope"></i></button>
                <button onclick="irPagina(3)">Página 3 <i class="fas fa-futbol envelope"></i></button>
                <button onclick="irPagina(4)">Página 4 <i class="fas fa-film envelope"></i></button>
                <button onclick="irPagina(5)">Página 5 <i class="fas fa-birthday-cake envelope"></i></button>
                <button onclick="irPagina(6)">Página 6 <i class="fas fa-envelope-open-text envelope"></i></button>
                <button onclick="irPagina(7)">Página 7 <i class="fas fa-sun envelope"></i></button>
            </div>
        </div>
    </div>

    <script>
        function mostrarContenido() {
            document.getElementById('pantallaBienvenida').style.display = 'none';
            document.getElementById('contenido').style.display = 'block';
            document.getElementById('navegacion').style.display = 'block';
            irPagina(1); // Muestra la primera página al iniciar
        }

        function mostrarMensajeNegativo() {
            alert('Lo siento, parece que no fuiste lo suficientemente sincera. ¡Inténtalo de nuevo!');
        }

        function irPagina(numero) {
            const paginas = document.querySelectorAll('.pagina');
            paginas.forEach(pagina => pagina.classList.remove('active'));
            document.getElementById(`pagina${numero}`).classList.add('active');
        }

        function verificarCodigo() {
            const codigoInput = document.getElementById('codigoInput').value;
            const codigoMensaje = document.getElementById('codigoMensaje');
            
            if (codigoInput === '28082001') {
                codigoMensaje.innerHTML = '¡Código correcto! &#x2764; ¡Feliz cumpleaños! Que disfrutes de esta celebración llena de amor y alegría. &#x1F60A;';
            } else if (codigoInput === '09072022') {
                codigoMensaje.innerHTML = '¡Código correcto! &#x1F60D; Este es el día que comenzó en algún momento nuestro noviazgo, un día que aprecio mucho. Cada momento que pase contigo fue un tesoro. Te quiero mucho, Niña. &#x2764;';
            } else {
                codigoMensaje.innerHTML = 'Código incorrecto. &#x1F622; Intenta de nuevo. ¡Tú puedes!';
            }
        }

        function resetearCodigo() {
            document.getElementById('codigoInput').value = '';
            document.getElementById('codigoMensaje').textContent = '';
        }
    </script>
</body>
</html> 