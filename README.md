
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Focus Kids</title>
  <style>
    html, body {
      height: 100%;
      margin: 0;
      padding: 0;
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(to bottom right, #e3f2fd, #bbdefb);
    }

    body {
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .container {
      background-color: #ffffffdd;
      padding: 30px 20px;
      border-radius: 20px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.1);
      max-width: 700px;
      width: 90%;
      text-align: center;
      box-sizing: border-box;
      animation: fadeIn 0.6s ease-in-out;
    }

    h1, h2 {
      margin: 10px 0;
    }

    .options {
      display: flex;
      flex-direction: column;
      gap: 15px;
      margin-top: 20px;
      align-items: center;
    }

    button {
      background-color: #2196f3;
      color: white;
      border: none;
      padding: 14px 20px;
      font-size: 16px;
      width: 90%;
      max-width: 300px;
      border-radius: 10px;
      cursor: pointer;
      transition: transform 0.2s, background-color 0.3s;
    }

    button:hover {
      background-color: #1976d2;
      transform: scale(1.05);
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    @media (max-height: 500px) {
      body {
        align-items: flex-start;
        padding-top: 20px;
      }
    }
  </style>
</head>
<body>
  <div class="container" id="mainContainer">
    <h1>FOCUS KIDS</h1>
    <h2>¿QUÉ ERES?</h2>
    <div class="options" id="userOptions">
      <button onclick="showStudentOptions()">ESTUDIANTE</button>
      <button onclick="showParentOptions()">PADRE/TUTOR</button>
    </div>
  </div>

  <script>
    function showStudentOptions() {
      const container = document.getElementById("mainContainer");
      container.innerHTML = `
        <h2>Opciones para Estudiantes</h2>
        <div class="options">
          <button>Ejercicios de concentración</button>
          <button>Juegos educativos</button>
          <button>Mi progreso</button>
          <button onclick="goBack()">Volver</button>
        </div>
      `;
    }

    function showParentOptions() {
      const container = document.getElementById("mainContainer");
      container.innerHTML = `
        <h2>Opciones para Padres/Tutores</h2>
        <div class="options">
          <button>Reportes de avance</button>
          <button>Consejos y recursos</button>
          <button>Configuración del perfil</button>
          <button onclick="goBack()">Volver</button>
        </div>
      `;
    }

    function goBack() {
      const container = document.getElementById("mainContainer");
      container.innerHTML = `
        <h1>FOCUS KIDS</h1>
        <h2>¿QUÉ ERES?</h2>
        <div class="options" id="userOptions">
          <button onclick="showStudentOptions()">ESTUDIANTE</button>
          <button onclick="showParentOptions()">PADRE/TUTOR</button>
        </div>
      `;
    }
  </script>
</body>
</html>
