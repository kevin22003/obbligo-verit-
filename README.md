# obbligo-verit-
<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Obbligo o Verità</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>Obbligo o Verità</h1>
        <div class="input-section">
            <h2>Aggiungi un Obbligo o una Verità</h2>
            <input type="text" id="inputText" placeholder="Inserisci un obbligo o una verità">
            <button onclick="addTask()">Aggiungi</button>
        </div>
        <div class="display-section">
            <button onclick="showTask('obbligo')">Obbligo</button>
            <button onclick="showTask('verità')">Verità</button>
            <div id="taskDisplay"></div>
        </div>
    </div>
    <script src="script.js"></script>
</body>
</html>

body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.container {
    background-color: #fff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    text-align: center;
    width: 300px;
}

.input-section, .display-section {
    margin-bottom: 20px;
}

input[type="text"] {
    width: calc(100% - 100px);
    padding: 10px;
    margin-right: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
}

button {
    padding: 10px;
    background-color: #28a745;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

button:hover {
    background-color: #218838;
}

let tasks = {
    obbligo: [],
    verità: []
};

function addTask() {
    const inputText = document.getElementById('inputText').value.trim();
    if (inputText) {
        if (inputText.toLowerCase().includes('verità')) {
            tasks.verità.push(inputText);
        } else {
            tasks.obbligo.push(inputText);
        }
        document.getElementById('inputText').value = '';
        alert('Aggiunto con successo!');
    } else {
        alert('Inserisci un obbligo o una verità.');
    }
}

function showTask(type) {
    const taskList = tasks[type];
    if (taskList.length === 0) {
        document.getElementById('taskDisplay').innerText = 'Nessun ' + type + ' disponibile.';
    } else {
        const randomTask = taskList[Math.floor(Math.random() * taskList.length)];
        document.getElementById('taskDisplay').innerText = randomTask;
    }
}
