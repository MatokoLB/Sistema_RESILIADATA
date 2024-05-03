
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






