
# Sistema_RESILIADATA
O sistema irá auxiliar na avaliação de quais são as tecnologias que as empresas parceiras 
estão utilizando e quem são seus colaboradores.


## MODELO CONCEITUAL

<div align="center">
<img src="https://github.com/MatokoLB/Sistema_RESILIADATA/assets/112680379/0cc43304-dd4e-4d28-9451-b88806380078" width="700px"/>
</div>


## MODELO LÓGICO
<div align="center">
<img src="https://github.com/MatokoLB/Sistema_RESILIADATA/assets/112680379/8f67cfbb-0c07-4ccd-a091-18f3ec50ddaf" width="700px"/>
</div>


### PERGUNTAS SOBRE O MODELO 🐧- Tux

#### QUAIS SÃO AS ENTIDADES NECESSÁRIAS ?
- As entidades necessárias são: EMPRESA COLABORADOR e TECNOLOGIA

#### QUAIS SÃO OS PRINCIPAIS CAMPOS E SEUS RESPECTIVOS TIPOS?


#### COMO ESSAS ENTIDADES ESTÃO RELACIONADAS?
- Empresa tem colaborador:
 Relacionamento de um para muitos (1:N) entre Empresa e Colaborador. Isso significa que uma empresa pode ter vários colaboradores, mas um colaborador está associado a apenas uma empresa. 

- Empresa utiliza tecnologia:
Relacionamento de muitos para muitos (N:N) entre Empresa e Tecnologia.
Isso significa que uma empresa pode utilizar várias tecnologias e uma tecnologia pode ser utilizada por várias empresas.
Para modelar esse relacionamento uma tabela de junção (Empresa_Tecnologia) com duas chaves estrangeiras (id_empresa e id_tecnologia) formado uma chave primaria composta foi criada.

#### SIMULE 2 REGISTROS PARA CADA ENTIDADE

