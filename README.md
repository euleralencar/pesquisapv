# Pesquisa Plenário Virtual (PV)

[![hackmd-github-sync-badge](https://hackmd.io/VMJnzZ0USWCwGRc27kQmHQ/badge)](https://hackmd.io/VMJnzZ0USWCwGRc27kQmHQ)


## Objetivo


O projeto de pesquisa tem como objetivo analisar o mecanismo do Plenário Virtual e sua utilização pelo Supremo Tribunal Federal durante o período de pandemia no ano de 2020, tratando-se, portanto, de uma pesquisa descritiva e exploratória.

Pretende-se também proceder a uma análise comparativa em relação à maneira como o Tribunal utilizava o PV em um período anterior e como passou a utilizá-lo durante a pandemia.

Para chegar as respostas esse primeiro estudo trilhará os seguintes passos:

1. Análise geral das decisões no período de 2006 até 2021;
1. Análise do comportamento de decisoes monocráticas e colegiadas e como este último tem se comportado comparativamente;
1. Análise sobre o colegiado e buscar respostas sobre como o ambiente virtual vem sendo usado ao longo do anos, dado as emendas regimentais trazidas nos últimos anos que buscavam a modernização da Corte;
1. Análise sobre o impacto das decisões virtuais nos tipos de processos que vão ao plenário ou turma;
1. Análise sobre o comportamento de votação no Plenário Virtual nos período imediamente antes e imediatamente após a pandemia;
2. Análise dos pedidos de destaque e sustentações orais;


## Bases de Dados

Para trabalhar com a pesquisa de dados utilizamos quatro bases que se complementam:

1. Base de decisões;
2. Base de votos;
3. Base de destaques;
4. Base de sustentações orais.

Essas bases podem ser acessadas na pasta \dados desse github.

## Dicionário de dados

### 1. Base de decisões

O estudo foi realizado a partir de dados coletados Portal de Informações Gerenciais (PIG) em **27/08/2021**. Este sistema é o SAP BusinessObjects BI (SAP BO) que é um conjunto centralizado de ferramentas de relatórios e análises para plataformas de business intelligence (BI). Ele consiste em uma série de aplicativos de relatórios que permitem aos usuários descobrir dados, realizar análises para obter insights e criar relatórios que visualizam os insights.

Este sistema faz registro de diversas dimensões de dados do STF, desde recebimento do processo no STF até sua baixa. **Para o presente estudo foram extraídos dados de decisão de 01.01.2006 até 31.06.2021.**

Dicionário :book: 

1. **classe**: classe processual;
1. **numero**: número associado a classe processual acima;
1. **link**: composição entre classe processual e seu número, criando uma chave única para cada processo;
1. **data_autuacao**: data em que o processo foi autuado (entrou) no STF;
1. **data_baixa**: data em que o processo foi baixado no STF, isto é, é um processo que não faz parte mais do rol de processos em tramitação do Tribunal;
1. ~~* **relator_atual**: é variável que registra o relator atual do processo. Caso o processo já tenha sido baixado, o relator atual será o último ministro que tenha ficado como do processo, que pode ser diferente do nome_ministro abaixo;~~
1. **nome_ministro_a**: variável que registra o ministro responsável pela decisão. Quando o relator submete ao plenário e vence, seu nome é registrado nessa variável. Quando o relator é vencido, então é utilizado o primeiro ministro a discordar do relator como referência para decisão;
1. **data_andamento**: data da decisão;
1. **observacao_andamento**: campo livre que permite inclusão de informações adicionais sobre a decisão do processo. É uma variável rica para exploração;
1. **subgrupo_andamento_comissao**: variável que registra o grupo que o andamento de decisão pertence, por exemplo, se é uma decisão do grupo liminar, se é uma decisão do grupo final, e assim por diante;
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
- Foi realizado correção na variável órgão julgador, que registra o responsável pela decisão seja ministro ou órgão colegiado. Para isso, é realizado a combinação das variáveis **orgao_julgador** e a busca do termo *"Sessão Virtual"* no campo **observacao_andamento**. Dessa forma, podemos encontrar os valores dos julgamentos virtuais;
- Foi criado uma nova variável ramo_direito_novo (versão 2) com alguns ajustes de classificação no ramo do direito. A tabela de ajuste, conforme abaixo:


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

### 2. Base de votos;

Dicionário :book: 
- **id_voto**: número único que identifica cada voto;
- **id_julgamento**: número único que identifica cada julgamento. Se um processo foi julgado mais de uma vez, será registrado com dois id_julgamentos diferentes;
- **classe**: Classe processual;
- **numero**: Número único associado a classe;
- **id_processo**: Combinação da classe e número que dá um número único a cada processo;
- **tipo_julgamento**:
- **sigla_ministro_voto**:
- **nome_ministro_voto**:
- **descricao_do_voto**:
- **data_hora_voto**:
- **ambiente_voto**:

#### **Notas metodológicas** :bookmark: 

Metodologicamente, é quase impossível que os números batam integralmente, pois a base de votos é contabilizada no nível de ministro a ministro com suas respectivas data de votação. Acontece que há entre o primeiro e o último voto diferença temporal que impactaria a entrada daquele processo dentro da base.

Poderia acontecer da votação começar fora do período da pesquisa (primeiro voto) e finalizar dentro do período da pesquisa (último voto) ou o contrário, começar dentro do período (primeiro voto) e finalizar fora (último voto). Outra possibilidade é começar no período “pre-pandamia” e finalizar no período “pos-pandemia”.

Isso poderia trazer algumas dificuldades de manipulação da base que aumentariam a complexidade com pouco benefício em termos de identificação de padrões estatísticos.

Assim, para estabelecimento de uma uniformidade metodolófica, utilizou-se como referência a data do último voto como data daquele julgamento. Assim, se a data do último voto daquele processo estiver dentro do período da pesquisa, então seria contabilizado dentro da base, caso contrário seria descartado.

A diferença para a base de decisões é que poderia ocorrer uma votação antes do período da pesquisa, mas se ela foi registrada dentro do período, seria incluida na base de análise. Assim, é possível ocorrer pequenas divergências (~ 100 processos por ambiente de decisão) entre a base de decisões e a base de votos.

Para manipulação da base foram considerados somente os votos dentro do período da pesquisa, isto é de 19/06/2019 a 31/12/2020 e foram retirados os ministros que se declaração suspeitos ou impedidos. 

### 3. Base de destaques;

Dicionário :book: 

- **classe**: Classe processual;
- **numero**: Número único associado a classe;
- **id_processo**: Combinação da classe e número que dá um número único a cada processo;
- **tipo_pedido_destaqueo**: Identifica se o destaque era sobre mérito ou recurso;
- **ministro_pedido_destaque**: Ministro que solicitou o destaque;
- **descricao_andamento**: Andamento de associado ao destaque "Retirado do Julgamento Virtual" associado com a observação do andamento "Pedido de destaque";
- **obs_pedido_destaque**: Os pedidos de destaque são registrados nesse campo como "Pedido de destaque"
- **data_destaque**: data do andamento de "Retirado do Julgamento Virtual";
- **periodo_destaque**: identifica que se foi no período pré-pandemia, pós-pandemia ou fora destes dois períodos.


### 4. Base de sustentações orais. :construction: 

Em construção. 


## 5. Baixar os dados

Os dados podem ser baixados na pasta **dados** desse Git. Os arquivos foram salvos em RDS por questões de otimização. Para baixar os arquivos basta baixar o programa R e usar o script a seguir:

```{R}
decisao <- readRDS(file="data//base_decisoes.RDS")

votos <- readRDS(file="data//base_votos.RDS")

destaque <- readRDS(file="data//base_destaque.RDS")
```
