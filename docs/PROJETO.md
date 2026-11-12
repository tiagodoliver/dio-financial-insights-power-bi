# Documentação do projeto

## Objetivo

Permitir que um gestor explore o desempenho comercial e o resultado financeiro da amostra Financial Sample, com navegação simples e representações alternativas para o mesmo tema.

## Estrutura da entrega

```text
README.md
Financial-Insights.pbix
dados/
  Financial Sample.xlsx
docs/
  PROJETO.md
  01-vendas.png
  02-lucratividade.png
  tema-financial-insights.json
```

O `.pbix` contém o modelo importado e os dados incorporados. As imagens são prévias estáticas; a interação está no arquivo do Power BI. O JSON contém o tema de cores utilizado e pode ser reutilizado em Exibição → Temas → Procurar temas.

## Construção

O modelo de referência da professora foi preservado como ponto de partida. A tabela `financials` reúne dimensões comerciais, período e valores financeiros. Os visuais usam agregações de soma, sem necessidade de visuais externos.

| Página | Conteúdo |
|---|---|
| 01 · Visão de vendas | Cinco cartões, área mensal, colunas por produto, barras/rosca por segmento e barras/treemap por país |
| 02 · Lucratividade | Cinco cartões, área mensal, colunas de lucro por produto, barras de lucro por segmento e país |

Cada página possui segmentadores de período, país, segmento e ano. Os filtros são locais à página. Os botões superiores têm ações de navegação entre páginas. Quatro indicadores controlam a visibilidade dos pares de gráficos da primeira página, preservando os filtros; dois indicadores restauram os filtros das respectivas páginas. O botão Limpar associa o ícone de restauração à ação.

A identidade visual utiliza fundo claro, cabeçalho azul-escuro, cartões brancos e uma paleta de azul-petróleo, verde e dourado. Os produtos são apresentados em colunas para mostrar as seis categorias sem rolagem.

## Definições

| Indicador | Agregação usada |
|---|---|
| Vendas líquidas | Soma de `financials[ Sales]` — o campo da referência possui espaço inicial |
| Lucro | Soma de `financials[Profit]` |
| Custo dos produtos | Soma de `financials[COGS]` |
| Descontos | Soma de `financials[Discounts]` |
| Vendas brutas | Soma de `financials[Gross Sales]` |
| Unidades vendidas | Soma de `financials[Units Sold]` |

As identidades da amostra são vendas brutas − descontos = vendas líquidas e vendas líquidas − custos = lucro. Os valores completos foram conferidos contra o Excel. A margem citada no README é a razão entre os totais de lucro e vendas; ela não é um cartão ou uma medida adicional no relatório.

## Dados e atualização

A amostra possui 700 linhas, cinco países, seis produtos, cinco segmentos e 16 meses. A coluna de data representa o mês com o primeiro dia, não o dia individual de cada venda. O período vai de 01/09/2013 a 01/12/2014, incluindo os meses de setembro de 2013 a dezembro de 2014.

O arquivo abre com os dados incorporados, sem depender da localização da planilha. Para atualizar os dados, ajuste a origem herdada do material de referência em **Transformar dados → Configurações da fonte de dados → Alterar fonte**, apontando para a cópia `dados/Financial Sample.xlsx`, e aplique as alterações. A atualização da origem e o agendamento no Service não foram configurados nesta entrega.

Não houve conversão de moeda nem inclusão de dados de produção. Comparações de 2013 e 2014 precisam usar meses equivalentes. Sem filtro de ano, os gráficos mensais somam os mesmos meses dos dois anos.

## Validação

O arquivo foi aberto no Power BI Desktop instalado no computador. As duas páginas e seus gráficos foram inspecionados. Os indicadores de visibilidade e a navegação foram acionados no aplicativo. O filtro de 2013 apresentou vendas de **26.415.255,51** e lucro de **3.878.464,51**, conciliados com a planilha. O botão Limpar restaurou o conjunto completo.

| Conferência sem filtros | Resultado esperado |
|---|---:|
| Registros da planilha | 700 |
| Vendas líquidas | 118.726.350,26 |
| Lucro | 16.893.702,26 |
| Custos | 101.832.648,00 |
| Descontos | 9.205.248,24 |
| Vendas brutas | 127.931.598,50 |
| Unidades vendidas | 1.125.806 |

Os cartões abreviam valores como Mi e Mil. Pequenas diferenças de ponto flutuante antes do arredondamento não alteram os totais monetários exibidos a duas casas.

## Atendimento ao desafio

| Requisito | Implementação |
|---|---|
| Estrutura e layout | Duas páginas com identidade visual consistente |
| Navegação por botões | Vendas ↔ Lucro |
| Segmentadores e botão com imagem/ícone | Período, país, segmento e ano; Limpar com ícone de restauração |
| Indicadores e visuais alternativos | Barras/rosca e barras/treemap na página de vendas |
| Segunda página | Análise de lucratividade |
| Repositório e referência | Fork da professora, créditos e arquivos de entrega |
| Publicação no Power BI Service | **Pendente:** serviço exigiu acesso com conta corporativa/de estudante; somente Desktop disponível |

## Publicação futura

Entrar com uma conta habilitada, abrir o `.pbix`, publicar em um workspace autorizado e testar os filtros no relatório publicado. Depois, acrescentar o link ao README. Publicar no Service não concede automaticamente acesso a todos os avaliadores. Nenhum link público de “Publicar na Web” foi criado.

## Referência

[Repositório original da professora Juliana Zanelatto](https://github.com/julianazanelatto/power_bi_analyst), commit `b010c1874a183a0fb4b831e76dc68b9b872becec`, pasta Módulo 2 / Desafio de Projeto.
