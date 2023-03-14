<h1>EX001</h1>
<h3>Como foi criado o banco</h3>
<ul>
<li>Inicialmente criamos um novo banco de dados com um nome de nossa escolha, apos isso criamos uma querry com nosso GBD
<li>Criamos as tabelas Cliente, Carro, Apolice e Sinistro seguindo as regras de negocio
<li>Inserimos as colunas que devem ser criadas dentro das tabelas e seus respectivos tipos
<li>Definimos os valores que devem ser inseridos como "NOT NULL"
<li>Definimos as chaves primarias
<li>Criamos uma CONSTRAINT para defini ro uso de duas chaves primarias
<li>OBS... Utilizamos o comando DEFAULT para definir um dado para "Cidade"
</li>
USE "Nome do Banco de Dados"<br>
<hr>
<h2>Criação da tabela Cliente</h2>
<hr>
CREATE TABLE Cliente (<br>
    CodCliente INT PRIMARY KEY,<br>
    Nome VARCHAR(45),<br>
    CPF VARCHAR(45) NOT NULL UNIQUE,<br>
    Sexo VARCHAR(20),<br>
    Estado VARCHAR(45),<br>
    Cidade VARCHAR(45) DEFAULT 'ITAPIRA',<br>
    Bairro VARCHAR(45),<br>
    Numero VARCHAR(45),<br>
    Rua VARCHAR(45),<br>
    TelefoneFixo VARCHAR(45),<br>
    TelefoneCelular VARCHAR(45) NOT NULL<br>
);<br>
<hr>
<h2>Criação da tabela Carro</h2>
<hr>
CREATE TABLE Carro (<br>
    CodCarro INT PRIMARY KEY,<br>
    Placa VARCHAR(45) NOT NULL,<br>
    Marca VARCHAR (45) NOT NULL,<br>
    Modelo VARCHAR(45) NOT NULL,<br>
    Ano VARCHAR(45) NOT NULL,<br>
    Chassi VARCHAR(45) NOT NULL,<br>
    Cor VARCHAR(45)<br><br>
	);<br>
<hr>
<h2>Criação da tabela Apolice</h2>
<hr>
CREATE TABLE Apolice (<br>
    CodApolice INT PRIMARY KEY NOT NULL,<br>
    ValorCobertura DECIMAL NOT NULL,<br>
    ValorFranquia DECIMAL  NOT NULL,<br>
    DataInicioVigencia DATE CHECK (DataInicioVigencia > getDate())NOT NULL,<br>
    DataFimVigencia DATE NOT NULL,<br>
    Cliente_CodCliente INT REFERENCES Cliente(CodCliente),<br>
    Carro_CodCarro INT REFERENCES Carro(CodCarro),<br>
);<br>
<hr>
<h2>Criação da tabela Sinistro</h2>
<hr>
CREATE TABLE Sinistro (<br>
    CodSinistro INT,<br>
    HoraSinistro INT,<br>
    DataSinistro DATE,<br>
    LocalSinistro VARCHAR(45),<br>
    Condutor VARCHAR(45),<br>
    Carro_CodCarro INT,<br>
	
   CONSTRAINT pk_Sinistro PRIMARY KEY(CodSinistro, Carro_CodCarro),<br>
   CONSTRAINT fk_Sinistro FOREIGN KEY (Carro_CodCarro) REFERENCES Carro(CodCarro), 
);
<hr>
