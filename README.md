# gamestore-springboot-apirest
Proposed project for the extension of SERRATEC API REST discipline. The idea is to develop an API for a game e-commerce store.

# Espaco-Dos-Games
Continuação do Projeto Final da Disciplina de API, durante a residência do Serratec.

Construção do minimundo: 

Você foi convidado a desenvolver uma API para um novo sistema de E Commerce de uma loja chamada Espaço dos Games 
onde o usuário do tipo cliente poderá executar as seguintes ações:

* Consultar uma lista de produtos. (Autenticação = false)
* Consultar uma lista de produtos vinculada a uma categoria. (Autenticação = false)
* Consultar um produto pelo seu id. (Autenticação = false)
* Consultar uma lista de categorias. (Autenticação = false)
* Consultar uma categoria pelo id. (Autenticação = false)

* Poder cadastrar uma conta (Autenticação = false)
	* Toda conta deve conter (e-mail, senha, telefone, dataCadastro e perfil)

* Poder criar um pedido (Autenticação = true)
	*Todo pedido deve ter: Número(?id?), Cliente(usuário), Data do Pedido, Valor Total, Desconto Total,
	 Acréscimo Total e Observação.
	*Cada pedido poderá ter muitos itens.
	*Cada item poderá ter (Quantidade, Valor Unitário, Desconto, Acréscimo e Valor Total).
	*Cálculo do valor do item (valor unitário - desconto + acréscimo) * quantidade
	*Forma de Pagamento
'	*Quando o pedido for cadastrado, deve enviar um email automaticamente para o cliente informando
	 os dados do pedido. Nesse e-mail envie um layout bonitinho do tipo HTML.

Deve existir um usuário do tipo Admin
Todo usuário admin, pode fazer tudo na API.
Com o usuário admin, deve ser possível executar as seguintes ações;
	*Cadastrar uma Categoria.
'	*Atualizar uma Categoria.
	*Cadastrar um produto.
		* Todo produto deve ter (id, nome , valor, quantidade, observação)
	*Atualiar um produto.
	*Inativar produto.
	*Inativar uma categoria.
Tabela de log das alterações e inclusões feitas em produtos e categorias.
	*(id, tipo, data, valorOriginal, valorAtual, idUsuario)
Tem que ter tratamento de erro com retorno correto dos statuscode.
Extras:
	*Criar documentação no swagger.
	*Adicionar foto ao produto.


Planejamento para construção da aplicação:

Nome da Loja: Espaço dos Games.

Modelo de Dados:

Jogos: Cada jogo deve conter id, título, desenvolvedor, um gênero, uma plataforma, preço, estoque, observação e status.
Gênero: Cada gênero deve conter id, nome, descrição e status.
Usuário: Cada usuário deve ter id, nome, e-mail, senha, telefone e um endereço.
Pedidos: Cada pedido deve ter id, código, usuário, data do pedido, valor total, desconto total, acréscimo total, lista de jogos, um endereço de entrega e status (pendente, em processamento, enviado ou entregue).

EndPoints:

GET/jogos: Este endpoint deve retornar uma lista de todos os jogos ativos e inativos. (autenticação = true / autorização = ADMIN)
GET/jogos/ativos: Este endpoint deve retornar uma lista de todos os jogos ativos. (autenticação = false)
GET/jogos/inativos: Este endpoint deve retornar uma lista de todos os produtos inativos. (autenticação = true / autorização = ADMIN)
GET/jogos/{id}/generos: Este endpoint deve retornar uma lista de jogos pelo id de um gênero. (atenticação = false)
GET/jogos/{id}: Este endpoint deve retornar um jogo pelo seu id. (autenticação = false)
POST/jogos: Este endpoint deve cadastrar um jogo. (autenticação = true / autorização = ADMIN)
PUT/jogos/{id}: Este endpoint deve atualizar um jogo. (autenticação = true / autorização = ADMIN)
PUT/jogos/{id}/inativar: Este endpoint deve desativar um jogo. (autenticação = true / autorização = ADMIN)
PUT/jogos/{id}/ativar: Este endpoint deve ativar um jogo. (autenticação = true / autorização = ADMIN)

GET/generos: Este endpoint deve retornar uma lista de todos os gêneros ativos e inativos. (autenticação = true / autorização = ADMIN)
GET/generos/ativos: Este endpoint deve retornar uma lista de todos os gêneros ativos. (autenticação = false)
GET/generos/inativos: Este endpoint deve retornar uma lista de todos os gêneros inativos. (autenticação = true / autorização = ADMIN)
GET/generos/{id}: Este endpoint deve retornar um gênero pelo seu id. (autenticação = false)
POST/jogos: Este endpoint deve cadastrar um gênero. (autenticação = true / autorização = ADMIN)
PUT/jogos/{id}: Este endpoint deve atualizar um gênero. (autenticação = true / autorização = ADMIN)
PUT/jogos/{id}/inativar: Este endpoint deve desativar um gênero. (autenticação = true / autorização = ADMIN)
PUT/jogos/{id}/ativar: Este endpoint deve ativar um gênero. (autenticação = true / autorização = ADMIN)

GET/usuarios: Este endpoint deve retornar uma lista de todos os usuários ativos e inativos. (autenticação = true / autorização = ADMIN)
GET/usuarios/ativos: Este endpoint deve retornar uma lista de todos os usuários ativos. (autenticação = true / autorização = ADMIN)
GET/usuarios/inativos: Este endpoint deve retornar uma lista de todos os usuários inativos. (autenticação = true / autorização = ADMIN)
GET/usuarios/{id}: Este endpoint deve retornar um usuário pelo seu id. (autenticação = true / autorização = ADMIN
GET/usuarios/?: Este endpoint deve retornar o usuário que está utilizando a consulta. (autenticação = true)
POST/usuarios/?: Este endpoint deve cadastrar um usuário. (autenticação = false)
POST/usuarios/?: Este endpoint deve logar um usuário. (autenticação = false)
PUT/usuarios/{id}: Este endpoint deve atualizar um usuário. (autenticação = true / autorização = ADMIN)
PUT/usuarios/?: Este endpoint deve atualizar o usuário que está utilizando a consulta. (autenticação = true)
PUT/usuarios/{id}/inativar: Este endpoint deve desativar um usuário. (autenticação = true / autorização = ADMIN)
PUT/usuarios/{id}/ativar: Este endpoint deve ativar um usuário. (autenticação = true / autorização = ADMIN)

GET/pedidos: Este endpoint deve retornar um lista de todos os pedidos. (autenticação = true / autorização = ADMIN)
GET/pedidos/?: Este endpoint deve retornar uma lista de pedidos do usuário que está utilizando a consulta. (autenticação = true)
GET/pedidos/{id}: Este endpoint deve retornar um pedido pelo seu id. (autenticação = true / autorização = ADMIN)
POST/pedidos: Este endpoint deve cadastrar um pedido. (autenticação = true)
PUT/pedidos/{id}: Este endpoint deve atualizar um pedido. (autenticação = true / autorização = ADMIN)
PUT/pedidos/?: Este endpont deve atualizar um pedido do usuário que está utilizando a aplicação. (autenticação = true)

GET/logs: Este endpoint deve retornar uma lista de todos os logs. (autenticação = true / autorização = ADMIN)
GET/logs/{id}: Este endpoint deve retornar um log por id. (autenticação = true / autorização = ADMIN)
GET//logs/tipos: Este endpoint deve retornar uma lista de logs pelo tipo da alteração. (autenticação = true / autorização = ADMIN)
Modelo de dados

Implementação: JAVA.

Testes:

--- Ainda não chegou no período de testes ---

Deploy:

--- Projeto em andamento, não é possível fazer o Deploy ---
Plataformas em vista AWS, Azure ou GCP
