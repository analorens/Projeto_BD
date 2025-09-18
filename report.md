# Projeto do Banco de Dados SAM (v1.0)
Wladmir Cardoso Brandão Março 30, 2020
## Professor
Marco Paulo

## Integrantes
Ana Lorens
Álvaro Félix
Augusto Henrique
Leonardo Andrade
Vitor Martins
Walker Rocha

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
Um mini mundo em banco de dados corresponde a uma representação simplificada e delimitada de uma parte específica do mundo real, escolhida para ser organizada dentro de um sistema de banco de dados. Essa abordagem tem como objetivo selecionar apenas os dados relevantes para o contexto de um projeto, estabelecendo com clareza o escopo do que será armazenado e utilizado pela aplicação. Dessa forma, evita-se a inclusão de informações desnecessárias, reduzindo a sobrecarga e garantindo que o modelo seja mais objetivo e funcional.

Um banco de dados para um sistema acadêmico que gerencia a matrícula de alunos em aulas especializadas. Em particular, as aulas são categorizados por tipo, sendo eles: reforço, inglês, pré-técnico, e pré-enem. As aulas no geral possuem hora de início, hora de fim, duração, modalidade, relatório/observações, aula realizada, professor. As aulas de reforço são sempre individuais, possuem matéria. Já as aulas de inglês possuem: Conteúdo abordado na aula, professor que ministrou a aula, class que recebeu a aula, dever de casa e registro de qual é o conteúdo da próxima aula. As aulas Pré-CEFET e Pré-ENEM possuem uma turma, e uma disciplina. Sendo que cada disciplina do Pré enem e pré CEFET possuem professor e horário fixo. Todos Alunos possuem um responsável e o responsável pode ser resposável por vários alunos. Aluno possui nome,telefone e caso o aluno adquira um plano, ele possuirá também: cpf, endereço, Nº do contrato, status, detalhe do plano. Aluno pode participar de diferentes tipos de aula. Planos possuem: modalidade, frequência de aulas por semana, em grupo ou individual, se paga
taxa de matricula, desconto, data de vencimento, valor do curso. Professor possui cpf, rg, comprovante de endereço, endereço, dados bancários. Professor pode ser CLT ou Horista. Ambas especializações de professor possuem contrato no qual possui: Data de Inicio. Porém o contrato do Professor CLT possui data de fim.

# 1
## 2.1 Requisitos Funcionais
Diferentes grupos de usuários demandarão diferentes operações de manipulação de dados sobre diferentes porções
do banco de dados. O grupo SecRetaRia demandará atualização e recuperação de dados sobre praticamente todas
os elementos do banco de.dados, uma vez que esse grupo será o responsável por manter os dados atualizados, dando
suporte aos outros grupos. O grupo PRofessoR demandará consultas de recuperação de dados sobre suas alocações
a cursos. O grupo Aluno demandará consultas para atualização de seus dados cadastrais e para manipulação de
dados sobre suas matrículas. O grupo GeRÊncia demandará a recuperação de dados agrupados sobre matrícula e
cursos, tais como carga horária, custo e alocações de professores e alunos. O grupo GeRal demandará recuperação
de dados sobre áreas, cursos, módulos e tópicos para tomada de decisão sobre inscrição como aluno ou professor da
instituição de.ensino. A Tabela 1 apresenta as principais consultas que cada grupo de usuários demandará ao sistema
de banco de dados, bem como a frequência esperada de submissão (A para alta, M para média e B para baixa.
