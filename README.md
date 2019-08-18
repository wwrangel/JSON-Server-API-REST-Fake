# JSON-Server-API-REST-Fake
Json Server - Criando uma API REST fake

É uma biblioteca capaz de criar uma API Fake em 30 segundos e sem precisar escrever  nenhuma linha de código.

Passo a passo para simular uma API

1 – Começando com JSON Server: 

Instalação
<n>npm install -g json-server</n>

Criando o arquivo de banco de dados
Crie um arquivo de nome db.json numa pasta do seu computador (para o teste pode usar o arquivo aqui disponibilizado).


Iniciando o servidor
Agora é só rodar o comando abaixo e seu servidor estará iniciado. Lembrando que por padrão a API vai funcionar no enderço: http://localhost:3000
json-server --watch db.json

2 – Rotas
As rotas definem como você vai acessar a API.
As rotas são:
Request	URL		Detalhes
GET		/produtos	Busca todos os produtos
GET		/produtos/1	Busca um produto
POST		/produtos	Salva um produto
PUT		/produtos/1	Atualiza dos os dados do produto
PATCH		/produtos/1	Atualiza parte dos dados do produto
DELETE	/produtos/1	Remove um produto

As rotas são compostas pelo endereço base (localhost:3000) mais o recurso que você quer acessar com por exemplo “produtos”.
Para executar os requests dos exemplos abaixo você pode usar a ferramenta Postman (https://www.getpostman.com/) ou alguma outra de sua preferencia.
Para ver os resultados na pratica assista o vídeo acima ou execute os exemplos no seu computador.

Exemplos:
Exemplo 1: Buscar todos os produtos
Dados de envio
GET http://localhost:3000/produtos/
Content-Type: application/json
Retorno : Lista tudo

Exemplo 2: Buscar apenas um produtos
Dados de envio
GET http://localhost:3000/produtos/1
Content-Type: application/json
Retorno : Só registro com ID 1
Exemplo 3: Salvar um registro
Dados de envio
POST http://localhost:3000/produtos/
Content-Type: application/json
{
    "nome": "Hambúrguer de frango",
    "descricao": "Pão, bife de hambúrguer 90g de frango, salada e batata.",
    "preco": 9.5,
    "categoria_id": 1
}

Retorno : Registro recém criado


Exemplo 4: Alterar um produto
Dados de envio
PUT http://localhost:3000/produtos/1
Content-Type: application/json
{
    "nome": "Hambúrguer de frango",
    "descricao": "Pão, bife de hambúrguer 90g de frango, salada e batata.",
    "preco": 10.5,
    "categoria_id": 1
}

Retorno : Registro recém alterado


Exemplo 5: Alterar apenas o nome de um produto
Dados de envio
PATCH http://localhost:3000/produtos/1
Content-Type: application/json
{
    "nome": "Hambúrguer de frango artezanal"
}

Retorno : Registro recém alterado


Exemplo 6: Excluir um produto
Dados de envio
DELETE http://localhost:3000/produtos/1
Content-Type: application/json
Retorno : Status: 200 OK


3 – Filtros
Para executar usar o nome das propriedades do objeto que você quer pesquisar.
No exemplo abaixo estou pesquisando por produtos que o nome é “X-Búrguer”
Dados de envio
GET http://localhost:3000/produtos?nome=X-Búrguer
Content-Type: application/json

Retorno : Registro com os dados do filtro

4 – Paginação
Para paginação usar o parâmetro “_page” e por padrão cada página terá 10 itens. Para alterar a quantidade de itens por página, usar o parâmetro “_limit”.
No exemplo abaixo vou buscar a página 1 e quero 2 itens por página.

Dados de envio
GET http://localhost:3000/produtos/?_page=1&amp;_limit=2
Content-Type: application/json

Retorno : Lista com n registros por página.

5 – Ordenação
Para ordenar usar os parâmetros “_sort” para informar qual campo vai sofrer a ordenação e “_order” para definir se ascendente ou descendente. Lembrando que é possível ordenar por mais de um campo.
O exemplo abaixo ordena por por nome e em ordem descendente.

Dados de envio
GET http://localhost:3000/produtos/?_sort=nome&amp;_order=desc
Content-Type: application/json

Retorno: Registros ordenados conforme parâmetro.

Referencias
JSON Server: https://github.com/typicode/json-server
Postman: https://www.getpostman.com/
Fábrica de Código: http://www.fabricadecodigo.com/json-server/
