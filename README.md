# Pesquisa Plenário Virtual (PV)

## Bases de Dados

Para trabalhar com a pesquisa de dados utilizamos quatro bases que se complementam:

1. Base de decisões;
2. Base de votos;
3. Base de destaques;
4. Base de sustentações orais.

## Dicionário de dados

### Base de decisões

**classe**: classe processual
**numero**: número associado a classe processual acima
**link**: composição entre classe processual e seu número, criando uma chave única para cada processo.
**meio_processovariável** que verifica se é um processo físico ou eletrônico.
**data_autuacao**: data em que o processo foi autuado (entrou) no STF.
**data_baixa**: data em que o processo foi baixado no STF, isto é, é um processo que não faz parte mais do rol de processos em tramitação do Tribunal.
**relator_atual**: é variável que registra o relator atual do processo. Caso o processo já tenha sido baixado, o relator atual será o último ministro que tenha ficado como **relator** do processo, que pode ser diferente do nome_ministro abaixo.
**nome_ministro_a**: variável que registra o ministro responsável pela decisão. Quando o relator submete ao plenário e vence, seu nome é registrado nessa variável. Quando o relator é vencido, então é utilizado o primeiro ministro a discordar do relator como referência para decisão.
**mes_andamento** mês da decisão.
**data_andamento**: data da decisão.
**observacao_andamento**: campo livre que permite inclusão de informações adicionais sobre a decisão do processo. É uma variável rica para exploração.
**subgrupo_andamento_comissao**: variável que registra o grupo que o andamento de decisão pertence, por exemplo, se é uma decisão do grupo liminar, se é uma decisão do grupo final, e assim por diante.
**primeira_decisao_final**: andamento da primeira decisão final.
**data_primeira_decisao_final**: data da primeira decisão final.
**primeira_decisao_liminar**: andamento da primeira decisão liminar.
**data_primeira_decisao_liminar**: data da primeira decisão liminar.
**orgao_julgador**: Indica qual origem da decisão, seja ela monocrática ou colegiada;
**tipo_decisao**: Informa se a decisão é monocrática ou colegiada;
**ramo_direito_novo**: É classificado pelo tipo da matéria do processo que corresponde ao primeiro assunto do processo;
**assuntos**: Informa os assuntos atribuídos ao processo;
**preferencia_covid_19**: Informa se o processo tem algum assunto relacionado ao Covid-19;
**indicador_virtual**: Indica se a decisão do processo foi julgada em sessões virtuais;
**qtd_ocorrencias_processuais**: Indica a quantidade de ocorrências em um determinado andamento de um processo. Por exemplo, se um determinado processo tiver três decisões finais em um único andamento, os três serão contabilizados;
