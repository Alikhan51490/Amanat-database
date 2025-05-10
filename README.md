<!DOCTYPE html><html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Baza Dannykh Amanat</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: url('https://images.unsplash.com/photo-1506744038136-46273834b3fb') center/cover no-repeat;
      color: white;
      height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
    }
    h1 {
      font-size: 3em;
      background-color: rgba(0,0,0,0.5);
      padding: 0.5em 1em;
      border-radius: 10px;
    }
    .menu {
      position: absolute;
      top: 20px;
      right: 20px;
    }
    .menu button {
      background: transparent;
      border: none;
      font-size: 2em;
      color: white;
      cursor: pointer;
    }
    .dropdown {
      display: none;
      position: absolute;
      right: 0;
      background-color: rgba(0, 0, 0, 0.8);
      border-radius: 5px;
    }
    .dropdown a {
      color: white;
      padding: 10px;
      display: block;
      text-decoration: none;
    }
    .dropdown a:hover {
      background-color: rgba(255, 255, 255, 0.1);
    }
    .form-section {
      display: none;
      background-color: rgba(0,0,0,0.6);
      padding: 20px;
      border-radius: 10px;
      margin-top: 20px;
      width: 90%;
      max-width: 500px;
    }
    .form-section textarea {
      width: 100%;
      height: 150px;
      padding: 10px;
      font-size: 1em;
    }
    .form-section button {
      margin-top: 10px;
      padding: 10px 20px;
      font-size: 1em;
    }
  </style>
</head>
<body>
  <div class="menu">
    <button onclick="toggleDropdown()">⋮</button>
    <div class="dropdown" id="dropdownMenu">
      <a href="#" onclick="openForm('zak')">Заключения</a>
      <a href="#" onclick="openForm('uch')">Регистрация участков</a>
      <a href="#" onclick="openForm('dom')">Регистрация домов</a>
    </div>
  </div>
  <h1>Amanat</h1>  <div id="zak" class="form-section">
    <h2>Заключения</h2>
    <textarea id="zakData"></textarea>
    <button onclick="saveData('zak')">Сохранить</button>
  </div>
  <div id="uch" class="form-section">
    <h2>Регистрация участков</h2>
    <textarea id="uchData"></textarea>
    <button onclick="saveData('uch')">Сохранить</button>
  </div>
  <div id="dom" class="form-section">
    <h2>Регистрация домов</h2>
    <textarea id="domData"></textarea>
    <button onclick="saveData('dom')">Сохранить</button>
  </div>  <script>
    function toggleDropdown() {
      const menu = document.getElementById('dropdownMenu');
      menu.style.display = menu.style.display === 'block' ? 'none' : 'block';
    }

    function openForm(id) {
      document.querySelectorAll('.form-section').forEach(f => f.style.display = 'none');
      document.getElementById(id).style.display = 'block';
      loadData(id);
    }

    function saveData(id) {
      const data = document.getElementById(id + 'Data').value;
      localStorage.setItem(id + 'Data', data);
      alert('Данные сохранены');
    }

    function loadData(id) {
      const data = localStorage.getItem(id + 'Data');
      document.getElementById(id + 'Data').value = data || '';
    }
  </script></body>
</html># Amanat-database
