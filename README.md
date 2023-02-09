# BANCOS-DE-DADOS
BANCO DE DADOS ADS 2 PERIODO
CREATE TABLE JOGADORES(/*comandos para criar uma tabela*/
ID_JOGADOR NUMBER(10,0) NOT NULL,/*comandos para criar um bloco para a tabela determinando que sera um numero, tera até 10 posicoes e sera obrigatorio*/
NOME VARCHAR2 (100) NOT NULL,/*comandos para criar um bloco para a tabela determinando que sera um texto, tera até 100 posicoes e sera obrigatorio*/
POSICAO VARCHAR2(100)/*comandos para criar um bloco para a tabela determinando que sera um texto, tera até 100 posicoes, porem pode ser nulo*/
BI VARCHAR2(100),/*comandos para criar um bloco para a tabela determinando que sera um texto, tera até 100 posicoes, porem pode ser nulo*/
CONSTRAINT/*regras para que os campos sejam obrigatorios, e não repitam */PK_JOGADORES /*nome designado para a regra*/PRIMARY KEY/*nome da regra*/(ID_JOGADOR) /*campo que sera aplicado a regra*/
);

CREATE TABLE CONTRATADOS(/*criação de nova tabela que fara referência ao campo ID_JOGADOR*/
ID_JOGADOR NUMBER(10,0)NOT NULL,/*criando ligação da nova tabela com a tabela ID_JOGADOR*/
DATA_INICIOS DATE NOT NULL,
DATA_FIMS DATE NOT NULL,
CONSTRAINT PK_CONTRATADOS  /*regra pra a data_inicio não ser maior que a data_fim*/
CONSTRAINT FK_CONTRATADOS_REF_JOGADOR FOREIGN KEY(ID_JOGADOR)/*regra para manter a integridade dos dados,e criar referência da tabela contratado com a tabela jogador*/
REFERENCES JOGADORES/*criando referencia com a tabela jogador*/(ID_JOGADOR),/*ja criado referencia para a tabela jogador criando referencia ao campo id_jogador*/
CONSTRAINT CK_CONTRATADOS CHECK(DATA_FIMS > DATA_INICIOS)/*regra validador para não permitir que a data_fim seja menor que a data_inicio*/
);

*/ ALTER TABLE JOGADORES RENAME TO JOGADOREEEEEEEEEEEEEES;/*alterar nome de tabela*/
ALTER TABLE JOGADOREES RENAME TO JOGADORES;/*alterar nome de tabela*/

ALTER TABLE JOGADORES ADD APELIDO VARCHAR2(30);/*adicionando novos campos a tabela*/

ALTER TABLE JOGADORES RENAME COLUMN APELIDO TO NICKNAME;/*alterando nome coluna*/

DESC JOGADORES;/*mostrar estrutura da tabela*/

ALTER TABLE JOGADORES MODIFY POSICAO NUMBER(5,0)/*modificar tipo da coluna*/

DROP TABLE JOGADORES;/*exclui tabela,caso esteja relacionado a outra tabela,precisa antes excluir a tabela associada e depois a tabela principal*/

ALTER TABLE CONTRATADO DROP CONSTRAINT FK_CONTRATADOS_REF_JOGADOR;/*excluir referenciação de tabelas*/

ALTER TABLE CONTRATADOS
DISABLE CONSTRAINT FK_CONTRATADOS_REF_JOGADOR;/*desabilitar referenciação de tabelas*/ 

ALTER TABLE CONTRATADOS ENABLE CONSTRAINT FK_CONTRATADOS_REF_JOGADOR;/*Habilitar referenciação de tabelas*/ 
