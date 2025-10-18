# 📊 Projeto de Análise de Aplicativos - Grupo Q

**Autor:** Victor Flausino  
**Data:** Outubro/2025  
**Ferramentas:** Google Colab · DuckDB · Power BI  


---

## 🧰  Tecnologias Utilizadas
- **Python (Google Colab)** – para limpeza e tratamento com DuckDB  
- **DuckDB SQL Engine** – processamento de grandes CSVs com alta performance  
- **Power BI** – visualização, modelagem e storytelling de dados  
- **Markdown + GitHub** – documentação e publicação do projeto  


---

## 🧠 1. Contexto do Desafio

Este projeto foi desenvolvido com base em dados públicos do Google Play Store (até agosto/2018), com o objetivo de apoiar a diretoria de uma empresa de **aplicativos educacionais** a entender:

- Quais categorias têm **maior potencial de crescimento**  
- Como está a **percepção dos usuários**  
- Quais fatores influenciam a **aceitação e o engajamento** dos apps  

O trabalho incluiu todo o ciclo de dados: **extração, tratamento, modelagem e análise visual**, com aplicação de técnicas analíticas para gerar **insights de negócio**.

---

## ⚙️ 2. Preparação e Modelagem dos Dados

### Bases utilizadas
- `googleplaystore.csv` — dados dos aplicativos (instalações, preço, categoria, rating etc.)  
- `googleplaystore_user_reviews.csv` — avaliações e sentimentos de usuários.  

### Transformações aplicadas (ETL em DuckDB via Google Colab)
- **Padronização textual:** correção de capitalização (`Category`, `App`) e remoção de espaços com `TRIM()`.  
- **Correção de tipos:** conversão de campos numéricos e remoção de símbolos (“+”, “,”, “$”).  
- **Imputação de nulos:** `Rating` com valor “NaN” substituído pela **média da categoria**.  
- **Datas:** conversão do campo `"Last Updated"` para data e criação da coluna `Ano_Atualizacao`.  
- **Novas métricas criadas:**
  - `Reach_Band` (baixo / médio / alto) — faixa de instalações.  
  - `Revenue_Potential` — potencial de receita (`Installs * Price` para apps pagos).  

---

## 📊 3. Estrutura do Dashboard

O painel foi construído no **Power BI** e dividido em **três páginas principais**, cada uma com propósito claro de storytelling.

---

### 🟦 Página 1 – Visão Geral
**Objetivo:** apresentar uma visão macro do mercado de aplicativos.

**Principais indicadores:**
- Total de Apps  
- Instalações Totais  
- Rating Médio  
- Total de Reviews  
- NPS Estimado  

**Principais análises:**
- Evolução temporal das notas médias  
- Correlação entre engajamento e popularidade  
- Taxa de engajamento (reviews / installs)  

📸 **Screenshot:**
![Visão Geral](2_dashboard/screenshots/tela_1_visao_geral.png)

---

### 🟩 Página 2 – Análise de Mercado e Crescimento
**Objetivo:** identificar categorias com **maior potencial de investimento**.

**KPIs:**
- Categoria com Maior Crescimento  
- % de Apps Atualizados recentemente (em relação a 2018)  
- Receita Potencial Total  
- Índice de Potencial de Crescimento  

**Cálculo do Índice de Potencial:**
