<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Focus Kids - Actividades</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
        }
        .container {
            margin: 20px;
        }
        .hidden {
            display: none;
        }
        .activity-img {
            width: 80%;
            max-width: 600px;
        }
        button {
            margin: 10px;
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div class="container" id="menuPrincipal">
        <h1>Actividades</h1>
        <button onclick="mostrarMaterias()">Seleccionar Materia</button>
    </div>

    <div class="container hidden" id="menuMaterias">
        <h2>Selecciona una materia</h2>
        <button onclick="cargarActividades('lenguaje')">Lenguaje</button>
        <button onclick="cargarActividades('cientifico')">Saberes y Pensamiento Científico</button>
        <button onclick="cargarActividades('comunitario')">De lo Humano y lo Comunitario</button>
        <button onclick="cargarActividades('etica')">Ética, Naturaleza y Sociales</button>
        <button onclick="volverInicio()">Volver</button>
    </div>

    <div class="container hidden" id="visorActividades">
        <h2 id="tituloMateria"></h2>
        <img id="imagenActividad" class="activity-img" src="" alt="Actividad">
        <br>
        <button onclick="cambiarImagen(-1)">Anterior</button>
        <button onclick="cambiarImagen(1)">Siguiente</button>
        <br>
        <button onclick="volverMaterias()">Volver</button>
    </div>

    <script>
        const actividades = {
            "lenguaje": ["img1.jpg", "img2.jpg", "img3.jpg"], // Reemplaza con las rutas correctas
            "cientifico": ["img4.jpg", "img5.jpg", "img6.jpg"],
            "comunitario": ["img7.jpg", "img8.jpg"],
            "etica": ["img9.jpg", "img10.jpg"]
        };

        let materiaActual = "";
        let indiceImagen = 0;

        function mostrarMaterias() {
            document.getElementById("menuPrincipal").classList.add("hidden");
            document.getElementById("menuMaterias").classList.remove("hidden");
        }

        function cargarActividades(materia) {
            materiaActual = materia;
            indiceImagen = 0;
            document.getElementById("menuMaterias").classList.add("hidden");
            document.getElementById("visorActividades").classList.remove("hidden");
            document.getElementById("tituloMateria").innerText = materia.replace("cientifico", "Saberes y Pensamiento Científico")
                                                                      .replace("comunitario", "De lo Humano y lo Comunitario")
                                                                      .replace("etica", "Ética, Naturaleza y Sociales");
            actualizarImagen();
        }

        function actualizarImagen() {
            document.getElementById("imagenActividad").src = actividades[materiaActual][indiceImagen];
        }

        function cambiarImagen(direccion) {
            indiceImagen += direccion;
            if (indiceImagen < 0) {
                indiceImagen = 0;
            } else if (indiceImagen >= actividades[materiaActual].length) {
                indiceImagen = actividades[materiaActual].length - 1;
            }
            actualizarImagen();
        }

        function volverMaterias() {
            document.getElementById("visorActividades").classList.add("hidden");
            document.getElementById("menuMaterias").classList.remove("hidden");
        }

        function volverInicio() {
            document.getElementById("menuMaterias").classList.add("hidden");
            document.getElementById("menuPrincipal").classList.remove("hidden");
        }
    </script>
</body>
</html>
