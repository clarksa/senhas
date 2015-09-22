# senhas
Projeto de Senhas

1.	Banco de Dados utilizado
postgresql-9.4.4-3

2.	Funções de Banco
2.2.	 Criar banco de dados no postgresql
•	Nome: senhas
•	Owner: postgres

-- Database: senhas

-- DROP DATABASE senhas;

CREATE DATABASE senhas
  WITH OWNER = postgres
       ENCODING = 'UTF8'
       TABLESPACE = pg_default
       LC_COLLATE = 'Portuguese_Brazil.1252'
       LC_CTYPE = 'Portuguese_Brazil.1252'
       CONNECTION LIMIT = -1;

3.	Usuário
•	User: gerente
•	Senha: 123
-- Role: gerente

-- DROP ROLE gerente;

CREATE ROLE gerente LOGIN
  ENCRYPTED PASSWORD 'md5ab087a8753d654a17b633081a21acac7'
  SUPERUSER INHERIT CREATEDB CREATEROLE REPLICATION;


4.	Criar Tabela

-- Table: senhas

-- DROP TABLE senhas;

CREATE TABLE senhas
(
  id numeric NOT NULL,
  status boolean,
  tipo character(1), -- P - Prioritaria, N - Normal
  senha numeric(4,0) NOT NULL,
  senhachamada boolean DEFAULT false,
  CONSTRAINT pk_senhas PRIMARY KEY (id)
)
WITH (
  OIDS=FALSE
);
ALTER TABLE senhas
  OWNER TO postgres;
COMMENT ON COLUMN senhas.tipo IS 'P - Prioritaria, N - Normal';

5.	Utilizar Tomcat 8
6.	Parar o service do Tomcat 8
7.	Colocar o arquivo senhas.war na pasta 

•	C:\Program Files\Apache Software Foundation\Tomcat 8.0\webapps

8.	Iniciar o service Tomcat 8
9.	Copiar para a pasta abaixo o arquivo postgresql-9.4-1203.jdbc4.jar
•	C:\Program Files\Apache Software Foundation\Tomcat 8.0\webapps\senhas\WEB-INF\lib

10.	Porta do Tomcat é a 8080
11.	Links da página para acesso
http://localhost:8080/senhas/cliente.html
http://localhost:8080/senhas/gerente.html
http://localhost:8080/senhas/painel.html

Serão apresentadas 3 telas, onde:
A tela do Cliente é para solicitar senhas
A tela do Gerente é para o gerente chamar senhas e reiniciar as senhas
A tela do Painel apresenta a senha chamada pelo gerente

