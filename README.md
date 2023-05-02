<!DOCTYPE html>
<html>
<head>
	<title>Cadastro de Clientes</title>
	<meta charset="UTF-8">
	<script src="cadastro.js"></script>
</head>
<body>
	<h1>Cadastro de Clientes</h1>
	<form>
		<label>Nome: </label><input type="text" id="nome"><br>
		<label>E-mail: </label><input type="email" id="email"><br>
		<label>Telefone: </label><input type="text" id="telefone"><br>
		<label>Endereço: </label><input type="text" id="endereco"><br>
		<button type="button" onclick="cadastrarCliente()">Cadastrar</button>
	</form>
	<h2>Lista de Clientes</h2>
	<table>
		<tr>
			<th>Nome</th>
			<th>E-mail</th>
			<th>Telefone</th>
			<th>Endereço</th>
		</tr>
		<tbody id="listaClientes"></tbody>
	</table>
</body>
</html>


JavaScript:


let clientes = []

function cadastrarCliente() {
	let nome = document.getElementById("nome").value
	let email = document.getElementById("email").value
	let telefone = document.getElementById("telefone").value
	let endereco = document.getElementById("endereco").value
	
	let cliente = {
		nome: nome,
		email: email,
		telefone: telefone,
		endereco: endereco
	}
	
	clientes.push(cliente)
	
	limparCampos()
	
	atualizarListaClientes()
	
	alert("Cliente cadastrado com sucesso!")
}

function limparCampos() {
	document.getElementById("nome").value = ""
	document.getElementById("email").value = ""
	document.getElementById("telefone").value = ""
	document.getElementById("endereco").value = ""
}

function atualizarListaClientes() {
	let tabelaClientes = document.getElementById("listaClientes")
	
	tabelaClientes.innerHTML = ""
	
	for(let i = 0; i < clientes.length; i++) {
		let cliente = clientes[i]
		
		let linha = tabelaClientes.insertRow(-1)

		let colunaNome = linha.insertCell(0)
		colunaNome.textContent = cliente.nome

		let colunaEmail = linha.insertCell(1)
		colunaEmail.textContent = cliente.email

		let colunaTelefone = linha.insertCell(2)
		colunaTelefone.textContent = cliente.telefone

		let colunaEndereco = linha.insertCell(3)
		colunaEndereco.textContent = cliente.endereco
	}
}
