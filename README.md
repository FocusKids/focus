
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>FOCUS KIDS</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(to bottom right, #e3f2fd, #bbdefb);
      color: #333;
      margin: 0;
      padding: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      overflow: hidden;
    }

    .container {
      text-align: center;
      background-color: #ffffffcc;
      padding: 40px;
      border-radius: 20px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.1);
      max-width: 700px;
      animation: fadeIn 1s ease-in-out;
    }

    h1, h2 {
      margin-bottom: 20px;
      color: #0d47a1;
    }

    p {
      font-size: 16px;
      line-height: 1.6;
      margin-bottom: 16px;
    }

    button {
      background-color: #2196f3;
      color: white;
      border: none;
      padding: 12px 24px;
      font-size: 16px;
      margin: 10px;
      border-radius: 10px;
      cursor: pointer;
      transition: transform 0.2s, background-color 0.3s;
    }

    button:hover {
      background-color: #1976d2;
      transform: scale(1.05);
    }

    .hidden {
      display: none;
    }

    .visor {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 10px;
      margin: 20px 0;
    }

    .visor img {
      max-width: 90vw;
      max-height: 70vh;
      object-fit: contain;
      border-radius: 20px;
      box-shadow: 0 10px 25px rgba(0,0,0,0.2);
      transition: transform 0.3s ease;
    }

    .nav-buttons {
      display: flex;
      justify-content: center;
      gap: 20px;
    }

    .nav-btn {
      background-color: #1976d2;
      color: white;
      border: none;
      font-size: 24px;
      padding: 10px 16px;
      border-radius: 10px;
      cursor: pointer;
      transition: background-color 0.3s;
    }

    .nav-btn:hover {
      background-color: #0d47a1;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: scale(0.95); }
      to { opacity: 1; transform: scale(1); }
    }
  </style>
</head>
<body>
  <audio id="click-sound" src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_7b3919fcdb.mp3?filename=button-click-124476.mp3"></audio>

  <div class="container" id="home">
    <h1>FOCUS KIDS</h1>
    <h2>¿QUÉ ERES?</h2>
    <button onclick="seleccionar('student')">Estudiante</button>
    <button onclick="seleccionar('tutor')">Padre/Tutor</button>
  </div>

  <div class="container hidden" id="student">
    <h2>¡Hola, estudiante!</h2>
    <button onclick="mostrarActividades('lenguaje')">Lenguaje</button>
    <button onclick="mostrarActividades('cientifico')">Científico</button>
    <button onclick="mostrarActividades('comunitario')">Comunitario</button>
    <button onclick="mostrarActividades('etica')">Ética</button>
    <button onclick="volver('home')">Volver al inicio</button>
  </div>

  <div class="container hidden" id="actividad">
    <h2 id="actividadTitulo"></h2>
    <div class="visor">
      <div class="nav-buttons">
        <button class="nav-btn" onclick="cambiarImagen(-1)">⟵</button>
        <button class="nav-btn" onclick="cambiarImagen(1)">⟶</button>
      </div>
      <img id="imagenActual" src="" alt="Actividad">
      <p id="contadorImagen">Imagen 1 de 1</p>
    </div>
    <button onclick="volver('student')">Volver</button>
  </div>

  <div class="container hidden" id="tutor">
    <h2>¡Hola, Padre/Tutor!</h2>
    <p><strong>Discalculia:</strong> Dificultad en habilidades matemáticas que afecta tareas como medir tiempo, manejar dinero o cocinar.</p>
    <p><strong>Dislexia:</strong> Trastorno específico de la lectura que impacta la comprensión lectora y el rendimiento escolar.</p>
    <p><strong>TDAH:</strong> Trastorno neuropsiquiátrico con síntomas de impulsividad, hiperactividad y dificultad para concentrarse.</p>
    <button onclick="volver('home')">Volver al inicio</button>
  </div>

  <script>
    const actividades = {
      lenguaje: ["3.jpg", "4.jpg", "5.jpg", "6.jpg", "7.jpg"],
      cientifico: ["9.jpg", "10.png", "11.jpg", "12.jpg"],
      comunitario: ["14.jpg", "15.jpg", "16.jpg", "17.jpg"],
      etica: ["19.jpg", "20.jpg"]
    };

    let indiceActual = 0;
    let imagenesActuales = [];

    function reproducirSonido() {
      const sonido = document.getElementById("click-sound");
      sonido.currentTime = 0;
      sonido.play();
    }

    function seleccionar(tipo) {
      reproducirSonido();
      mostrarSeccion(tipo);
    }

    function volver(seccion) {
      reproducirSonido();
      mostrarSeccion(seccion);
    }

    function mostrarSeccion(id) {
      document.querySelectorAll('.container').forEach(div => div.classList.add("hidden"));
      document.getElementById(id).classList.remove("hidden");
    }

    function mostrarActividades(materia) {
      reproducirSonido();
      imagenesActuales = actividades[materia];
      indiceActual = 0;
      actualizarImagen();
      document.getElementById("actividadTitulo").innerText = `Actividades de ${materia.charAt(0).toUpperCase() + materia.slice(1)}`;
      mostrarSeccion("actividad");
    }

    function actualizarImagen() {
      const img = document.getElementById("imagenActual");
      img.src = imagenesActuales[indiceActual];
      document.getElementById("contadorImagen").innerText = `Imagen ${indiceActual + 1} de ${imagenesActuales.length}`;
    }

    function cambiarImagen(direccion) {
      reproducirSonido();
      indiceActual = (indiceActual + direccion + imagenesActuales.length) % imagenesActuales.length;
      actualizarImagen();
    }
  </script>
</body>
</html>
