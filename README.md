````markdown
# Salifort Motors: Previsão de Rotatividade de Funcionários (Employee Turnover)

> **Projeto desenvolvido como Capstone do Google Advanced Data Analytics Professional Certificate.**

## 📄 Documentação

Além do notebook com toda a análise, este repositório também inclui dois documentos produzidos ao longo do projeto:

- 📑 **[Documento PACE](reports/Salifort%20Motors%20Documento%20PACE.pdf)** — Documento que descreve o planejamento do projeto, os objetivos de negócio e a estratégia adotada seguindo o framework **PACE (Plan, Analyze, Construct, Execute)**.
- 📊 **[Sumário Executivo](reports/Salifort%20Motors%20Sumário%20Executivo.pdf)** — Resumo executivo elaborado para stakeholders, apresentando os principais resultados, conclusões e recomendações de negócio em linguagem não técnica.

---

## Visão Geral do Projeto

Este repositório contém um projeto completo de análise de dados e machine learning focado em People Analytics. Ele foi desenvolvido como projeto final (Capstone) do certificado **Google Advanced Data Analytics**, simulando um caso real de negócio enfrentado por uma equipe de Ciência de Dados.

O projeto analisa a **Salifort Motors**, uma fabricante fictícia de veículos de energia alternativa com sede na França. A empresa possui uma força de trabalho global de mais de 100.000 funcionários e enfrenta uma elevada taxa de rotatividade (turnover), tanto por desligamentos voluntários quanto involuntários.

Como a empresa investe significativamente no recrutamento, treinamento e desenvolvimento de seus colaboradores, compreender os fatores associados ao turnover tornou-se uma necessidade estratégica.

O objetivo deste projeto é analisar os dados históricos dos funcionários, identificar os fatores mais relevantes relacionados ao desligamento e desenvolver modelos de classificação capazes de prever quais colaboradores apresentam maior probabilidade de deixar a empresa. Além da construção dos modelos, a análise busca gerar insights que possam apoiar decisões voltadas à retenção de talentos.

---

## Dicionário de Dados

A análise utiliza o conjunto de dados `HR_capstone_dataset.csv`.

- **14.999 registros**, onde cada linha representa um funcionário.
- **10 variáveis** relacionadas ao perfil, desempenho e histórico dos colaboradores.

### Variáveis

- **`satisfaction_level`** **(float):** Nível de satisfação do funcionário, variando entre 0 e 1.
- **`last_evaluation`** **(float):** Nota da última avaliação de desempenho, variando entre 0 e 1.
- **`number_project`** **(int):** Número de projetos nos quais o funcionário atua.
- **`average_monthly_hours`** **(int):** Média de horas trabalhadas por mês.
- **`time_spend_company`** **(int):** Tempo de permanência do funcionário na empresa (anos).
- **`work_accident`** **(int):** Indica se o funcionário sofreu acidente de trabalho (`0 = Não`, `1 = Sim`).
- **`left`** **(int):** Variável alvo que indica se o funcionário deixou a empresa (`0 = Permaneceu`, `1 = Saiu da empresa`).
- **`promotion_last_5years`** **(int):** Indica se o funcionário recebeu promoção nos últimos cinco anos.
- **`department`** **(string):** Departamento onde o funcionário trabalha.
- **`salary`** **(string):** Faixa salarial (`low`, `medium` ou `high`).

---

## Metodologia

Este projeto foi desenvolvido seguindo o framework **PACE (Plan, Analyze, Construct, Execute)**.

As principais etapas foram:

1. **Análise Exploratória dos Dados (EDA)**
   - Limpeza dos dados;
   - Tratamento de inconsistências;
   - Análise estatística;
   - Visualizações para identificação de padrões.

2. **Engenharia de Atributos**
   - Preparação dos dados para modelagem;
   - Codificação das variáveis categóricas.

3. **Construção dos Modelos**
   - Regressão Logística;
   - Árvore de Decisão (Decision Tree);
   - Random Forest.

4. **Otimização e Avaliação**
   - Ajuste de hiperparâmetros utilizando **GridSearchCV**;
   - Comparação dos modelos utilizando métricas de classificação.

## Resultados da Análise

Após comparar diferentes algoritmos de classificação, verificou-se que os modelos baseados em árvores apresentaram desempenho significativamente superior ao modelo de Regressão Logística. A **Random Forest** obteve o melhor desempenho geral na tarefa de prever o turnover dos funcionários.

### Desempenho dos Modelos

| Modelo | Accuracy | Precision | Recall | F1-Score |
|---------|---------:|----------:|--------:|----------:|
| Regressão Logística | 83% | 80% | 83% | 80% |
| Árvore de Decisão | 96,2% | 87,0% | 90,4% | 88,7% |
| **Random Forest** | **Melhor desempenho geral** | — | — | — |

### Principais Insights

A análise exploratória e os modelos de Machine Learning indicaram que funcionários com **baixa satisfação**, **maior carga de trabalho**, **elevado número de projetos simultâneos** e **longas jornadas mensais** apresentam maior probabilidade de deixar a empresa.

Outro padrão observado foi o aumento do risco de desligamento entre colaboradores com aproximadamente **quatro anos de empresa**, sugerindo um possível momento crítico relacionado ao desenvolvimento profissional ou à progressão de carreira.

A análise de importância das variáveis mostrou que fatores relacionados à satisfação, desempenho e carga de trabalho possuem influência significativamente maior na previsão do turnover do que características demográficas ou organizacionais.

## Recomendações

Os resultados sugerem que a empresa pode reduzir sua taxa de rotatividade por meio de iniciativas voltadas ao equilíbrio da carga de trabalho e ao desenvolvimento profissional dos colaboradores. Limitar o número de projetos simultâneos, revisar políticas relacionadas às horas extras e tornar mais transparentes as expectativas sobre carga de trabalho podem contribuir para aumentar a satisfação dos funcionários.

Além disso, recomenda-se acompanhar mais de perto colaboradores com aproximadamente quatro anos de empresa, oferecendo oportunidades de crescimento e reconhecimento profissional. Por fim, os critérios de avaliação de desempenho devem priorizar a qualidade das contribuições dos funcionários, evitando que avaliações elevadas estejam excessivamente associadas apenas a jornadas de trabalho muito extensas.

## Próximos Passos

Como continuidade deste projeto, algumas possibilidades incluem:

- Avaliar o impacto da variável `last_evaluation` na ocorrência de possível **data leakage**;
- Aplicar técnicas de interpretabilidade, como **SHAP**, para explicar individualmente as previsões dos modelos;
- Explorar modelos de agrupamento (**K-Means**) para identificar perfis distintos de funcionários;
- Comparar os resultados com outros algoritmos de classificação, como **XGBoost**.

## Estrutura do Repositório

```text
├── data/
│   └── HR_capstone_dataset.csv
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

### Descrição dos Arquivos

- **`data/`**: Contém o conjunto de dados utilizado na análise.
- **`notebooks/`**: Notebook Jupyter com todo o pipeline de limpeza, análise exploratória, engenharia de atributos, modelagem e avaliação dos modelos.
- **`reports/`**
  - **`Salifort Motors Documento PACE.pdf`**: Documento que descreve o planejamento e a estratégia do projeto seguindo o framework PACE.
  - **`Salifort Motors Sumário Executivo.pdf`**: Resumo executivo com os principais resultados, limitações e recomendações de negócio para stakeholders.
- **`README.md`**: Documentação principal do projeto.
````
