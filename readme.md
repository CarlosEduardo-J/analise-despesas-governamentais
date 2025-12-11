# 💰 Análise de Desempenho e Eficiência de Despesas Governamentais (Python/Pandas)

## 🎯 Objetivo do Projeto: Desafio com Dados Reais

Este projeto foi desenvolvido com o propósito de enfrentar um **desafio real** de Data Science: trabalhar com uma base de dados pública comumente encontrada em ambientes de trabalho—**cheia de inconsistências, formatos misturados e dados sujos (outliers e erros de registro)**.

O objetivo principal foi transformar dados brutos de despesas governamentais em *insights* de **desempenho orçamentário e eficiência de caixa**, ranqueando órgãos públicos com base na velocidade e eficácia de seus pagamentos.

## 🛠️ Aprendizados e Desafios Superados

Este projeto foi excepcionalmente desafiador e proporcionou um aprendizado profundo, especialmente nas seguintes áreas:

### 1. Limpeza e Tratamento de Dados (ETL)

* **Valores Monetários Complexos:** Foi necessário criar um robusto encadeamento de métodos (`.str.replace()`) para padronizar e converter strings monetárias (formato brasileiro `1.000,00`) para o tipo numérico `float`, corrigindo pontos e vírgulas.
* **Tratamento de Outliers e Erros:** Utilização do `.clip(lower=0)` para neutralizar valores negativos em Empenhado e Liquidado (prováveis estornos), garantindo a integridade dos cálculos.
* **Divisão por Zero:** Uso do `numpy.where` e `np.nan` para calcular as Taxas de Eficiência, tratando casos onde o denominador era zero e evitando resultados `inf` (Infinito) na média.

### 2. Geração de Métricas Diagnósticas (KPIs)

O maior valor do projeto foi ir além do gasto total, criando Indicadores-Chave de Desempenho (KPIs) essenciais para o diagnóstico:

* **Taxa de Liquidação:** (Liquidado / Empenhado) — Mede o quanto do valor prometido foi confirmado.
* **Taxa de Pagamento (KPI Principal):** (Pago / Liquidado) — **Mede a eficiência do fluxo de caixa e a gestão de passivos.**

> **Valor Adicionado:** A criação destas métricas permitiu que a análise se movesse de uma simples contagem de gastos para um diagnóstico de **eficiência** e **saúde financeira** dos órgãos.

## 📊 Principais Análises e Insights

O projeto culminou em três áreas de *insights* principais:

### 1. Ranqueamento de Eficiência de Pagamento

* Gráficos de barra que ranqueiam os órgãos pela `Taxa de Pagamento`.
* **Insight:** Identificação clara de órgãos com Taxa **$> 1.0$** (que estão ativamente pagando **Restos a Pagar** e limpando **passivos**, como o **Ministério da Fazenda**) e órgãos com baixa eficiência (Taxa **$< 0.8$**, como o **Ministério dos Direitos Humanos**), que exigem investigação.

### 2. Análise Temporal (Sazonalidade)

* Visualização da **Evolução Mensal do Valor Pago vs. Valor Liquidado**.
* **Insight:** Demonstra a **sazonalidade** do gasto governamental, com picos de saída de caixa (Valor Pago) em meses específicos, influenciados pelo pagamento de **obrigações antigas**.

### 3. Análise Descritiva de Gasto

* Ranqueamento dos **Top 10** e **10 Menores** órgãos por **Valor Pago** total, identificando a **concentração de despesas**.

---

## 🛠️ Tecnologias Utilizadas

* **Python:** Linguagem de programação principal.
* **Pandas:** Manipulação, limpeza e transformação de dados (ETL).
* **NumPy:** Tratamento de erros matemáticos e criação de lógica condicional (Taxas de Eficiência).
* **Matplotlib/Seaborn:** Visualização e geração de gráficos de ranqueamento e séries temporais.

## 📁 Estrutura do Repositório

O código foi dividido em dois notebooks para organizar o pipeline de análise (seguindo o princípio de **separação de preocupações**):

1.  **`analise_base.ipynb`:** Contém a **limpeza de dados, tratamento de outliers e geração das colunas de Taxa de Pagamento/Liquidação**.
2.  **`analise_final.ipynb`:** Contém a **análise descritiva, análise temporal e a geração dos gráficos de ranqueamento (Top/Menores 10 Eficiência)**, focando na apresentação dos *insights*.