# Predição de Avaliações Negativas no Ecossistema Olist

Solução integrada de Business Intelligence e Machine Learning para predição de avaliações negativas no ecossistema Olist, desenvolvida como entrega da Fase 2 da disciplina Projeto em Business Intelligence e Analytics (PUCRS Online, 2026).

## Pergunta de pesquisa

Quais fatores operacionais, logísticos e financeiros possuem maior peso estatístico na determinação de uma avaliação negativa no e-commerce brasileiro?

## Principais achados

1. **Tempo de entrega é o principal determinante**, respondendo por aproximadamente 52% da importância do Random Forest. Pedidos atrasados têm taxa de avaliação negativa de 73,3% contra 17,3% dos pedidos entregues no prazo. Hipótese 1 confirmada com larga margem.
2. **Razão frete/preço é o segundo driver de insatisfação**, especificamente em produtos de baixo ticket (razão média de 0,57 em ticket baixo contra 0,11 em ticket alto). Hipótese 2 confirmada.
3. **Pedidos multi-vendedor têm taxa de avaliação negativa 3x maior** (60,5% vs 20,5%), mas o canal causal originalmente proposto (multi-vendor leva a consolidação mais lenta) foi refutado pelos dados, já que pedidos multi-vendedor consolidam mais rápido (1,38 vs 2,30 dias). Hipótese 3 parcialmente confirmada, com o mecanismo real em aberto.

## Dashboards interativos

Os quatro dashboards podem ser visualizados diretamente no navegador:

- [Dashboard 0: Visão Executiva](https://rafaehlers.github.io/projetobi-olist-fase2/dashboards/dashboard_0_visao_executiva.html) (KPIs gerais, evolução temporal, distribuição de notas)
- [Dashboard 1: Hipótese 1, Atrasos e Satisfação](https://rafaehlers.github.io/projetobi-olist-fase2/dashboards/dashboard_1_hipotese_1.html)
- [Dashboard 2: Hipótese 2, Frete vs Preço em Baixo Ticket](https://rafaehlers.github.io/projetobi-olist-fase2/dashboards/dashboard_2_hipotese_2.html)
- [Dashboard 3: Hipótese 3, Pedidos Multi-Vendedor](https://rafaehlers.github.io/projetobi-olist-fase2/dashboards/dashboard_3_hipotese_3.html)

## Estrutura do repositório

| Arquivo ou diretório | Descrição |
|---|---|
| `01_etl_e_star_schema.ipynb` | ETL, engenharia de features e construção do Star Schema |
| `02_dashboards_bi.ipynb` | Geração dos quatro dashboards interativos em Plotly |
| `03_modelo_preditivo.ipynb` | Treinamento e avaliação dos modelos preditivos |
| `dashboards/` | Arquivos HTML standalone dos dashboards (links renderizados na seção acima) |
| `data/` | Data Warehouse SQLite e CSVs originais do dataset Olist |
| `olist_dw.sqlite` | Data Warehouse em Star Schema (1 tabela fato, 5 dimensões) |
| `modelo_random_forest.pkl` | Modelo Random Forest serializado para inferência |

## Stack técnico

- **ETL e manipulação tabular:** Pandas, NumPy
- **Data Warehouse:** SQLite com modelagem Star Schema (1 fato, 5 dimensões)
- **Visualização (BI):** Plotly Express e Plotly Graph Objects
- **Machine Learning:** Scikit-learn (Regressão Logística, Random Forest)
- **Ambiente de execução:** Google Colab, Jupyter
- **Versionamento:** GitHub

## Modelos treinados

| Métrica | Regressão Logística (baseline) | Random Forest (principal) |
|---|---|---|
| Acurácia | 0,7550 | 0,7887 |
| Precisão | 0,4257 | 0,4975 |
| Recall | 0,4704 | 0,3975 |
| F1-score | 0,4469 | 0,4419 |
| ROC-AUC | 0,6983 | 0,7024 |

## Dataset

Brazilian E-Commerce Public Dataset by Olist, disponível no Kaggle: https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce

Aproximadamente 100 mil pedidos realizados em marketplaces brasileiros entre 2016 e 2018.

## Autor

Rafael de Menezes Ehlers, Curso Superior de Tecnologia em Banco de Dados, PUCRS Online (2026).
