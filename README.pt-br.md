# Dashboard de Chamados Abertos no Sistema OTRS (atualmente Znuny)

## 1. Introdução

Este projeto, iniciado antes da minha participação, foi desenvolvido para monitorar e analisar o fluxo de chamados no sistema OTRS (atualmente Znuny) da UFPB. 

Minha contribuição incluiu:

- Criação da tabela `fato_atendimento_historico`, que consolida os dados essenciais dos atendimentos.
- Construção de um dashboard funcional no Metabase, voltado para gestores da Superintendência de Tecnologia da Informação (STI).
- Modelagem dimensional dos dados, com tabelas de fatos e dimensões que sustentam visualizações e análises consistentes.
- Geração de **views materializadas**, utilizadas como fonte dos painéis no Metabase.

O objetivo principal do projeto é fornecer uma ferramenta prática e acessível para que os gestores da STI — incluindo gerentes de setores e o superintendente — acompanhem o volume, a distribuição e o status dos chamados abertos pela comunidade universitária da UFPB.

O dashboard oferece visualizações como:

- Volume de chamados por status ao longo do tempo.
- Chamados por fila, serviço, horário e data.
- Monitoramento de SLAs.
- Ranking de usuários com maior número de chamados.

Além de otimizar a gestão, a iniciativa promove **transparência interna**, melhora a **alocação de recursos** e apoia a **priorização de demandas críticas**.

## 2. Alcance

- Atinge **90+ colaboradores da STI**, incluindo técnicos e analistas de TI.
- Utilizado por **todos os gerentes de TI**, além do **superintendente de TI**.
- Algumas visualizações também são utilizadas por **gestores institucionais de outros setores**.


## 3. Tempo em Produção

- Projeto em produção desde **2020**.
- Atualmente (2025), está sendo descontinuado, pois o sistema OTRS está sendo integrado ao **GitLab**, que passa a receber automaticamente os tickets como *issues*.
- O acompanhamento e análise dos chamados passarão a ser feitos por meio de um novo dashboard, baseado nos dados extraídos do GitLab.

> Veja também: [Projeto GitLab Analytics](https://github.com/cordulaflavio/gitlab-analytics) *(link de exemplo)*

## 4. Tecnologias Utilizadas

- **Pentaho Data Integration (PDI)**: Para desenvolvimento dos processos ETL que alimentam o banco de dados analítico.
- **SQL (MySQL e PostgreSQL)**: Para construção das tabelas de fato e dimensão, modelagem de dados e criação de views.
- **CRON**: Para agendamento da atualização periódica dos dados.
- **Metabase**: Para construção dos dashboards com acesso controlado e visualizações responsivas e interativas.

## 5. Arquitetura do Projeto

A solução está inserida em uma arquitetura de **Data Warehouse departamental**, composta por múltiplos **Data Marts** temáticos. Este projeto corresponde ao **data mart `dm_otrs`**, responsável por centralizar e disponibilizar informações analíticas sobre os chamados do sistema OTRS/Znuny.

O processo completo segue a abordagem **ETL**, com extração dos dados de produção, transformação e carga em estrutura analítica modelada em esquema estrela.

### 5.1. Etapas do Processo

1. **Extração (E)**:
   - Dados extraídos diretamente do banco de produção do OTRS/Znuny (MySQL).
   - Utilização de queries SQL no Pentaho para leitura incremental e total.

2. **Transformação (T)**:
   - Criação de chaves substitutas.
   - Tratamento de datas, normalização e padronização de campos.
   - Cálculo de indicadores como tempo de atendimento e atraso de SLA.

3. **Carga (L)**:
   - Inserção dos dados transformados em um banco PostgreSQL.
   - Organização dos dados em **tabelas fato e dimensões** no escopo do data mart `dm_otrs`.
   - Criação de **views materializadas** para otimizar o consumo via Metabase.

### 5.2. Modelagem de Dados

- **Tabelas de Dimensão**:
  - `dim_sla` — Acordos de nível de serviço.
  - `dim_service` — Tipos de serviços relacionados aos chamados.
  - `dim_queue` — Filas de atendimento.
  - `dim_users` — Solicitantes e atendentes.
  - `dim_ticket_state` — Estados dos chamados.

- **Tabela Fato**:
  - `fato_atendimento_historico` — Armazena os eventos relacionados ao atendimento dos chamados, vinculando todas as dimensões e registrando métricas como duração, SLA, e status.

### 5.3. Transformações no Pentaho

Abaixo, uma das transformações desenvolvidas no Pentaho Data Integration (PDI), responsável por carregar a tabela de fatos `fato_chamado_atendimento`:

![Transformação fato_chamado_atendimento](https://github.com/cordulaflavio/OTRS-Data-Analytics/blob/main/images/Pentaho-03-fato_chamado_atendimento.png)
Outras imagens do PDI estão disponíveis na pasta [`images/`](images/) do projeto.

## 6. Dashboard

> ⚠️ Todos os dados apresentados nas imagens abaixo foram anonimizados. Não há exposição de informações sensíveis ou identificação de usuários. A segurança e a privacidade foram garantidas em todo o processo.

![Dashboard STI](https://github.com/cordulaflavio/OTRS-Data-Analytics/blob/main/images/Dashboard-OTRS-STI.png?raw=true)

## 7. Contato

Para dúvidas ou colaboração, entre em contato:

**Flavio Córdula**  
Superintendência de Tecnologia da Informação – UFPB  
[LinkedIn](https://www.linkedin.com/in/cordulaflavio)  
