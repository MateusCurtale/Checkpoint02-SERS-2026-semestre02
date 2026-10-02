# Checkpoint02-SERS-2026-semestre02
Está atividade explora duas API's e a partir delas foram desenvolvidas duas tarefas: Uma de regressão e outra de classificação. Também foram desenvolvidos três algoritmos diferentes em cada tarefas e estes foram comparados.

## Objetivo

Este repositório contém a solução da avaliação com duas tarefas independentes:

1. **Classificação da fonte renovável** usando dados públicos do SIGA/ANEEL.
2. **Regressão da radiação solar** usando a API histórica Open-Meteo para Petrolina (PE).

Cada tarefa compara três algoritmos, totalizando seis modelos.

## Estrutura

- `Checkpoint_2_APIs_Energias_ML.ipynb` — notebook completo e executável em ordem.
- `aneel_classificacao_orange.csv` — gerado pela consulta pública da ANEEL.
- `meteo_regressao_orange.csv` — gerado pela consulta histórica da Open-Meteo.
- `requirements.txt` — bibliotecas utilizadas.

## Tarefa 1 — Classificação

Fonte: SIGA — ANEEL.

Entradas:
- `potencia_kw`
- `latitude`
- `longitude`

Alvo:
- `fonte`

Classes:
- Solar
- Eólica
- Hidráulica

Divisão:
- 80% treino
- 20% teste
- `random_state=42`
- estratificada

Algoritmos:
- Regressão Logística
- KNN
- Random Forest

Métricas:
- Accuracy
- Precision macro
- Recall macro
- F1 macro
- matriz de confusão

## Tarefa 2 — Regressão

Fonte: API histórica Open-Meteo.

Local:
- Petrolina, PE
- aproximadamente -9,39 / -40,50

Período:
- 01/04/2025 a 30/06/2025

Fuso:
- America/Recife

Horários:
- 7h até 17h

Entradas:
- temperatura
- umidade
- nuvens
- vento
- hora

Alvo:
- `radiacao_w_m2`

Divisão:
- primeiras 80% das horas para treino
- últimas 20% para teste
- ordem temporal preservada

Algoritmos:
- Regressão Linear
- Random Forest Regressor
- Gradient Boosting Regressor

Métricas:
- MAE
- MSE
- R²

## Como executar

### Google Colab

1. Abra o Google Colab.
2. Faça upload de `Checkpoint_2_APIs_Energias_ML.ipynb`.
3. Execute as células na ordem.
4. As consultas públicas gerarão automaticamente os dois CSVs.
5. Preencha nome e matrícula na primeira célula.
6. Salve o notebook com os resultados.

### Instalação local

```bash
pip install -r requirements.txt
```

Depois abra o notebook com Jupyter ou VS Code.

## APIs

ANEEL — SIGA:
https://dadosabertos.aneel.gov.br/dataset/siga-sistema-de-informacoes-de-geracao-da-aneel

Open-Meteo — Historical Weather API:
https://open-meteo.com/en/docs/historical-weather-api

## Conclusões

As conclusões numéricas devem ser lidas nas tabelas produzidas pelo notebook após a consulta das APIs e execução dos seis modelos.

Na classificação, potência e localização podem apresentar relação com a fonte, mas não constituem uma identificação direta da tecnologia.

Na regressão, a hora do dia é relevante por causa do ciclo diário da radiação solar. A radiação estimada também não deve ser confundida com geração elétrica de um sistema fotovoltaico, pois geração depende de características específicas da instalação e de suas perdas.

## Segurança

As consultas utilizadas não precisam de tokens. Nenhuma senha, chave ou credencial deve ser colocada neste repositório.
