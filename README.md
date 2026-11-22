# Porsche-Dashboard
Porshe Dashboard
# Dashboard de Performance Comercial Porsche

Um dashboard interativo de performance comercial, desenvolvido em página única, com base na planilha `Sanitized` do arquivo de vendas da Porsche fornecido.

## Dashboard

Após a ativação do GitHub Pages, o dashboard estará disponível em:

`https://<nome-de-usuario-github>.github.io/<nome-do-repositorio>/`

> **Status da publicação:** ainda não publicado. É necessário conectar a conta do GitHub e aprovar a exposição dos dados públicos antes da publicação.

## Perguntas de negócio selecionadas — e justificativas

O dashboard concentra-se em perguntas que apoiam a gestão da performance comercial:

1. **Quem gera o maior valor em vendas e quem possui o maior ticket médio?**  
   Essa análise diferencia o volume total de vendas do valor médio por transação, ajudando a distinguir uma performance baseada em quantidade de vendas daquela baseada em vendas de maior valor.

2. **Qual estado lidera em valor de vendas e qual possui o maior ticket médio?**  
   A base de dados contém informações de estado e cidade, mas não possui um campo específico de região. Por isso, o estado foi utilizado como dimensão geográfica de comparação, evitando a criação de agrupamentos regionais sem fundamento nos dados.

3. **Qual modelo Porsche vende mais unidades e qual gera o maior valor em vendas?**  
   O volume de unidades e a receita respondem a diferentes questões sobre o mix de produtos: popularidade versus contribuição financeira.

4. **Como as vendas evoluem mês a mês e quais cidades mais contribuem para a receita?**  
   A receita mensal ajuda a monitorar o comportamento das vendas ao longo do tempo e possíveis efeitos de sazonalidade. Já a receita por cidade destaca a concentração geográfica em termos financeiros.

O ranking dos vendedores destaca os três maiores geradores de receita e apresenta os sete seguintes. Para identificar os líderes em ticket médio, são consideradas, sempre que possível, apenas pessoas com pelo menos duas vendas, reduzindo a influência de uma única transação com valor excepcionalmente alto.

## Histórico de prompts e alterações até a versão final

O dashboard foi desenvolvido de forma iterativa, a partir de quatro solicitações do usuário:

### Prompt 1 — Solicitação inicial

> Desenvolva um dashboard profissional de performance comercial em HTML, utilizando a planilha anexada e considerando a aba `Sanitized` como principal fonte de dados e a aba de tabela dinâmica como referência complementar. Inclua filtros para mês/ano da venda, estado, forma de pagamento e status de entrega; indicadores de valor total de vendas em USD, quantidade de vendas e ticket médio; respostas às perguntas de negócio sobre o principal vendedor, liderança geográfica e desempenho dos modelos Porsche; um ranking dos 10 principais vendedores, com destaque para os três primeiros; um gráfico de linha com a evolução das vendas ano contra ano; e um gráfico de área/Pareto 80/20 das vendas por cidade. Utilize o site internacional da Porsche como inspiração visual, com um estilo limpo, elegante, premium e minimalista. Todo o conteúdo textual do dashboard deve estar em inglês.

### Prompt 2 — Direção visual premium e evolução mensal

O design foi refinado com imagens da Porsche, uma paleta dourada mais marcante, tipografia maior e menos subtítulos e legendas desnecessários. O filtro de data mudou de mês/ano para **apenas ano**. O gráfico de tendência anual foi substituído por um gráfico de **evolução mensal das vendas**, exibindo os meses do ano selecionado. O gráfico de Pareto por cidade foi substituído por um gráfico de colunas simples.

### Prompt 3 — Indicador financeiro por cidade e filtros de seleção múltipla

O gráfico por cidade deixou de apresentar a quantidade de transações e passou a apresentar o **valor de vendas por cidade**. Todos os filtros foram transformados em controles de seleção múltipla. Os textos e rótulos das opções dos filtros passaram a utilizar a cor dourada sobre um fundo cinza-claro. A paleta geral foi alterada de branco para **cinza-claro, preto e dourado**.

### Prompt 4 — Rótulos dos meses com o ano

Os rótulos do gráfico de evolução mensal foram atualizados para incluir o ano, por exemplo, `Jan/24`, permitindo diferenciar meses de anos distintos quando múltiplos anos são selecionados.

## Preparação dos dados antes da utilização de IA

A planilha original contém duas abas: `Tabela_Dinamica` e `Sanitized`.

- A aba `Sanitized` foi selecionada como fonte oficial dos dados: **100 linhas e 12 colunas**.
- A aba `Tabela_Dinamica` apresenta uma visão pré-agregada, semelhante a uma tabela dinâmica, com células em branco e elementos de formatação. Por isso, não foi utilizada como fonte de dados em nível de transação.
- A aba `Sanitized` não apresentou valores ausentes nas 100 linhas observadas.
- O campo `SaleDateSanitized` foi convertido para o formato de data, utilizando o padrão original `YYYY-MM-DD`. O dashboard agrupa os dados por ano e mês; os dias não são utilizados como filtro.
- Os nomes exibidos dos vendedores foram padronizados para letras maiúsculas e minúsculas de forma consistente (por exemplo, variações como `kevin` e `KEVIN` são exibidas da mesma maneira).
- A estrutura de dados utilizada pelo dashboard contém os campos necessários para suas visualizações: ID da venda, data, modelo Porsche, ano do modelo, preço de venda, forma de pagamento, cidade, estado, vendedor e status de entrega. Os nomes dos clientes e a quilometragem dos veículos não são necessários para as análises solicitadas e foram omitidos da estrutura de dados do dashboard.
- Os valores de venda são apresentados em USD porque a solicitação original exigia essa moeda. A planilha não possui um campo separado de metadados que identifique a moeda; portanto, essa escolha é uma premissa de apresentação, e não uma conversão de moeda verificada de forma independente.
- Nenhum valor de venda foi convertido ou recalculado. O ticket médio é calculado dividindo-se o valor total de vendas pela quantidade de transações.

## Ferramentas e abordagem de implementação

O dashboard foi desenvolvido por meio de um fluxo de programação conversacional no ChatGPT e entregue como uma página HTML independente, utilizando JavaScript e Chart.js.

- **ChatGPT Canvas:** não utilizado.
- **Agente com uma skill (habilidade):** não utilizado.
- **Ambos:** não. O projeto não foi desenvolvido por meio de um design gerado no Canva nem de um fluxo de trabalho baseado em agente e skills. Foi uma implementação direta em HTML/CSS/JavaScript, aprimorada iterativamente por meio dos quatro prompts.
