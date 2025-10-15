# Projeto do Banco de Dados (v1.0)

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

## 2 Especificação do Minimundo
Em modelagem de banco de dados, um minimundo é a representação simplificada e bem delimitada de uma parte específica do mundo real, recortada para atender ao objetivo de um sistema. Em vez de espelhar toda a realidade, o minimundo seleciona apenas as entidades, relacionamentos e atributos relevantes para o projeto, deixando claro o escopo do que será armazenado e utilizado pela aplicação. Essa delimitação evita incluir informações desnecessárias, reduz a sobrecarga de dados e torna o modelo mais objetivo, consistente e funcional. O minimundo deste projeto descreve um sistema acadêmico para gerenciamento de alunos, responsáveis, professores, planos, turmas/disciplinas e aulas nas modalidades Reforço, Inglês, Pré-ENEM e Pré-CEFET.

O _'Aluno'_ possui nome e telefone; ao adquirir um plano, passa a ter também CPF, ENDEREÇO, BAIRRO, COMPLEMENTO, CEP, CIDADE/ESTADO, NÚMERO DE CONTRATO, EMAIL, STATUS e DETALHES DO PLANO. Todo aluno deve possuir responsável legal; uma mesma pessoa pode acompanhar vários alunos. Quando maior de idade, o próprio aluno assume essa função. Os dados do _'Responsável legal'_ — -(identificação e contato)-* — são mantidos para o vínculo.

As _'Aulas'_ são eventos agendados que registram HORA DE ÍNICIO, HORA DE FIM, DURAÇÃO, MODALIDADE (individual ou em grupo), -(DATA)-*,  OBSERVAÇOES, INDICADOR DE AULA REALIZADA e o PROFESSOR QUE MINISTROU. A modalidade _'Reforço'_ é sempre individual e associa uma matéria específica e agendamentos pontuais. Na modalidade _'Inglês'_, além dos campos gerais, registram-se o CONTEUDO ABORDADO, a TURMA QUE RECEBEU A AULA, o DEVER DE CASA e o CONTEUDO PREVISTO PARA PRÓXIMA AULA. As modalidades _'Pré-ENEM'_ e _'Pré-CEFET'_ funcionam por _'Turmas'_ e _'Disciplinas'_; cada disciplina nessas preparações possui professor e horário fixo.

Os _'Planos'_ definem regras acadêmicas e financeiras: MODALIDADE ATENDIDA , FREQUÊNCIA SEMANAL DE AULAS, FORMATO (em grupo ou individual), exigência de TAXA DE MATRICULA, POLÍTICAS DE DESCONTO, DADOS DE VENCIMENTO e VALOR DO CURSO. Um aluno pode ter vários planos ao longo do tempo, mas apenas um plano ativo determina suas condições de participação no período vigente. Um aluno pode participar de diferentes tipos de aula ao longo do tempo, conforme sua necessidade e plano.

O _'Professor'_ mantém CPF, RG, ENDEREÇO e DADOS BANCÁRIOS. Há dois TIPOS DE REGIMES de contrato: clt e horista. Todo contrato tem DATA DE INÍCIO; no regime clt também há DATA DE FIM (o horista não possui, por natureza, término fixo, sendo regido por carga horária e demandas). Professores ministram aulas conforme sua ESPECIALIZAÇOES e podem estar vinculados a _'DICIPLINAS'_ com HORAS DE ÍNICIO e HORAS DE FIM.

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
