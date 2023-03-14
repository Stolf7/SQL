<h1>EX001</h1>

USE Nome do Banco de Dados<br>
<h2>Criação da tabela Cliente</h2>
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
<h2>Criação da tabela Carro</h2>
CREATE TABLE Carro (<br>
    CodCarro INT PRIMARY KEY,<br>
    Placa VARCHAR(45) NOT NULL,<br>
    Marca VARCHAR (45) NOT NULL,<br>
    Modelo VARCHAR(45) NOT NULL,<br>
    Ano VARCHAR(45) NOT NULL,<br>
    Chassi VARCHAR(45) NOT NULL,<br>
    Cor VARCHAR(45)<br><br>
	);<br>
<h2>Criação da tabela Apolice</h2>
CREATE TABLE Apolice (<br>
    CodApolice INT PRIMARY KEY NOT NULL,<br>
    ValorCobertura DECIMAL NOT NULL,<br>
    ValorFranquia DECIMAL  NOT NULL,<br>
    DataInicioVigencia DATE CHECK (DataInicioVigencia > getDate())NOT NULL,<br>
    DataFimVigencia DATE NOT NULL,<br>
    Cliente_CodCliente INT REFERENCES Cliente(CodCliente),<br>
    Carro_CodCarro INT REFERENCES Carro(CodCarro),<br>
);<br>
<h2>Criação da tabela Sinistro</h2>
CREATE TABLE Sinistro (<br><br>
    CodSinistro INT,<br>
    HoraSinistro INT,<br>
    DataSinistro DATE,<br>
    LocalSinistro VARCHAR(45),<br>
    Condutor VARCHAR(45),<br>
    Carro_CodCarro INT,<br>
	
   CONSTRAINT pk_Sinistro PRIMARY KEY(CodSinistro, Carro_CodCarro),<br>
   CONSTRAINT fk_Sinistro FOREIGN KEY (Carro_CodCarro) REFERENCES Carro(CodCarro), <br>

);
