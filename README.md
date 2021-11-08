# Pesquisa Plenário Virtual (PV)

[![hackmd-github-sync-badge](https://hackmd.io/VMJnzZ0USWCwGRc27kQmHQ/badge)](https://hackmd.io/VMJnzZ0USWCwGRc27kQmHQ)


## Bases de Dados

Para trabalhar com a pesquisa de dados utilizamos quatro bases que se complementam:

1. Base de decisões;
2. Base de votos;
3. Base de destaques;
4. Base de sustentações orais.

## Dicionário de dados

### 1. Base de decisões

O estudo foi realizado a partir de dados coletados Portal de Informações Gerenciais (PIG) em **27/08/2021**. Este sistema é o SAP BusinessObjects BI (SAP BO) que é um conjunto centralizado de ferramentas de relatórios e análises para plataformas de business intelligence (BI). Ele consiste em uma série de aplicativos de relatórios que permitem aos usuários descobrir dados, realizar análises para obter insights e criar relatórios que visualizam os insights.

Este sistema faz registro de diversas dimensões de dados do STF, desde recebimento do processo no STF até sua baixa. **Para o presente estudo foram extraídos dados de decisão de 01.01.2006 até 31.06.2021.**

1. **classe**: classe processual;
1. **numero**: número associado a classe processual acima;
1. **link**: composição entre classe processual e seu número, criando uma chave única para cada processo;
1. ~~* **meio_processovariável** que verifica se é um processo físico ou eletrônico;~~
1. **data_autuacao**: data em que o processo foi autuado (entrou) no STF;
1. **data_baixa**: data em que o processo foi baixado no STF, isto é, é um processo que não faz parte mais do rol de processos em tramitação do Tribunal;
1. ~~* **relator_atual**: é variável que registra o relator atual do processo. Caso o processo já tenha sido baixado, o relator atual será o último ministro que tenha ficado como do processo, que pode ser diferente do nome_ministro abaixo;~~
1. **nome_ministro_a**: variável que registra o ministro responsável pela decisão. Quando o relator submete ao plenário e vence, seu nome é registrado nessa variável. Quando o relator é vencido, então é utilizado o primeiro ministro a discordar do relator como referência para decisão;
1. ~~* **mes_andamento** mês da decisão;~~
1. **data_andamento**: data da decisão;
1. **observacao_andamento**: campo livre que permite inclusão de informações adicionais sobre a decisão do processo. É uma variável rica para exploração;
1. **subgrupo_andamento_comissao**: variável que registra o grupo que o andamento de decisão pertence, por exemplo, se é uma decisão do grupo liminar, se é uma decisão do grupo final, e assim por diante;
1. ~~* **primeira_decisao_final**: andamento da primeira decisão final;~~
1. ~~* **data_primeira_decisao_final**: data da primeira decisão final;~~
1. ~~* **primeira_decisao_liminar**: andamento da primeira decisão liminar;~~
1. ~~* **data_primeira_decisao_liminar**: data da primeira decisão liminar;~~
1. **orgao_julgador**: Indica qual origem da decisão, seja ela monocrática ou colegiada;
1. **tipo_decisao**: Informa se a decisão é monocrática ou colegiada;
1. **ramo_direito_novo**: É classificado pelo tipo da matéria do processo que corresponde ao primeiro assunto do processo;
1. **assuntos**: Informa os assuntos atribuídos ao processo;
1. **preferencia_covid_19**: Informa se o processo tem algum assunto relacionado ao Covid-19;
1. **indicador_virtual**: Indica se a decisão do processo foi julgada em sessões virtuais;
1. **qtd_ocorrencias_processuais**: Indica a quantidade de ocorrências em um determinado andamento de um processo. Por exemplo, se um determinado processo tiver três decisões finais em um único andamento, os três serão contabilizados.
1. **marcos_pandemia**: indica em que período aquela decisão foi tomada: pré-pandemia, pós-pandemia ou fora desses duas classificações, conforme regra abaixo:
    * Se decisão foi cadastrada em sistema entre 18.06.2019 e 19.03.2020 então classificamos como "pré-pandemia";
    * Se decisão foi cadastrada em sistema entre 19.03.2020 e 31.12.2020 então classificamos como "pré-pandemia";
    * Fora destes dois períodos é cadastrada como não se aplica.

**Observações metodologicas:**
- - Registramos sobre o problema dos virtuais?
- Foi criado ramo do direito novo 2 com alguns ajustes de classificação no ramo do direito. Acho importante registrar na metodologia, conforme abaixo:


|ramo_direito_novo                                                                      |para_ramo_direito                                           |
|:--------------------------------------------------------------------------------------|:-----------------------------------------------------------|
|DIREITO MARÍTIMO                                                                       |DIREITO MARÍTIMO                                            |
|DIREITO ELEITORAL E PROCESSO ELEITORAL DO STF                                          |DIREITO ELEITORAL E PROCESSO ELEITORAL                      |
|DIREITO ADMINISTRATIVO E OUTRAS MATÉRIAS DE DIREITO PÚBLICO - MEIO AMBIENTE - POLUIÇÃO |DIREITO ADMINISTRATIVO E OUTRAS MATÉRIAS DE DIREITO PÚBLICO |
|NA                                                                                     |ASSUNTOS DIVERSOS                                           |
|REGISTROS PÚBLICOS                                                                     |ASSUNTOS DIVERSOS                                           |
|ASSUNTOS DIVERSOS                                                                      |ASSUNTOS DIVERSOS                                           |
|ASSUNTO PARA PROCESSO ANTIGO                                                           |ASSUNTOS DIVERSOS                                           |
|SENTENÇA ESTRANGEIRA                                                                   |ASSUNTOS DIVERSOS                                           |
|CRIME CONTRA O SISTEMA FINANCEIRO NACIONAL                                             |ASSUNTOS DIVERSOS                                           |
|ESTRANGEIRO                                                                            |ASSUNTOS DIVERSOS                                           |
|CONCURSO PÚBLICO                                                                       |ASSUNTOS DIVERSOS                                           |
|PROCESSO CIVIL                                                                         |ASSUNTOS DIVERSOS                                           |
|AÇÃO POPULAR                                                                           |ASSUNTOS DIVERSOS                                           |
|DESAPROPRIAÇÃO                                                                         |ASSUNTOS DIVERSOS                                           |
|SOCIEDADE CIVIL                                                                        |ASSUNTOS DIVERSOS                                           |
|PODER DE POLÍCIA                                                                       |ASSUNTOS DIVERSOS                                           |
|PREVIDÊNCIA SOCIAL                                                                     |ASSUNTOS DIVERSOS                                           |
|ADVOGADO                                                                               |ASSUNTOS DIVERSOS                                           |
|SUPREMO TRIBUNAL FEDERAL                                                               |ASSUNTOS DIVERSOS                                           |
|SEGURANÇA PÚBLICA                                                                      |ASSUNTOS DIVERSOS                                           |


Baixar as bases:



### 2. Base de votos;


### 3. Base de destaques;


### 4. Base de sustentações orais.

