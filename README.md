# UMA SOLUÇÃO DE BI PARA A FARMACOVIGILÂNCIA BASEADA NO SISTEMA DE INFORMAÇÃO VIGIMED

## Objetivo: Criar um data warehouse utilizando dados do sistema VigiMed para facilitar a interpretação e análise de dados de farmacovigilância
- Automatizar a coleta de dados do VigiMed.
- Tratar e higienizar os dados utilizando processos de ETL(Extração, Transformação e Carregamento).
- Popular e manter atualizado um banco de dados estruturado.
- Desenvolver uma rotina de atualização automática para os dados do banco.
- Integrar o banco de dados a ferramentas de Business Intelligence para análises e visualizações interativas.
  
Fonte de dados: https://dados.gov.br/dados/conjuntos-dados/notificacoes-em-farmacovigilancia

Data da Extração de dados: 24/02/2025

----------------------------------------------------------------------------------------------------------------------------------------
## Arquivo VigiMed.Notificacoes.csv

Atributos: 29
Instâncias: 243.353

| **Campo**                                   | **Descrição**                                                                                              |
|---------------------------------------------|------------------------------------------------------------------------------------------------------------|
| **UF**                                      | Unidade da Federação responsável pela notificação do evento adverso.                                        |
| **TIPO_ENTRADA_VIGIMED**                    | Interface de entrada da informação no VigiMed.                                                              |
| **RECEBIDO_DE**                             | Caracterização do notificador do caso.                                                                     |
| **IDENTIFICACAO_NOTIFICACAO**                | Número de identificação da notificação.                                                                     |
| **DATA_INCLUSAO_SISTEMA**                   | Data que a notificação foi registrada no sistema VigiMed pela primeira vez.                                |
| **DATA_ULTIMA_ATUALIZACAO**                 | Data que a notificação foi atualizada no sistema pela última vez.                                          |
| **DATA_NOTIFICACAO**                        | Data da Notificação.                                                                                       |
| **TIPO_NOTIFICACAO**                        | Tipo de Notificação.                                                                                       |
| **NOTIFICACAO_PARENT_CHILD**                | Notificação relacionada ao uso de medicamento pelo pai/mãe, cujo evento ocorreu no filho/feto.             |
| **DATA_NASCIMENTO**                         | Data de nascimento do paciente.                                                                            |
| **IDADE_MOMENTO_REACAO**                    | Idade do paciente no momento da reação.                                                                    |
| **GRUPO_IDADE**                             | Grupo Idade                                                                                                 |
| **IDADE_GESTACIONAL_MOMENTO_REACAO**        | Período da gestação no momento do evento (se notificação parente-child). Pode ser informado em dias, semanas, meses ou trimestre. |
| **SEXO**                                    | Sexo do paciente.                                                                                          |
| **GESTANTE**                                | Reação foi em gestante. Podendo ser sim ou não.                                                             |
| **LACTANTE**                                | Reação foi em lactante. Podendo ser sim ou não.                                                             |
| **PESO_KG**                                 | Peso declarado.                                                                                             |
| **ALTURA_CM**                               | Altura declarada.                                                                                           |
| **REACAO_EVENTO_ADVERSO_MEDDRA**            | Reação evento adverso codificado no MedDRA                                                                  |
| **GRAVE**                                   | Evento adverso grave ou não grave                                                                           |
| **GRAVIDADE**                               | Critério da gravidade de evento adverso grave                                                               |
| **DESFECHO**                                | Desfecho do evento adverso vivenciado.                                                                      |
| **DATA_INICIO_HORA**                        | Data de Início do Evento Adverso                                                                            |
| **DATA_FINAL_HORA**                         | Data do término do evento adverso.                                                                          |
| **DURACAO**                                 | Duração do evento adverso.                                                                                 |
| **RELACAO_MEDICAMENTO_EVENTO**              | Papel do medicamento no evento, ou seja, se ele é Suspeito, Concomitante, em interação ou Medicamento não administrado. |
| **NOME_MEDICAMENTO_WHODRUG**                | Nome do medicamento codificado no WHODrug.                                                                  |
| **ACAO_ADOTADA**                            | Medida adotada após a ocorrência do evento.         

----------------------------------------------------------------------------------------------------------------------------------------
## Arquivo VigiMed.Medicamentos.csv

Atributos: 9
Instâncias: 466.704

| **Campo**                                      | **Descrição**                                                                                              |
|------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| **IDENTIFICACAO_NOTIFICACAO**                   | Número de identificação da notificação.                                                                     |
| **RELACAO_MEDICAMENTO_EVENTO**                 | Papel do medicamento no evento, ou seja, se ele é Suspeito, Concomitante, em interação ou Medicamento não administrado. |
| **NOME_MEDICAMENTO_WHODRUG**                   | Nome do medicamento codificado no WHODrug.                                                                  |
| **PRINCIPIOS_ATIVOS_WHODRUG**                   | Nome do princípio do medicamento codificado no WHODrug.                                                     |
| **CODIGO_ATC**                                  | Código da classificação ATC (Anatomical Therapeutic Chemical Code).                                         |
| **DETENTOR_REGISTRO**                          | Nome da empresa detentora do registro do Medicamento.                                                       |
| **CONCENTRACAO**                               | Concentração do medicamento utilizada na posologia.                                                         |
| **COMPONENTE_SUSPEITO**                        | Tipo de componente que causou a reação: ativo, excipiente ou outro agente.                                  |
| **ACAO_ADOTADA**                               | Medida adotada após a ocorrência do evento adverso.                                                          |
| **PROBLEMAS_ADICIONAIS_RELCIONADOS_MEDICAMENTO**| Informação adicional pertinente ao caso.                                                                    |
| **INDICACAO_MEDDRA**                           | Indicação do medicamento codificada no dicionário MedDRA.                                                   |
| **INDICACAO_RELATADA_NOTIFICADOR_INICIAL**     | Indicação do medicamento informada pelo notificador.                                                        |
| **DOSE**                                       | Dose do medicamento utilizada.                                                                              |
| **FREQUENCIA_DOSE**                            | Número de unidades da dose no intervalo de tempo definido.                                                  |
| **POSOLOGIA**                                  | Dose do medicamento na frequência definida.                                                                  |
| **DURACAO**                                    | Duração da administração de medicamento.                                                                    |
| **INICIO_ADMINISTRACAO**                       | Início da administração do medicamento.                                                                     |
| **FIM_ADMINISTRACAO**                          | Fim da administração do medicamento.                                                                        |
| **FORMA_FARMACEUTICA**                         | Forma farmacêutica do medicamento utilizada (comprimido, solução, pomada, etc).                            |
| **VIA_ADMINISTRACAO**                          | Via que o medicamento foi administrado.                                                                     |
| **VIA_ADMINISTRACAO_MAE_PAI**                  | Via que o medicamento foi administrado pela mãe ou pai (se notificação parente-child).                      |
| **NUMELO_LOTE**                                | Número do lote do medicamento.                                                                              |

----------------------------------------------------------------------------------------------------------------------------------------
## Arquivo VigiMed.Reacoes.csv

Atributos: 12
Instâncias: 685.777

| **Campo**                                       | **Descrição**                                                                                              |
|-------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| **IDENTIFICACAO_NOTIFICACAO**                    | Número de identificação da notificação.                                                                     |
| **REACAO_EVTO_ADVERSO_MEDDRA_LLT**              | Evento adverso relatado na notificação codificado no MedDRA.                                                |
| **PT**                                          | Termo preferencial do dicionário MedDRA.                                                                   |
| **HLT**                                         | Termo do nível mais alto do dicionário MedDRA.                                                             |
| **HLGT**                                        | Grupo do termo do nível mais alto do dicionário MedDRA.                                                     |
| **SOC**                                         | Sistema Órgão Classe.                                                                                     |
| **DATA_INICIO_HORA**                            | Data de Início do Evento Adverso                                                                            |
| **DATA_FINAL_HORA**                             | Data do término do evento adverso.                                                                          |
| **DURACAO**                                     | Duração do evento adverso.                                                                                 |
| **GRAVE**                                       | Evento grave ou não grave                                                                                  |
| **GRAVIDADE**                                   | Critério da gravidade da reação que é marcada quando ela é grave.                                          |
| **DESFECHO**                                    | Desfecho do evento adverso vivenciado.                                                                      |
