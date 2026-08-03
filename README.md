# Salifort Motors: Previsão de Rotatividade de Funcionários (Employee Turnover)

## Visão Geral do Projeto
Este repositório contém um projeto completo de análise de dados e machine learning focado em recursos humanos. Ele foi desenvolvido como projeto final (Capstone) para o certificado Google Advanced Data Analytics, criado para simular fielmente o trabalho conduzido por profissionais de dados no mercado.

O projeto foca na **Salifort Motors**, uma fabricante fictícia de veículos de energia alternativa com sede na França. A empresa possui uma força de trabalho global de mais de 100.000 funcionários e é líder no cruzamento de energia alternativa e automóveis.

Atualmente, a empresa está lidando com uma alta taxa de rotatividade (turnover), incluindo funcionários que pedem demissão e aqueles que são desligados.

Considerando que a Salifort investe significativamente no recrutamento, treinamento e qualificação de seus colaboradores, essa elevada rotatividade representa um problema financeiramente custoso. O objetivo deste projeto é analisar os resultados de uma pesquisa recente com os funcionários e construir um modelo preditivo capaz de identificar quais colaboradores têm maior probabilidade de deixar a empresa. Com isso, busca-se fornecer insights para que a liderança compreenda os fatores associados ao turnover e desenvolva estratégias para aumentar a retenção de talentos.

---

## Dicionário de Dados

A análise utiliza o conjunto de dados `HR_capstone_dataset.csv`, composto por informações autorrelatadas pelos funcionários.

- **14.999 registros**, onde cada linha representa um funcionário.
- **10 variáveis** relacionadas ao perfil, desempenho e histórico dos colaboradores.

### Variáveis

- **`satisfaction_level` (float):** Nível de satisfação do funcionário, variando entre 0 e 1.
- **`last_evaluation` (float):** Nota da última avaliação de desempenho, variando entre 0 e 1.
- **`number_project` (int):** Número de projetos nos quais o funcionário atua.
- **`average_monthly_hours` (int):** Média de horas trabalhadas por mês.
- **`time_spend_company` (int):** Tempo de permanência do funcionário na empresa (anos).
- **`work_accident` (int):** Indica se o funcionário sofreu acidente de trabalho (`0 = Não`, `1 = Sim`).
- **`left` (int):** Variável alvo que indica se o funcionário deixou a empresa (`0 = Não`, `1 = Sim`).
- **`promotion_last_5years` (int):** Indica se o funcionário recebeu promoção nos últimos cinco anos.
- **`department` (string):** Departamento onde o funcionário trabalha.
- **`salary` (string):** Faixa salarial (`low`, `medium` ou `high`).

---

## Metodologia

Este projeto foi desenvolvido seguindo o framework **PACE (Plan, Analyze, Construct, Execute)**.

As principais etapas foram:

1. **Análise Exploratória dos Dados (EDA):**
   - Limpeza dos dados;
   - Tratamento de valores inconsistentes;
   - Análise estatística;
   - Visualização de distribuições e correlações.

2. **Construção e Avaliação dos Modelos de Machine Learning:**
   - Regressão Logística;
   - Árvore de Decisão (Decision Tree);
   - Random Forest;
   - XGBoost.

Os modelos foram comparados utilizando métricas apropriadas para classificação, buscando identificar a melhor abordagem para prever a saída de funcionários.

---

## Resultados da Análise e Principais Insights

> **⚠️ Atualizar esta seção após concluir  análise.**

- **Desempenho dos Modelos:** Descreva o modelo que apresentou o melhor desempenho e as principais métricas (Accuracy, Precision, Recall, F1-score e ROC-AUC).
- **Principais Variáveis:** Identifique quais atributos tiveram maior importância na previsão da saída dos funcionários.
- **Insights de Negócio:** Destaque os principais padrões encontrados durante a análise exploratória.

---

## Recomendações e Próximos Passos

> **⚠️ Atualizar esta seção com base nos resultados obtidos.**

Exemplos:

- Implementar estratégias para reduzir a sobrecarga de trabalho em equipes críticas.
- Desenvolver políticas de retenção voltadas para colaboradores com maior risco de desligamento.
- Revisar critérios de promoção e desenvolvimento profissional.
- Monitorar continuamente os indicadores identificados como mais relevantes pelo modelo.

---

## Estrutura do Repositório

```text
├── data/
│   └── HR_capstone_dataset.csv
│
├── notebooks/
│   └── Salifort_Motors_Capstone.ipynb
│
├── docs/
│   ├── PACE_Strategy_Document.pdf
│   └── Executive_Summary.pdf
│
└── README.md
```

### Descrição dos arquivos

- **`data/`**: Contém o conjunto de dados original utilizado no projeto.
- **`notebooks/`**: Notebook Jupyter com todo o processo de limpeza dos dados, análise exploratória, engenharia de atributos, treinamento e avaliação dos modelos.
- **`reports/`**
  - **`PACE_Strategy_Document.pdf`**: Documento que descreve o planejamento, análise, construção e execução do projeto seguindo o framework PACE.
  - **`Executive_Summary.pdf`**: Resumo executivo destinado à liderança da empresa, apresentando os principais resultados, limitações dos modelos e recomendações de negócio em linguagem não técnica.
