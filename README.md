<div align="center">

# 📊 Radar de Vendas

### Dashboard interativo para analisar faturamento, categorias e regiões — direto no navegador.

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org/pt-BR/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org/pt-BR/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript)
[![Chart.js](https://img.shields.io/badge/Chart.js-4.4.4-FF6384?style=for-the-badge&logo=chartdotjs&logoColor=white)](https://www.chartjs.org/)
[![Papa Parse](https://img.shields.io/badge/Papa%20Parse-5.4.1-8E44AD?style=for-the-badge)](https://www.papaparse.com/)
[![Render](https://img.shields.io/badge/Deploy-Render-46E3B7?style=for-the-badge&logo=render&logoColor=black)](https://render.com/)

<br>

[![▶ Abrir o Dashboard](https://img.shields.io/badge/▶_Abrir_o_Dashboard-public/index.html-2ea44f?style=for-the-badge)](public/index.html)
[![📁 Dados de exemplo](https://img.shields.io/badge/📁_Dados_de_exemplo-dados--exemplo.csv-0366d6?style=for-the-badge)](public/dados-exemplo.csv)
[![🍔 Base regional](https://img.shields.io/badge/🍔_Base_regional-hamburgueria-e36209?style=for-the-badge)](public/dados/vendas_hamburgueria_regional.csv)

</div>

---

## 📖 Sobre o projeto

O **Radar de Vendas** é um dashboard interativo criado para a atividade de **Fundamentos de IA e Análise de Dados**. Ele investiga a **evolução mensal do faturamento** e **compara categorias e regiões**, com filtros, pesquisa, ordenação e exportação.

> 💡 **Sem complicação:** o projeto foi feito **sem backend, sem banco de dados, sem React e sem etapa de compilação**. É só abrir o HTML e usar!

---

## 📚 Sumário

- [✨ O que o dashboard mostra](#-o-que-o-dashboard-mostra)
- [🚀 Como executar](#-como-executar)
- [🧮 Dados e regras de cálculo](#-dados-e-regras-de-cálculo)
- [📥 Usando seu próprio CSV](#-usando-seu-próprio-csv)
- [🍔 Base regional fictícia](#-base-regional-fictícia)
- [🌐 Publicação no Render via GitHub](#-publicação-no-render-via-github)
- [✅ Verificação didática](#-verificação-didática)

---

## ✨ O que o dashboard mostra

| Recurso | Descrição |
|---|---|
| 📈 **Gráficos** | Evolução mensal do faturamento e comparação entre categorias e regiões |
| 🏆 **Produtos mais vendidos** | Tabela ordenada por unidades vendidas, com destaque para o **produto líder** |
| 🗺️ **Resumo por região** | Tabela com uma linha para cada região disponível na base |
| 🔎 **Filtros e pesquisa** | Refine os dados por período, categoria, região e texto |
| ↕️ **Ordenação** | Organize as tabelas pela coluna desejada |
| 💾 **Exportação** | Exporte os resultados filtrados |
| 📅 **Período inteligente** | Ao informar a **data inicial**, o período segue automaticamente até o **último dia disponível** na base. A **data final** pode ser ajustada manualmente |

---

## 🚀 Como executar

<div align="center">

[![Abrir index.html](https://img.shields.io/badge/👉_Abrir-public/index.html-2ea44f?style=for-the-badge)](public/index.html)

</div>

**É só abrir [`public/index.html`](public/index.html) diretamente no navegador.** 🎉

- ✅ A **base demonstrativa** já aparece na tela e **não depende de `fetch`**.
- 📤 Para usar outra base, clique em **Importar CSV**. O arquivo é processado **localmente no navegador** (nada é enviado para servidores).

> ⚠️ **Atenção:** as bibliotecas **Chart.js 4.4.4** e **Papa Parse 5.4.1** (e a fonte visual) são carregadas por **CDN**. Por isso, é necessário **acesso à internet** para que os gráficos e a importação funcionem.

---

## 🧮 Dados e regras de cálculo

O arquivo [`public/dados-exemplo.csv`](public/dados-exemplo.csv) possui **200 registros fictícios**, distribuídos de **janeiro a dezembro de 2025**. Cada linha representa **uma venda de um produto**.

### 🗂️ Colunas do CSV

| Coluna | Formato / Descrição |
|---|---|
| `id_venda` | Identificador da venda |
| `data` | Data no formato `AAAA-MM-DD` |
| `produto` | Nome do produto |
| `categoria` | Categoria do produto |
| `regiao` | Região da venda |
| `quantidade` | Quantidade vendida |
| `preco_unitario` | Preço de cada unidade |

### 📐 Fórmulas utilizadas

| Indicador | Como é calculado |
|---|---|
| 💰 **Faturamento da linha** | `quantidade × preco_unitario` |
| 💵 **Faturamento total** | Soma do faturamento das linhas filtradas |
| 🧾 **Quantidade de vendas** | Quantidade de `id_venda` **únicos** |
| 📦 **Unidades vendidas** | Soma de `quantidade` |
| 🎯 **Ticket médio** | Faturamento total ÷ quantidade de vendas *(se não houver vendas, exibe **R$ 0,00**)* |

### 🧹 O que acontece na importação

❌ **São descartadas** as linhas:

- sem ID, categoria ou região;
- com data inválida;
- com número ausente ou não numérico;
- com quantidade ou preço **negativos**.

✅ **São mantidos:** zeros válidos.

ℹ️ **Duplicatas:** o dashboard **não remove duplicatas automaticamente**, pois cada linha pode ter significado próprio. Apenas **IDs repetidos** são contados **uma única vez** no indicador de vendas.

---

## 📥 Usando seu próprio CSV

1. Use a **primeira linha** com os **mesmos nomes de coluna** da tabela acima.
2. Números podem usar **ponto decimal** (ex.: `24.90`) ou **formato brasileiro simples** (ex.: `24,90`).
3. Ao usar o formato brasileiro, **prefira separar as colunas com ponto e vírgula (`;`)** para evitar conflito com a vírgula decimal.

**Exemplo com ponto e vírgula:**

```csv
id_venda;data;produto;categoria;regiao;quantidade;preco_unitario
1;2025-01-15;X-Burger;Lanches;Sudeste;2;24,90
```

---

## 🍔 Base regional fictícia

O arquivo `vendas_hamburgueria_regional.csv` foi gerado a partir de `vendas_hamburgueria.csv`, **sem alterar o arquivo original**.

- ➕ Acrescenta as colunas **`regiao`**, **`loja`** e **`endereco`**.
- 🗺️ Distribui as **1.367 vendas** de forma determinística entre as **27 unidades federativas**.
- 🏪 Os nomes das lojas e os endereços são **fictícios** e servem apenas para demonstração.

O dashboard também disponibiliza uma cópia em [`public/dados/vendas_hamburgueria_regional.csv`](public/dados/vendas_hamburgueria_regional.csv).

| Como você abriu o dashboard | O que acontece |
|---|---|
| 🖥️ Por um **servidor local** | A cópia é **carregada automaticamente** |
| 📂 Direto como **arquivo** (`file://`) | Use **Importar CSV** e selecione essa cópia |

---

## 🌐 Publicação no Render via GitHub

<div align="center">

[![Criar repositório no GitHub](https://img.shields.io/badge/1️⃣_GitHub-Criar_repositório-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/new)
[![Abrir o Render](https://img.shields.io/badge/2️⃣_Render-Novo_Static_Site-46E3B7?style=for-the-badge&logo=render&logoColor=black)](https://dashboard.render.com/static/new)

</div>

1. 🐙 Crie um repositório no **GitHub** e envie este projeto para a branch desejada.
2. 🌐 No **Render**, crie um novo **Static Site** e conecte o repositório.
3. 🌿 Configure a **branch** que contém o projeto.
4. 📂 Deixe **Root Directory** vazio.
5. 🔨 Em **Build Command**, use:
   ```bash
   echo "Site pronto"
   ```
6. 🚀 Em **Publish Directory**, use `public` e clique em publicar.

| Campo no Render | Valor |
|---|---|
| **Root Directory** | *(vazio)* |
| **Build Command** | `echo "Site pronto"` |
| **Publish Directory** | `public` |

---

## ✅ Verificação didática

Quer conferir se os cálculos estão corretos? Faça o teste manual:

> 🧪 Uma linha com **quantidade 2** e **preço R$ 24,90** deve gerar **R$ 49,80**.

- 🔄 Em **filtros sem registros**, os cartões voltam a **zero** e a tabela mostra uma **mensagem clara**.
- 🧱 O dashboard foi implementado **sem backend, banco de dados, React ou etapa de compilação**.

---

<div align="center">

**Feito com 📊 e ☕ para a atividade de Fundamentos de IA e Análise de Dados**

[![Voltar ao topo](https://img.shields.io/badge/⬆_Voltar_ao_topo-555555?style=for-the-badge)](#-radar-de-vendas)

</div>
