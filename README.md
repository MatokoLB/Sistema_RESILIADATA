
# 💻Sistema_RESILIADATA
O sistema irá auxiliar na avaliação de quais são as tecnologias que as empresas parceiras 
estão utilizando e quem são seus colaboradores.


## 📝MODELO CONCEITUAL

<div align="center">
<img src="https://github.com/MatokoLB/Sistema_RESILIADATA/assets/112680379/0cc43304-dd4e-4d28-9451-b88806380078" width="700px"/>
</div>


## 🕹️MODELO LÓGICO
<div align="center">
<img src="https://github.com/MatokoLB/Sistema_RESILIADATA/assets/112680379/8f67cfbb-0c07-4ccd-a091-18f3ec50ddaf" width="700px"/>
</div>


### PERGUNTAS SOBRE O MODELO 🐧- Tux

#### **QUAIS SÃO AS ENTIDADES NECESSÁRIAS ?**
As entidades necessárias são:
- 🏬EMPRESA
- 🧑‍💼COLABORADOR
- ⚛️TECNOLOGIA

#### *QUAIS SÃO OS PRINCIPAIS CAMPOS E SEUS RESPECTIVOS TIPOS* ?
###### 🏬Empresa
```
- 🔑id_empresa (int🔢): Identificador único para a empresa.
- nome (varchar🔡): Nome da empresa.
- email (varchar🔡): Email de contato da empresa.
- cnpj (varchar🔡): CNPJ da empresa.
```

###### ⚛️Tecnologia
```
- 🔑id_tecnologia (int🔢): Identificador único para a tecnologia.
- nome (varchar🔡): Nome da tecnologia.
- area (varchar🔡): Área da tecnologia.
```

###### 🧑‍💼Colaborador
```
- 🔑 id_colaborador (int🔢): Identificador único para o colaborador.
- nome (varchar🔡): Nome do colaborador.
- cpf (varchar🔡): CPF do colaborador.
- email (varchar🔡): Email do colaborador.
- 🗝️id_empresa (int🔢): Chave estrangeira associando o colaborador a uma empresa.
```

###### ∪ Tabela de Junção (Tecnologia_Empresa)
```
- 🔑id_empresa (int🔢): Chave estrangeira para a empresa.
- 🔑id_tecnologia (int🔢): Chave estrangeira para a tecnologia.
```

#### *COMO ESSAS ENTIDADES ESTÃO RELACIONADAS* ?
- 🏬Empresa tem 🧑‍💼colaborador:
 Relacionamento de um para muitos (1:N) entre Empresa e Colaborador. Isso significa que uma empresa pode ter vários colaboradores, mas um colaborador está associado a apenas uma empresa. 

- 🏬Empresa utiliza ⚛️Tecnologia:
Relacionamento de muitos para muitos (N:N) entre Empresa e Tecnologia.
Isso significa que uma empresa pode utilizar várias tecnologias e uma tecnologia pode ser utilizada por várias empresas.
Para modelar esse relacionamento uma tabela de junção (⚛️Tecnologia_Empresa🏬) com duas chaves estrangeiras (id_empresa e id_tecnologia) formado uma chave primaria composta foi criada.

#### *SIMULE 2 REGISTROS PARA CADA ENTIDADE*

##### 🧑‍💼Colaborador

id | nome | email | cpf | id_empresa 
:--------- | :------: | :-------: | :-------: | :-------:
1 | "João Silva" | "joao.silva@techinnovators.com" | "12345678900" | 1
2 | "Maria Souza" | "maria.souza@datasolutions.com" | "98265432100" | 2

---

##### 🏬Empresa

id | nome | email | cnpj
:--------- | :------: | :-------: | :-------:
1 | "Tech Innovators" | "contact@techinnovators.com" | "12345678000199"
2 | "Data Solutions" | "info@datasolutions.com" | "98765432000122"

---

##### ⚛️Tecnologia

id | nome | area
:--------- | :------: | :-------: 
1 | "Python" | "dados" 
2 | "React" | "info@datasolutions.com" 



##### ∪ Tabela de Junção (⚛️Tecnologia_Empresa🏬)

id_empresa | id_tecnologia 
:--------- | :------:  
1 | 2 
2 | 2  

#### *QUAIS OUTROS ATRIBUTOS AS ENTIDADES PODERIAM CONTER* ?

Dependendo dos requisitos do seu sistema, Podemos adicionar mais atributos para cada entidade a fim de torná-las mais completas e atender às necessidades sistema. Abaixo estão alguns exemplos de atributos adicionais para cada entidade:

<details>
 
###### 🏬Empresa
 
```
- telefone (varchar🔡): Número de telefone da empresa para contato.
- endereco (varchar🔡): Endereço físico da empresa.
- site (varchar🔡): URL do site da empresa.
- data_fundacao (date📆): Data de fundação da empresa.
- porte (varchar🔡): Tamanho ou porte da empresa (por exemplo, pequena, média, grande).
- setor (varchar🔡): Setor ou indústria em que a empresa atua.
- descricao (varchar🔡): Uma descrição breve da empresa.
```

###### ⚛️Tecnologia

```
- versao (varchar🔡): Versão específica da tecnologia usada pela empresa.
- descricao (varchar🔡): Descrição da tecnologia ou de suas características.
- data_lancamento (date📆): Data de lançamento ou criação da tecnologia.
- fabricante (varchar🔡): Fabricante ou provedor da tecnologia.
```

###### 🧑‍💼Colaborador

```
- data_contratacao (date📆): Data em que o colaborador foi contratado pela empresa.
- cargo (varchar🔡): Cargo ou função que o colaborador exerce na empresa.
- salario (decimal🔢): Salário do colaborador.
- endereco (varchar🔡): Endereço residencial do colaborador.
- data_nascimento (date📆): Data de nascimento do colaborador.
- telefone (varchar🔡): Número de telefone do colaborador.
```
</details>


### QUERRYS PODERIAM RESPONDER A QUESTÃO INICIAL
Para responder à pergunta sobre as tecnologias que as empresas parceiras estão utilizando e quem são seus colaboradores, temos que criar um script SQL para definir o banco de dados com as entidades: 🏬Empresa, ⚛️Tecnologia, 🧑‍💼Colaborador e a tabela de junção entre 🏬Empresa e ⚛️Tecnologia,em seguida criaremos suas consultas (query).

---
##### Criação do Banco de Dados e Tabelas
Nome do banco : AvaliacaoTecnologias

```
CREATE DATABASE AvaliacaoTecnologias;
USE AvaliacaoTecnologias;

CREATE TABLE Empresa (
    id_empresa INT PRIMARY KEY,
    nome VARCHAR(100),
    email VARCHAR(100),
    cnpj VARCHAR(20)
);

CREATE TABLE Tecnologia (
    id_tecnologia INT PRIMARY KEY,
    nome VARCHAR(50),
    area VARCHAR(50)
);

CREATE TABLE Colaborador (
    id_colaborador INT PRIMARY KEY,
    nome VARCHAR(100),
    cpf VARCHAR(14),
    email VARCHAR(100),
    id_empresa INT,
    FOREIGN KEY (id_empresa) REFERENCES Empresa(id_empresa)
);

CREATE TABLE Empresa_Tecnologia (
    id_empresa INT,
    id_tecnologia INT,
    PRIMARY KEY (id_empresa, id_tecnologia),
    FOREIGN KEY (id_empresa) REFERENCES Empresa(id_empresa),
    FOREIGN KEY (id_tecnologia) REFERENCES Tecnologia(id_tecnologia)
);


```


##### Script de Alimentação de Dados
```
INSERT INTO Empresa (id_empresa, nome, email, cnpj)
VALUES
    (1, 'Tech Innovators', 'contact@techinnovators.com', '12345678000199'),
    (2, 'Data Solutions', 'info@datasolutions.com', '98765432000122');

INSERT INTO Tecnologia (id_tecnologia, nome, area)
VALUES
    (1, 'Python', 'dados'),
    (2, 'React', 'webdev'),
    (3, 'SEO Tools', 'marketing');

INSERT INTO Colaborador (id_colaborador, nome, cpf, email, id_empresa)
VALUES
    (1, 'Joao Silva', '12345678900', 'joao.silva@techinnovators.com', 1),
    (2, 'Maria Souza', '98765432100', 'maria.souza@datasolutions.com', 2),
    (3, 'Carlos Mendes', '32165498700', 'carlos.mendes@techinnovators.com', 1),
    (4, 'Ana Paula', '65432198700', 'ana.paula@datasolutions.com', 2);

INSERT INTO Empresa_Tecnologia (id_empresa, id_tecnologia)
VALUES
    (1, 1), 
    (1, 2),
    (2, 3); 
```
---

##### Queries para Responder à Pergunta
Query para listar as tecnologias que as empresas estão utilizando:

```
SELECT 
    e.nome AS empresa_nome,
    t.nome AS tecnologia_nome,
    t.area AS tecnologia_area
FROM
    Empresa e
JOIN
    Empresa_Tecnologia et ON e.id_empresa = et.id_empresa
JOIN
    Tecnologia t ON et.id_tecnologia = t.id_tecnologia;

```
Essa query junta as tabelas Empresa, Empresa_Tecnologia e Tecnologia para listar as tecnologias que as empresas estão utilizando, incluindo o nome da empresa, o nome da tecnologia e a área da tecnologia.

---

##### Query para listar os colaboradores de cada empresa

```
SELECT
    e.nome AS empresa_nome,
    c.nome AS colaborador_nome,
    c.cpf AS colaborador_cpf,
    c.email AS colaborador_email
FROM
    Empresa e
JOIN
    Colaborador c ON e.id_empresa = c.id_empresa;

```
Essa query junta as tabelas Empresa e Colaborador para listar os colaboradores de cada empresa, incluindo o nome da empresa, o nome do colaborador, o CPF do colaborador e o email do colaborador.
