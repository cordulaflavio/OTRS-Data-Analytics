**Dashboard de Chamados Abertos no Sistema OTRS (atualmente Znuny) - Acompanhamento de Tickets**

- **Descrição**: Este projeto, iniciado antes da minha participação, foi desenvolvido para monitorar e analisar o fluxo de chamados no sistema OTRS (atualmente Znuny) da UFPB. Minha contribuição foi na criação da tabela `fato_chamado_atendimento`, que sintetiza dados de atendimento, permitindo um dashboard básico mas essencial para que as gerências da Superintendência de Tecnologia da Informação (STI) acompanharem o volume e o status dos chamados abertos em cada setor. Trabalhei na modelagem de dados para garantir uma estrutura eficiente e consistente, e criei dimensões e fatos para apoiar as análises e a visualização final no Metabase.

- **Tecnologias Utilizadas**:
  - **Pentaho Data Integration (PDI)**: Para a criação de pipelines de ETL e geração das tabelas de fato e dimensão.
  - **SQL (MySQL e PostgreSQL)**: Para modelagem de dados, construção de tabelas de fato e consultas analíticas.
  - **Metabase**: Para construção do dashboard que apresenta insights sobre o desempenho do atendimento e volume de chamados abertos por gerência.
