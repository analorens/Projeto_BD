# Projeto do Banco de Dados Help(v1.0)

## Professor
Marco Paulo Soares Gomes

## Integrantes
Ana Cecília Souza Lorens

Álvaro Félix da Silva

Augusto Henrique Gonçalves Valbonetti

Leonardo Andrade Caetano Dornelas

Vitor Martins Gonçalves

Walker Junio Gonzaga Rocha

## Resumo
O presente relatório apresenta o projeto do banco de dados SAM (Sistema Acadêmico de Matrícula). Especificamente, o relatório apresenta o resultado das atividades de especificação do minimundo, análise de requisitos,
projeto conceitual, projeto lógico e projeto físico do SAM versão 1.0 (v1.0). As informações necessárias para a realização das atividades de modelagem foram coletadas a partir de especificações textuais fornecidas pelo usuário
final. O banco de dados SAM (v1.0) foi concebido dentro do paradigma relacional utilizando como base o modelo
relacional, sendo constituído por um conjunto de cinco entidades, cinco relacionamentos e uma média de quatro
atributos por entidade. Além disso, as entidades e relacionamentos conceituais deram origem a um esquema de
implementação composto por sete tabelas e sete restrições de integridade referencial entre elas. Fisicamente, o
banco de dados é composto por sete arquivos indexados com índice em cada um dos campos correspondentes às
chaves primárias das tabelas de origem. Adicionalmente, existem índices para cada uma das chaves estrangeiras
para acelerar o processamento de transações sobre os arquivos.
## 1 Introdução

Instituições de ensino de apoio pedagógico precisam manter seus registros organizados e atualizados a fim de dar suporte a alunos e professores na execução de suas atividades de aprendizagem. A escolha da abordagem de banco de dados utilizada para organização e manutenção desses registros acadêmicos influencia a efetividade com
que as atividades são desenvolvidas. O objetivo do presente trabalho é propor um projeto de banco de dados para um sistema acadêmico de aulas especializadas que pode ser utilizado por diversas escolas de apoio pedagógico particular para gerenciar seus processos de matrícula de alunos em turmas e planos de aulas. Particularmente, propõe-se uma especificação de minimundo, análise de requisitos, projeto conceitual, projeto lógico e projeto físico do banco de dados, utilizando como base o modelo relacional e podendo ser implementado em sistemas gerenciadores de banco de dados (SGBD) relacionais comerciais.
A Seção 2 apresenta a especificação de minimundo do babco de dados, incluindo uma descrição textual das
principais características e restrições de dados. A Seção 3 apresenta o projeto conceitual do banco de dados, incluindo
diagrama entidade-relacionamento (ER) que representa de forma gráfica as principais definições conceituais, próximas à forma como os usuários percebem o banco de dados. A Seção 4 apresenta o projeto lógico do banco de dados,
incluindo diagrama relacional que representa de forma gráfica as principais definições para implementação do banco
de dados dentro do paradigma relacional.

## 2 Especificação do Minimundo
Em modelagem de banco de dados, um minimundo é a representação simplificada e bem delimitada de uma parte específica do mundo real, recortada para atender ao objetivo de um sistema. Em vez de espelhar toda a realidade, o minimundo seleciona apenas as entidades, relacionamentos e atributos relevantes para o projeto, deixando claro o escopo do que será armazenado e utilizado pela aplicação. Essa delimitação evita incluir informações desnecessárias, reduz a sobrecarga de dados e torna o modelo mais objetivo, consistente e funcional. O minimundo deste projeto descreve um sistema acadêmico para gerenciamento de alunos, responsáveis, professores, planos, turmas/disciplinas e aulas nas modalidades Reforço, Inglês, Pré-ENEM e Pré-CEFET.

O _'Aluno'_ possui nome; ao adquirir um plano, passa a ter também CPF, ENDEREÇO, BAIRRO, COMPLEMENTO, CEP, CIDADE/ESTADO, NÚMERO DE CONTRATO, EMAIL, STATUS e DETALHES DO PLANO. Todo aluno deve possuir responsável legal; uma mesma pessoa pode acompanhar vários alunos. Quando maior de idade, o próprio aluno assume essa função. Os dados do _'Responsável legal'_ — -(identificação e contato)-* — são mantidos para o vínculo.

As _'Aulas'_ são eventos agendados que registram HORA DE ÍNICIO, HORA DE FIM, DURAÇÃO, MODALIDADE (individual ou em grupo), -(DATA)-*,  OBSERVAÇOES, INDICADOR DE AULA REALIZADA, o PROFESSOR QUE MINISTROU e a TURMA. A modalidade _'Reforço'_ é sempre individual porém o aluno participa através de uma _'Turma'_ e associa uma matéria específica e agendamentos pontuais. Na modalidade _'Inglês'_, além dos campos gerais, registram-se o CONTEUDO ABORDADO, a TURMA QUE RECEBEU A AULA, o DEVER DE CASA e o CONTEUDO PREVISTO PARA PRÓXIMA AULA. As modalidades _'Pré-ENEM'_ e _'Pré-CEFET'_ podem ser resumidas a uma única entidade _'Preparatória'_ na qual possui TIPO(sendo Pré-CEFET ou Pré-ENEM), DISCIPLINA e TURMA.

Os _'Planos'_ definem regras acadêmicas e financeiras: MODALIDADE ATENDIDA , FREQUÊNCIA SEMANAL DE AULAS, FORMATO (em grupo ou individual), exigência de TAXA DE MATRICULA, POLÍTICAS DE DESCONTO, DADOS DE VENCIMENTO e VALOR DO CURSO. Um aluno pode ter vários planos ao longo do tempo, mas apenas um plano ativo por CURSO, e que determina suas condições de participação no período vigente respectivo àquele curso. Um aluno pode participar de diferentes tipos de aula ao longo do tempo, conforme sua necessidade e plano.

O _'Professor'_ mantém CPF, RG, ENDEREÇO, ESPECIALIZAÇOES e DADOS BANCÁRIOS. Há dois TIPOS DE REGIMES de contrato: clt e horista. Todo contrato tem DATA DE INÍCIO; no regime clt também há DATA DE FIM (o horista não possui, por natureza, término fixo, sendo regido por carga horária e demandas). Professores ministram aulas conforme suas ESPECIALIZAÇÕES .

Em síntese, este minimundo restringe-se à gestão dos atores (aluno, responsável, professor), das ofertas acadêmicas (planos, turmas, disciplinas) e da operação diária (aulas e seus registros), com escopo claro para suportar matrículas, agendamentos, acompanhamento pedagógico sem extrapolar para processos externos ao ambiente acadêmico definido.



## 3 Projeto Conceitual
Essa seção apresenta o projeto conceitual da Help, descrevento as principais estruturas e restrições conceituais
do nanco de dados. Particularmente, a Figura 1 apresenta o diagrama entidade-relacionamento (ER) do modelo
conceitual da Help.

<img width="2769" height="1177" alt="Escola - PCD II-Página-3 drawio" src="https://github.com/user-attachments/assets/bb1243e4-d196-4651-85c6-1f2ec4ab12e4" />

Figura 1: Diagrama ER do modelo conceitual do banco de dados Help
Adicionalmente, a Tabela 2 apresenta com mais detalhes os elementos descritos no diagrama apresentados
na Figura 1. Na Tabela 2, podemos observar que foram identificadas na descrição textual do minimundo cinco
entidades, com uma média de quatro atributos por entidade. Além disso, foram identificados cinco relacionamentos
entre entidades, bem como suas respectivas restrições de cardinalidade, e três restrições de totalidade presentes em
três relacionamentos diferentes.
3
## 4 Projeto Lógico
Essa seção apresenta o projeto lógico do banco de dados SAM (v1.0), descrevento as principais estruturas e restrições
lógicas baseadas no modelo de implementação relacional. Particularmente, a Figura 2 apresenta o diagrama relacional
do banco de dados, mapeado a partir do modelo conceitual descrito na Seção 3 do presente relatório.
CURSO
Sigla Nome Horas Custo Area
AREA
Sigla Nome SuperArea
MODULO
Sigla Nome Curso
TOPICO
Modulo Sigla Nome Horas
MATRICULA
Curso Aluno Data Pago
ALUNO
CPF Nome Sobrenome Sexo DataNasc
PROFESSOR
Curso CPF Nome
Figura 2: Diagrama do modelo de implementação relacional do SAM (v1.0)
Na Figura 2, podemos observar que foram mapeadas sete relações, com uma média de aproximadamente
quatro atributos por relação. Além disso, foram identificados sete referências entre relações. O diagrama relacional
apresentado na Figura 2 é muito útil para visualizar de maneira simples e compacta as relações, atributos e restrições
de chave e integridade referencial presentes no banco de dados, independentemente do SGBD relacional comercial
a ser adotado para sua implementação. O detalhamento de outros tipos de estruturas e restrições sobre dados são
dependentes do SGBD relacional comercial a ser adotado.
Além do modelo de dados, uma importante decisão a ser tomada no projeto lógico de um banco de dados é
a escolha da abordagem e da solução de banco de dados a serem adotadas. Particularmente, para implementação do
SAM (v1.0) adotaremos a abordagem baseada em SGBD relacional e a solução comercial MySQL. A Figura 3 apresenta
o EER do modelo de implementação relacional do SAM (v1.0), incluindo restrições de chave, representadas como uma
figura amarela de chave ao lado esquerdo do rótulo do atributo, tipo, apresentada ao lado direito do rótulo do atributo,
nulidade, representada como um losango ao lado esquerdo do rótulo do atributo (losango branco para NULL e azul
para NOT NULL), e integridade referencial, com losango vermelho representado chaves estrangeiras.
5
Figura 3: EER do modelo de implementação relacional do SAM (v1.0)
6
## 5 Conclusão
O presente relatório apresentou o projeto do banco de dados SAM (v1.0) para um sistema acadêmico de matrícula que,
em sua versão 1.0, pode ser utilizado por diversas instituições de ensino para gerenciar seus processos de matrícula
de alunos em cursos. Especificamente, propusemos uma especificação de minimundo e apresentamos os requisitos
funcionais e operacionais, o projeto conceitual, lógico e físico do banco de dados, concebido no paradigma relacional
e projetado para ser implementado em um SGBD relacional comercial.
7
6 Anexos: Scripts de Banco de Dados
Scripts de Criação de Tabelas
-- MySQL Script generated by MySQL Workbench
-- Wed Apr 8 08:32:55 2020
-- Model: New Model Version: 1.0
-- MySQL Workbench Forward Engineering
SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0;
SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0;
SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='TRADITIONAL,ALLOW_INVALID_DATES';
DROP SCHEMA IF EXISTS `SAM` ;
CREATE SCHEMA IF NOT EXISTS `SAM` DEFAULT CHARACTER SET utf8 ;
USE `SAM` ;
DROP TABLE IF EXISTS `Aluno` ;
DROP TABLE IF EXISTS `Area` ;
DROP TABLE IF EXISTS `Curso` ;
DROP TABLE IF EXISTS `Matricula` ;
DROP TABLE IF EXISTS `Modulo` ;
DROP TABLE IF EXISTS `Professor` ;
DROP TABLE IF EXISTS `Topico` ;
CREATE TABLE IF NOT EXISTS `Aluno` (
`CPF` CHAR(11) NOT NULL,
`Nome` VARCHAR(150) NOT NULL,
`Sobrenome` VARCHAR(80) NOT NULL,
`Sexo` CHAR(1) NOT NULL,
`DataNasc` DATE)
ENGINE = InnoDB;
CREATE TABLE IF NOT EXISTS `Area` (
`Sigla` CHAR(8) NOT NULL,
`Nome` VARCHAR(120) NOT NULL,
`SuperArea` CHAR(8) NULL)
ENGINE = InnoDB;
CREATE TABLE IF NOT EXISTS `Curso` (
`Sigla` CHAR(8) NOT NULL,
`Nome` VARCHAR(250) NOT NULL,
`Horas` INT NULL,
`Custo` DECIMAL(12,2) NOT NULL,
`Area` CHAR(8) NOT NULL)
ENGINE = InnoDB;
CREATE TABLE IF NOT EXISTS `Matricula` (
`Curso` CHAR(8) NOT NULL,
`Aluno` CHAR(11) NOT NULL,
`Data` DATE NOT NULL,
`Pago` TINYINT NOT NULL DEFAULT 0)
8
ENGINE = InnoDB;
CREATE TABLE IF NOT EXISTS `Modulo` (
`Sigla` CHAR(8) NOT NULL,
`Nome` VARCHAR(250) NOT NULL,
`Curso` CHAR(8) NOT NULL)
ENGINE = InnoDB;
CREATE TABLE IF NOT EXISTS `Professor` (
`Curso` CHAR(8) NOT NULL,
`CPF` CHAR(11) NOT NULL,
`Nome` VARCHAR(250) NOT NULL)
ENGINE = InnoDB;
CREATE TABLE IF NOT EXISTS `Topico` (
`Modulo` CHAR(8) NOT NULL,
`Sigla` CHAR(3) NOT NULL,
`Nome` VARCHAR(250) NOT NULL,
`Horas` INT NOT NULL)
ENGINE = InnoDB;
SET SQL_MODE=@OLD_SQL_MODE;
SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS;
SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS;
Scripts de Criação de Restrições
-- MySQL Script generated by MySQL Workbench
-- Wed Apr 8 08:32:55 2020
-- Model: New Model Version: 1.0
-- MySQL Workbench Forward Engineering
SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0;
SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0;
SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='TRADITIONAL,ALLOW_INVALID_DATES';
USE `SAM`;
ALTER TABLE `Aluno` ADD CONSTRAINT `PK_Curso` PRIMARY KEY (`CPF`);
ALTER TABLE `Area` ADD CONSTRAINT `PK_Area` PRIMARY KEY (`Sigla`);
ALTER TABLE `Curso` ADD CONSTRAINT `PK_Curso` PRIMARY KEY (`Sigla`);
ALTER TABLE `Matricula` ADD CONSTRAINT `PK_Matricula` PRIMARY KEY (`Curso`, `Aluno`);
ALTER TABLE `Modulo` ADD CONSTRAINT `PK_Modulo` PRIMARY KEY (`Sigla`);
ALTER TABLE `Professor` ADD CONSTRAINT `PK_Professor` PRIMARY KEY (`Curso`, `CPF`);
ALTER TABLE `Topico` ADD CONSTRAINT `PK_Topico` PRIMARY KEY (`Modulo`,`Sigla`);
ALTER TABLE `Area` ADD CONSTRAINT `FK_Area_Area`
FOREIGN KEY (`SuperArea`)
REFERENCES `Area` (`Sigla`)
ON DELETE SET NULL
ON UPDATE CASCADE;
ALTER TABLE `Curso` ADD CONSTRAINT `FK_Curso_Area`
9
FOREIGN KEY (`Area`)
REFERENCES `Area` (`Sigla`)
ON DELETE RESTRICT
ON UPDATE CASCADE;
ALTER TABLE `Matricula` ADD CONSTRAINT `FK_Matricula_Curso`
FOREIGN KEY (`Curso`)
REFERENCES `Curso` (`Sigla`)
ON DELETE RESTRICT
ON UPDATE CASCADE;
ALTER TABLE `Matricula` ADD CONSTRAINT `FK_Matricula_Aluno`
FOREIGN KEY (`Aluno`)
REFERENCES `Aluno` (`CPF`)
ON DELETE CASCADE
ON UPDATE CASCADE;
ALTER TABLE `Modulo` ADD CONSTRAINT `FK_Modulo_Curso`
FOREIGN KEY (`Curso`)
REFERENCES `Curso` (`Sigla`)
ON DELETE CASCADE
ON UPDATE CASCADE;
ALTER TABLE `Professor` ADD CONSTRAINT `FK_Professor_Curso`
FOREIGN KEY (`Curso`)
REFERENCES `Curso` (`Sigla`)
ON DELETE CASCADE
ON UPDATE CASCADE;
ALTER TABLE `Topico` ADD CONSTRAINT `FK_Topico_Modulo`
FOREIGN KEY (`Modulo`)
REFERENCES `Modulo` (`Sigla`)
ON DELETE CASCADE
ON UPDATE CASCADE;
SET SQL_MODE=@OLD_SQL_MODE;
SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS;
SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS;
Scripts de Criação de Restrições (Gatilhos)
-- MySQL Script generated by MySQL Workbench
-- Wed Apr 8 08:32:55 2020
-- Model: New Model Version: 1.0
-- MySQL Workbench Forward Engineering
SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0;
SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0;
SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='TRADITIONAL,ALLOW_INVALID_DATES';
DELIMITER $$
USE `SAM`$$
10
DROP TRIGGER IF EXISTS `Aluno_BEFORE_UPDATE` $$
USE `SAM`$$
CREATE DEFINER = CURRENT_USER TRIGGER `SAM`.`Aluno_BEFORE_UPDATE` BEFORE UPDATE ON `Aluno` BEGIN
IF NEW.Sexo = 'f' THEN
SET NEW.Sexo = 'F';
ELSEIF NEW.Sexo = 'm' THEN
SET NEW.Sexo = 'M';
END IF;
IF NEW.Sexo <> 'F' AND NEW.Sexo <> 'M' THEN
SIGNAL SQLSTATE '45000'
SET MESSAGE_TEXT = 'Sexo invalido: F ou M';
END IF;
END$$
USE `SAM`$$
DROP TRIGGER IF EXISTS `Curso_BEFORE_UPDATE` $$
USE `SAM`$$
CREATE DEFINER = CURRENT_USER TRIGGER `SAM`.`Curso_BEFORE_UPDATE` BEFORE UPDATE ON `Curso` BEGIN
IF NEW.Horas < 1 THEN
SIGNAL SQLSTATE '45000'
SET MESSAGE_TEXT = 'Horas invalida: Horas > 0';
END IF;
END$$
USE `SAM`$$
DROP TRIGGER IF EXISTS `Matricula_BEFORE_UPDATE` $$
USE `SAM`$$
CREATE DEFINER = CURRENT_USER TRIGGER `SAM`.`Matricula_BEFORE_UPDATE` BEFORE UPDATE ON `BEGIN
IF NEW.Pago <> 0 AND NEW.Pago <> 1 THEN
SIGNAL SQLSTATE '45000'
SET MESSAGE_TEXT = 'Pago invalido: 0 ou 1';
END IF;
END$$
USE `SAM`$$
DROP TRIGGER IF EXISTS `Topico_BEFORE_UPDATE` $$
USE `SAM`$$
CREATE DEFINER = CURRENT_USER TRIGGER `SAM`.`Topico_BEFORE_UPDATE` BEFORE UPDATE ON `Topico` BEGIN
IF NEW.Horas < 1 THEN
SIGNAL SQLSTATE '45000'
SET MESSAGE_TEXT = 'Horas invalida: Horas > 0';
END IF;
END$$
DELIMITER ;
SET SQL_MODE=@OLD_SQL_MODE;
SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS;
SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS;
11
Scripts de Criação de Índices
-- MySQL Script generated by MySQL Workbench
-- Wed Apr 8 08:32:55 2020
-- Model: New Model Version: 1.0
-- MySQL Workbench Forward Engineering
SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0;
SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0;
SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='TRADITIONAL,ALLOW_INVALID_DATES';
USE `SAM`;
CREATE UNIQUE INDEX `UN_Area_Nome` ON `Area` (`Nome` ASC);
CREATE INDEX `IDX_FK_Area_Area` ON `Area` (`SuperArea` ASC);
CREATE INDEX `IDX_FK_Curso_Area` ON `Curso` (`Area` ASC);
CREATE INDEX `IDX_FK_Matricula_Aluno` ON `Matricula` (`Aluno` ASC);
CREATE INDEX `IDX_FK_Modulo_Curso` ON `Modulo` (`Curso` ASC);
CREATE INDEX `IDX_FK_Professor_Curso` ON `Professor` (`Curso` ASC);
CREATE INDEX `IDX_FK_Topico_Modulo` ON `Topico` (`Modulo` ASC);
SET SQL_MODE=@OLD_SQL_MODE;
SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS;
SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS;
Scripts de Criação do Banco de Dados
USE `SAM` ;
INSERT INTO `Aluno` VALUES ('00506238866','Lisette','Friesen','F','2006-11-30'),
('00694710542','Lorine','Willms','F','2019-09-14'),
('01389490385','Orie','Daugherty','F','1986-10-25'),
('01525324976','Cali','Haag','F','1998-12-12'),
('01586644848','Jackeline','Barton','F','1994-08-16');
INSERT INTO `Area` (`Sigla`, `Nome`, `SuperArea`) VALUES ('10000003', 'Ciências Exatas e INSERT INTO `Area` (`Sigla`, `Nome`, `SuperArea`) VALUES ('20000006', 'Ciências Biológicas',INSERT INTO `Area` (`Sigla`, `Nome`, `SuperArea`) VALUES ('30000009', 'Engenharias',NULL);
INSERT INTO `Area` (`Sigla`, `Nome`, `SuperArea`) VALUES ('40000001', 'Ciências da Saúde',INSERT INTO `Area` (`Sigla`, `Nome`, `SuperArea`) VALUES ('50000004', 'Ciências Agrárias',INSERT INTO `Area` (`Sigla`, `Nome`, `SuperArea`) VALUES ('60000007', 'Ciências Sociais Aplicadas',INSERT INTO `Area` (`Sigla`, `Nome`, `SuperArea`) VALUES ('70000000', 'Ciências Humanas',INSERT INTO `Area` (`Sigla`, `Nome`, `SuperArea`) VALUES ('80000002', 'Lingüística, Letras INSERT INTO `Area` (`Sigla`, `Nome`, `SuperArea`) VALUES ('90000005', 'Outra',NULL);
INSERT INTO `Area` (`Sigla`, `Nome`, `SuperArea`) VALUES ('10100008', 'Matemática','10000003');
INSERT INTO `Area` (`Sigla`, `Nome`, `SuperArea`) VALUES ('10200002', 'Probabilidade e Estatística','INSERT INTO `Area` (`Sigla`, `Nome`, `SuperArea`) VALUES ('10300007', 'Ciência da Computação','INSERT INTO `Area` (`Sigla`, `Nome`, `SuperArea`) VALUES ('10400001', 'Astronomia','10000003');
12
INSERT INTO `Area` (`Sigla`, `Nome`, `SuperArea`) VALUES ('10500006', 'Física','10000003');
INSERT INTO Curso (`Sigla`, `Nome`, `Horas`,`Custo`,`Area`) VALUES ('10101012', 'Conjuntos', INSERT INTO Curso (`Sigla`, `Nome`, `Horas`,`Custo`,`Area`) VALUES ('10101020', 'Lógica INSERT INTO Curso (`Sigla`, `Nome`, `Horas`,`Custo`,`Area`) VALUES ('10101039', 'Teoria INSERT INTO Curso (`Sigla`, `Nome`, `Horas`,`Custo`,`Area`) VALUES ('10101047', 'Grupos INSERT INTO Curso (`Sigla`, `Nome`, `Horas`,`Custo`,`Area`) VALUES ('10101055', 'Álgebra INSERT INTO Curso (`Sigla`, `Nome`, `Horas`,`Custo`,`Area`) VALUES ('10101063', 'Geometria 13

