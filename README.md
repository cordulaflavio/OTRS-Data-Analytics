**Dashboard de Chamados Abertos no Sistema OTRS (atualmente Znuny) - Acompanhamento de Tickets**

### 1. Introdução

**Descrição**: Este projeto, iniciado antes da minha participação, foi desenvolvido para monitorar e analisar o fluxo de chamados no sistema OTRS (atualmente Znuny) da UFPB. Minha contribuição incluiu a criação da tabela `fato_chamado_atendimento`, que sintetiza dados de atendimento, e a construção de um dashboard básico, porém essencial, para que as gerências da Superintendência de Tecnologia da Informação (STI) acompanhem o volume e o status dos chamados abertos por setor. Trabalhei na modelagem de dados para garantir uma estrutura eficiente e consistente, desenvolvendo tabelas de dimensão e fato que apoiam tanto as análises quanto a visualização final no Metabase, que consome os dados de uma *view* materializada. 

### 2. Tecnologias Utilizadas

- **Pentaho Data Integration (PDI)**: Para a criação de pipelines de ETL e geração das tabelas de fato e dimensão.
- **SQL (MySQL e PostgreSQL)**: Para modelagem de dados, construção de tabelas de fato e consultas analíticas.
- **Metabase**: Para construção do dashboard que apresenta insights sobre o desempenho do atendimento e volume de chamados abertos por gerência.

### 3. Objetivo do Projeto
Este projeto foi desenvolvido para facilitar o acompanhamento e a análise dos chamados abertos no sistema OTRS (atualmente Znuny), utilizados pela Superintendência de Tecnologia da Informação (STI) da UFPB. Originalmente iniciado por outra equipe, o projeto estava parado e foi retomado para atender à necessidade de visualização mais prática e acessível das informações de chamados.

O principal objetivo é oferecer aos gestores da STI – incluindo os gerentes de cada setor e o superintendente – uma ferramenta prática para monitorar a distribuição e o status dos chamados abertos pela comunidade acadêmica da UFPB. O dashboard, acessível a todos os integrantes da STI, centraliza informações essenciais, como o volume de chamados por status ao longo do tempo, a quantidade de chamados por fila e por serviço, dados agrupados por hora e data, monitoramento do cumprimento de SLAs e um ranking de usuários. Tudo isso simplifica o processo de análise e tomada de decisão.

Além disso, o projeto contribui para aumentar a transparência interna e melhorar a alocação de recursos, ao fornecer dados estruturados e visualizações claras que auxiliam na identificação de gargalos e na priorização de demandas.

### 4. Arquitetura do Projeto
aaa
