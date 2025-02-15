<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quiz dos Amigos</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            text-align: center;
            padding: 20px;
        }
        .container {
            max-width: 600px;
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
            margin: auto;
        }
        .pergunta {
            font-size: 18px;
            font-weight: bold;
            margin-top: 20px;
        }
        .opcoes {
            display: flex;
            flex-direction: column;
            align-items: start;
        }
        .opcoes label {
            margin: 5px 0;
        }
        button {
            margin-top: 20px;
            padding: 10px 20px;
            font-size: 16px;
            background-color: blue;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
    </style>
</head>
<body>

    <div class="container">
        <h2>Quiz dos Amigos</h2>
        <form id="quizForm">
            <div id="perguntas"></div>
            <button type="button" onclick="mostrarRespostas()">Ver Respostas</button>
        </form>
    </div>

    <script>
        const perguntas = [
            "Quem vai ser pai primeiro?",
            "Quem vai ser o primeiro a aparecer com chifão?",
            "Quem é o mais provável de usar alguma droga?",
            "Quem ficaria bêbado primeiro?",
            "Quem tem mais chances de aparecer no jornal?",
            "Quem morreria primeiro?",
            "Quem vai se casar primeiro?",
            "Quem se envolveria em uma briga?",
            "Quem seria o primeiro a comer uma puta?",
            "Quem teria uma vida feliz?"
        ];
        
        const nomes = ["Maurício", "Fábio", "Cauã", "Mateus"];
        const perguntasDiv = document.getElementById("perguntas");

        perguntas.forEach((pergunta, index) => {
            let div = document.createElement("div");
            div.classList.add("pergunta");
            div.innerHTML = `<p>${pergunta}</p>`;
            
            let opcoesDiv = document.createElement("div");
            opcoesDiv.classList.add("opcoes");

            nomes.forEach(nome => {
                let label = document.createElement("label");
                label.innerHTML = `<input type="radio" name="pergunta${index}" value="${nome}"> ${nome}`;
                opcoesDiv.appendChild(label);
            });

            div.appendChild(opcoesDiv);
            perguntasDiv.appendChild(div);
        });

        function mostrarRespostas() {
            let respostas = [];
            perguntas.forEach((pergunta, index) => {
                let opcaoSelecionada = document.querySelector(`input[name="pergunta${index}"]:checked`);
                let resposta = opcaoSelecionada ? opcaoSelecionada.value : "Nenhum marcado";
                respostas.push(`${pergunta} -> ${resposta}`);
            });

            alert("Respostas selecionadas:\n\n" + respostas.join("\n"));
        }
    </script>

</body>
</html>
