<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Notícias sobre Violência Escolar</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
            background-color: #f9f9f9;
        }
        h1 {
            color: #333;
            text-align: center;
        }
        .noticia {
            background: white;
            padding: 15px;
            margin-bottom: 20px;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        .noticia h2 {
            margin-top: 0;
            color: #0066cc;
        }
        .noticia p {
            color: #555;
        }
        .fonte {
            font-size: 0.9em;
            color: #777;
            font-style: italic;
        }
        .busca {
            margin: 20px 0;
            text-align: center;
        }
        input, button {
            padding: 8px;
            font-size: 16px;
        }
    </style>
</head>
<body>
    <h1>Últimas Notícias sobre Violência Escolar</h1>
    
    <div class="busca">
        <input type="text" id="termoBusca" placeholder="Buscar por tema (ex: aluno, agressão)">
        <button onclick="buscarNoticias()">Buscar</button>
    </div>
    
    <div id="noticias">
        <!-- Notícias serão carregadas aqui via JavaScript -->
        <div class="noticia">
            <h2>Carregando notícias...</h2>
            <p>Se as notícias não aparecerem, verifique se há bloqueio de CORS no seu navegador.</p>
        </div>
    </div>

    <script>
        async function buscarNoticias() {
            const termo = document.getElementById('termoBusca').value.toLowerCase() || 'escola violência aluno';
            const noticiasContainer = document.getElementById('noticias');
            noticiasContainer.innerHTML = '<div class="noticia"><h2>Carregando...</h2></div>';

            // Simulação de notícias (em um caso real, você usaria uma API)
            const noticiasSimuladas = [
                {
                    titulo: 'Escola em SP registra caso de agressão entre alunos',
                    descricao: 'Um estudante foi agredido por colegas durante o recreio...',
                    fonte: 'Globo Educação',
                    link: 'https://educacao.globo.com'
                },
                {
                    titulo: 'Professores relatam aumento de violência em salas de aula',
                    descricao: 'Pesquisa mostra que 60% dos docentes já sofreram ameaças...',
                    fonte: 'Folha de São Paulo',
                    link: 'https://www.folha.com/educacao'
                }
            ];

            // Filtra notícias pelo termo digitado (simulação)
            const noticiasFiltradas = noticiasSimuladas.filter(noticia => 
                noticia.titulo.toLowerCase().includes(termo) || 
                noticia.descricao.toLowerCase().includes(termo)
            );

            // Exibe as notícias
            if (noticiasFiltradas.length > 0) {
                noticiasContainer.innerHTML = '';
                noticiasFiltradas.forEach(noticia => {
                    noticiasContainer.innerHTML += `
                        <div class="noticia">
                            <h2><a href="${noticia.link}" target="_blank">${noticia.titulo}</a></h2>
                            <p>${noticia.descricao}</p>
                            <p class="fonte">Fonte: ${noticia.fonte}</p>
                        </div>
                    `;
                });
            } else {
                noticiasContainer.innerHTML = '<div class="noticia"><h2>Nenhuma notícia encontrada.</h2></div>';
            }
        }

        // Carrega notícias ao abrir a página
        window.onload = buscarNoticias;
    </script>
</body>
</html>
