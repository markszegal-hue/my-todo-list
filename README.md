# my-todo-list
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-Do List</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>My To-Do List</h1>
        <input type="text" id="new-item" placeholder="Add a new item...">
        <button id="add-button">Add</button>
        <ul id="item-list"></ul>
    </div>
    <script src="script.js"></script>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    margin: 0;
    padding: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}

.container {
    background-color: white;
    padding: 20px;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    width: 300px;
    text-align: center;
}

input {
    padding: 10px;
    margin-right: 10px;
    border: 1px solid #ddd;
    border-radius: 3px;
}

button {
    padding: 10px 15px;
    border: none;
    background-color: #5cb85c;
    color: white;
    border-radius: 3px;
    cursor: pointer;
}

button:hover {
    background-color: #4cae4c;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    padding: 10px;
    border-bottom: 1px solid #ddd;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

li.completed {
    text-decoration: line-through;
    color: #888;
}
document.addEventListener('DOMContentLoaded', () => {
    const addButton = document.getElementById('add-button');
    const newItemInput = document.getElementById('new-item');
    const itemList = document.getElementById('item-list');

    addButton.addEventListener('click', () => {
        const itemText = newItemInput.value.trim();
        if (itemText !== '') {
            const li = document.createElement('li');
            li.textContent = itemText;

            const deleteButton = document.createElement('button');
            deleteButton.textContent = 'Delete';
            deleteButton.style.backgroundColor = '#d9534f';
            deleteButton.style.border = 'none';
            deleteButton.style.color = 'white';
            deleteButton.style.padding = '5px 10px';
            deleteButton.style.marginLeft = '10px';
            deleteButton.style.cursor = 'pointer';

            deleteButton.addEventListener('click', () => {
                itemList.removeChild(li);
            });

            li.appendChild(deleteButton);

            li.addEventListener('click', () => {
                li.classList.toggle('completed');
            });

            itemList.appendChild(li);
            newItemInput.value = '';
        }
    });
});
