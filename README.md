# prova-dom-II
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Minhas Notas</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #e0f2f7; 
            display: flex;
            justify-content: center;
            align-items: flex-start; 
            min-height: 100vh;
            margin: 0;
            padding: 20px;
            box-sizing: border-box; 
        }

        .container {
            background-color: #ffffff;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
            width: 100%;
            max-width: 600px; 
            margin-top: 50px; 
        }

        h1 {
            text-align: center;
            color: #263238; 
            margin-bottom: 25px;
        }

        .input-section {
            display: flex;
            gap: 10px; 
            margin-bottom: 30px;
            flex-wrap: wrap; 
        }

        #note-input {
            flex-grow: 1; 
            padding: 12px 15px;
            border: 1px solid #b0bec5; 
            border-radius: 5px;
            font-size: 1rem;
            box-sizing: border-box; 
            min-width: 150px; 
        }

        #add-note-btn {
            background-color: #4CAF50; 
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1rem;
            transition: background-color 0.3s ease;
            flex-shrink: 0; 
        }

        #add-note-btn:hover {
            background-color: #45a049; 
        }

        .notes-list {
            list-style: none;
            padding: 0;
        }

        .note-item {
            background-color: #f5f5f5;
            border: 1px solid #eceff1;
            padding: 15px 20px;
            margin-bottom: 10px;
            border-radius: 5px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            word-wrap: break-word; 
        }

        .note-text {
            flex-grow: 1;
            margin-right: 15px; 
            color: #37474f; 
        }

        .delete-btn {
            background-color: #f44336; 
            color: white;
            border: none;
            padding: 8px 12px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 0.9rem;
            transition: background-color 0.3s ease;
            flex-shrink: 0;
        }

        .delete-btn:hover {
            background-color: #da190b; 
        }

       
        (max-width: 480px) {
            .container {
                padding: 20px;
                margin-top: 20px;
            }

            .input-section {
                flex-direction: column; 
                gap: 15px;
            }

            {
                width: 100%; 
            }

            .note-item {
                flex-direction: column; 
                align-items: flex-start;
                gap: 10px;
            }

            .note-text {
                margin-right: 0;
                margin-bottom: 5px;
            }

            .delete-btn {
                width: 100%; 
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Minhas Anotações</h1>
        <div class="input-section">
            <input type="text" id="note-input" placeholder="Digite sua nota aqui...">
            <button id="add-note-btn">Adicionar Nota</button>
        </div>
        <ul id="notes-list" class="notes-list">
            </ul>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const noteInput = document.getElementById('note-input');
            const addNoteBtn = document.getElementById('add-note-btn');
            const notesList = document.getElementById('notes-list');

         
            addNoteBtn.addEventListener('click', () => {
                const noteText = noteInput.value.trim(); 
                if (noteText !== '') { // Só adiciona se o texto não estiver vazio
                    const listItem = document.createElement('li');
                    listItem.classList.add('note-item');

                    const noteContent = document.createElement('span');
                    noteContent.classList.add('note-text');
                    noteContent.textContent = noteText;

                    const deleteButton = document.createElement('button');
                    deleteButton.classList.add('delete-btn');
                    deleteButton.textContent = 'Excluir';

                  
                    deleteButton.addEventListener('click', () => {
                        notesList.removeChild(listItem);
                    });

                    listItem.appendChild(noteContent);
                    listItem.appendChild(deleteButton);
                    notesList.appendChild(listItem);

                    noteInput.value = ''; 
                    noteInput.focus(); 
                }
            });

          
            noteInput.addEventListener('keypress', (event) => {
                if (event.key === 'Enter') {
                    addNoteBtn.click(); 
                }
            });
        });
    </script>
</body>
</html>
