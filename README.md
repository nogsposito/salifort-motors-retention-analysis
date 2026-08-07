🇧🇷 Português | [🇺🇸 English](https://github.com/nogsposito/salifort-motors-retention-analysis/blob/main/README.en.md)

# Salifort Motors — Previsão de Turnover de Funcionários

Modelo preditivo de rotatividade de colaboradores construído com Regressão Logística, Árvore de Decisão e Random Forest, desenvolvido como projeto final (Capstone) do **Google Advanced Data Analytics Professional Certificate**.

![Python](https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-data%20wrangling-150458?logo=pandas&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-modeling-F7931E?logo=scikitlearn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-benchmark-blue)
![Jupyter](https://img.shields.io/badge/Jupyter-notebook-F37626?logo=jupyter&logoColor=white)

---

## O problema de negócio

A **Salifort Motors**, fabricante fictícia de veículos de energia alternativa com mais de 100.000 funcionários, enfrenta uma taxa de rotatividade elevada, o que gera custos recorrentes de recrutamento e treinamento. O departamento de RH quer entender **por que os funcionários saem** e **antecipar quem está em risco de sair**, para agir antes do desligamento e não depois dele.

Este projeto responde a essas duas perguntas construindo modelos de classificação sobre um histórico de **14.999 funcionários** e **10 variáveis** autorrelatadas (satisfação, avaliação de desempenho, carga de projetos, horas trabalhadas, tempo de casa, salário, entre outras).

## Principais resultados

| Modelo | AUC | Precisão | Recall | F1-score | Acurácia |
|---|---|---|---|---|---|
| Regressão Logística | — | 79% | 82% | 80% | 82% |
| Árvore de Decisão | 95,6% | 83,1% | 90,3% | 86,5% | 95,3% |
| **Random Forest** | **93,4%** | **91,3%** | **90,4%** | **88,5%** | **96,6%** |

A Random Forest foi escolhida como modelo final por apresentar o equilíbrio mais consistente entre as métricas, mesmo com a Árvore de Decisão alcançando uma AUC ligeiramente superior.

## O que os dados revelam

- **Sobrecarga de trabalho é o principal preditor de saída.** Número de projetos simultâneos, horas mensais trabalhadas e tempo de casa concentram a maior importância nos dois modelos baseados em árvore.
- **Existem dois perfis de saída bem distintos:** funcionários pouco satisfeitos com pouco tempo de casa, e funcionários com boas avaliações mas sobrecarregados, que saem apesar do bom desempenho.
- **Quatro anos de empresa é um ponto crítico.** Colaboradores nessa faixa de tenure apresentam quedas acentuadas de satisfação, sugerindo um gargalo de progressão de carreira.
- **Todos os funcionários com 7 projetos simultâneos deixaram a empresa** — um sinal de risco praticamente determinístico identificado na análise exploratória.
- **Promoções são raras e pouco associadas à carga horária**, o que reforça a hipótese de que reconhecimento e crescimento não acompanham o esforço.

## Abordagem técnica

**Limpeza de dados:** identificação e remoção de 3.008 registros duplicados (~20% da base), tratamento de outliers em `tenure` via análise de quartis, padronização de nomes de colunas.

**Prevenção de data leakage:** as primeiras versões dos modelos baseados em árvore atingiram métricas altas o suficiente para levantar suspeita de vazamento de dados. A variável `average_monthly_hours` foi substituída por uma feature derivada (`overworked`, funcionários acima de 175h/mês) e `satisfaction_level` foi removida do conjunto de treino nos modelos finais, tornando as previsões mais realistas para um cenário de produção.

**Modelagem:** Regressão Logística como baseline interpretável; Árvore de Decisão e Random Forest com tuning de hiperparâmetros via `GridSearchCV` e validação cruzada. Como as classes são desbalanceadas (83% ficaram / 17% saíram), a avaliação priorizou Precision, Recall, F1-score e AUC-ROC em vez de acurácia isolada.

## Stack técnico

`Python` · `pandas` · `numpy` · `scikit-learn` · `XGBoost` · `matplotlib` · `seaborn` · `Jupyter Notebook`

## Estrutura do repositório

```text
├── data/
│   └── HR_comma_sep.csv
│
├── notebooks/
│   └── Salifort_Motors_Capstone.ipynb
│
├── reports/
│   ├── Salifort Motors Documento PACE.pdf
│   └── Salifort Motors Sumário Executivo.pdf
│
└── README.md
```

## Documentação

- 📑 [Documento PACE](reports/Salifort%20Motors%20Documento%20PACE.pdf) — planejamento do projeto, objetivos de negócio e estratégia, seguindo o framework **PACE (Plan, Analyze, Construct, Execute)**.
- 📊 [Sumário Executivo](reports/Salifort%20Motors%20Sumário%20Executivo.pdf) — principais resultados e recomendações de negócio em linguagem não técnica, voltado a stakeholders.

## Como reproduzir

```bash
git clone https://github.com/nogsposito/salifort-motors-retention-analysis/edit/main/README.md
cd salifort-motors-turnover
pip install pandas numpy scikit-learn xgboost matplotlib seaborn jupyter
jupyter notebook notebooks/Salifort_Motors_Capstone.ipynb
```

## Próximos passos

- Aplicar **SHAP** para interpretar previsões individuais do modelo.
- Explorar **K-Means** para identificar perfis distintos de funcionários em risco.
- Comparar o desempenho final com **XGBoost**.
- Investigar novas variáveis: distância do deslocamento, formato de trabalho (remoto/presencial) e histórico de bônus.

---

Projeto desenvolvido como parte do **Google Advanced Data Analytics Professional Certificate**.
