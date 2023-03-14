# Banco-de-Dados-Relacional
Atividades da Matéria Banco de Dados Relacional

<h1>Criando o Banco de Dados </h1>

Usamos os comandos Create para iniciarmos:

Create Database TrabalhoDeBanco

<h2>Usando a base de Dados</h2>

Use TrabalhoDeBanco

<h2>Criando as primeiras tabelas</h2>

Criamos a primeira tabela com todas as especificações acometidas em aula: 

Create table Cliente (
CodCliente INT Primary Key,
Nome VARCHAR(45) not null, 
CPF VARCHAR(45) not null,
Sexo VARCHAR(20),
Estado VARCHAR(45),
Cidade VARCHAR(45) DEFAULT 'Itapira',
Bairro VARCHAR(45),
Numero VARCHAR(45),
Rua VARCHAR(45),
TelefoneFixo VARCHAR(45) ,
TelefoneCelular VARCHAR(45)not null,
CONSTRAINT UC_Cliente unique(CPF, TelefoneCelular)
);

E a tabela Carro: 

CREATE TABLE Carro(
CodCarro INT Primary Key,
Placa VARCHAR(45),
Marca VARCHAR(45),
Modelo VARCHAR(45),
Ano VARCHAR(45),
Chassi VARCHAR(45),
Cor VARCHAR (45),
);


<h2>Criando outras tabela usando Foreign Key</h2>

Logo após fizemos as outras usando o Foreign Key para conectar elas: 

CREATE TABLE Apolice (
CodApolice INT Primary Key,
ValorCobertura DECIMAL not null,
ValorFranquia DECIMAL not null,
DataInicioVigencia DATE not null,
DataFimVigencia DATE not null,
Cliente_CodCliente INT FOREIGN KEY REFERENCES Cliente(CodCliente),
Carro_CodCarro INT FOREIGN KEY REFERENCES Carro(CodCarro),
CONSTRAINT CD_DataInicioVigencia CHECK (DataInicioVigencia <= GETDATE())
);

E por último: 

CREATE TABLE Sinistro (
CodSinistro INT,
HoraSinistro INT, 
DataSinistro DATE,
LocalSinistro VARCHAR(45),
Condutor VARCHAR(45),
Carro_CodCarro INT foreign key references Carro(CodCarro),
primary key(CodSinistro, Carro_CodCarro)
);

Por fim finalizando a tarefa. 
