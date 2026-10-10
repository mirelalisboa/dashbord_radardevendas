# Radar de vendas

Dashboard interativo para a atividade de Fundamentos de IA e Análise de Dados. A página investiga a evolução mensal do faturamento e compara categorias e regiões, com filtros, pesquisa, ordenação e exportação.

Além dos gráficos, a página apresenta uma tabela de produtos mais vendidos (ordenada por unidades), destaca o produto líder e mostra uma tabela-resumo com uma linha para cada região disponível. Ao informar a data inicial, o período segue automaticamente até o último dia disponível na base; a data final pode ser ajustada manualmente.

## Como executar

Abra [`public/index.html`](public/index.html) diretamente no navegador. A base demonstrativa já aparece na tela e não depende de `fetch`. Para importar outra base, clique em **Importar CSV**; o arquivo é processado localmente no navegador.

As bibliotecas Chart.js 4.4.4 e Papa Parse 5.4.1 são carregadas por CDN, portanto é necessário acesso à internet para que os gráficos e a importação funcionem. A fonte visual também é carregada pela internet.

## Dados e regras

`public/dados-exemplo.csv` possui 200 registros fictícios distribuídos de janeiro a dezembro de 2025. Cada linha representa uma venda de um produto. As colunas são `id_venda`, `data` (AAAA-MM-DD), `produto`, `categoria`, `regiao`, `quantidade` e `preco_unitario`.

- Faturamento da linha = `quantidade × preco_unitario`.
- Faturamento total = soma do faturamento das linhas filtradas.
- Quantidade de vendas = quantidade de `id_venda` únicos.
- Unidades vendidas = soma de `quantidade`.
- Ticket médio = faturamento total ÷ quantidade de vendas. Quando não há vendas, o valor exibido é R$ 0,00.

Na importação, são descartadas linhas sem ID, categoria ou região, com data inválida, número ausente/não numérico ou quantidade/preço negativos. Zeros válidos são mantidos. O dashboard não remove duplicatas automaticamente, pois cada linha pode ter significado próprio; apenas IDs repetidos são contados uma vez no indicador de vendas.

## CSV próprio

Use a primeira linha com os mesmos nomes de coluna. Números podem usar ponto decimal (por exemplo, `24.90`) ou formato brasileiro simples (por exemplo, `24,90`). Para evitar conflito com a vírgula decimal, prefira separar as colunas com ponto e vírgula ao usar formato brasileiro.

## Publicação no Render via GitHub

1. Crie um repositório no GitHub e envie este projeto para a branch desejada.
2. No Render, crie um novo **Static Site** e conecte o repositório.
3. Configure a branch que contém o projeto.
4. Deixe **Root Directory** vazio.
5. Use `echo "Site pronto"` em **Build Command**.
6. Use `public` em **Publish Directory** e publique.

## Verificação didática

Para conferir os cálculos manualmente, uma linha com quantidade 2 e preço R$ 24,90 deve gerar R$ 49,80. Em filtros sem registros, os cartões voltam a zero e a tabela mostra uma mensagem clara. O dashboard foi implementado sem backend, banco de dados, React ou etapa de compilação.

## Base regional fictícia

O arquivo `vendas_hamburgueria_regional.csv` foi gerado a partir de `vendas_hamburgueria.csv`, sem alterar o arquivo original. Ele acrescenta as colunas `regiao`, `loja` e `endereco`, distribuindo as 1.367 vendas de forma determinística entre as 27 unidades federativas. Os nomes das lojas e endereços são fictícios e servem apenas para demonstração.

O dashboard também disponibiliza uma cópia em `public/dados/vendas_hamburgueria_regional.csv`. Ao abrir `public/index.html` por um servidor local, ela é carregada automaticamente; ao abrir diretamente como arquivo, use **Importar CSV** e selecione essa cópia.
