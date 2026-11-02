# OilyGiant: Melhor região para novos poços de petróleo

Projeto da Sprint 10 (Aprendizado de Máquina) do curso de Ciência de Dados.

## Contexto

A OilyGiant é uma empresa de mineração de petróleo. O objetivo deste projeto é **identificar a região com maior margem de lucro** para o desenvolvimento de novos poços, usando um modelo de regressão para prever o volume de reservas e a técnica de **Bootstrapping** para avaliar lucro potencial e risco.

## Objetivos

1. Carregar e explorar os dados de poços de três regiões.
2. Construir um modelo que preveja o volume de reservas de novos poços.
3. Selecionar os poços com maiores valores previstos.
4. Calcular o lucro de cada região e escolher a mais vantajosa.
5. Avaliar lucro médio, intervalo de confiança e risco de prejuízo com Bootstrapping.

## Dados

Três conjuntos de dados, um por região, com amostras de poços de petróleo:

| Coluna | Descrição |
|---|---|
| `id` | Identificador único do poço |
| `f0`, `f1`, `f2` | Características (features) do poço |
| `product` | Volume de reservas (mil barris), variável-alvo |

> Os arquivos de dados **não** estão versionados neste repositório (veja `.gitignore`). Coloque-os em `data/` antes de rodar.

## Condições de negócio

> Confira os valores exatos no enunciado do projeto e ajuste aqui.

- Orçamento para o desenvolvimento: _X_ milhões de dólares
- Número de poços a selecionar: _X_ (entre _Y_ poços explorados por região)
- Receita por unidade de reservas: _X_ dólares
- Risco máximo aceitável de prejuízo: _X_%
- Bootstrapping: _X_ amostras

## Metodologia

1. **Preparação dos dados:** verificação de nulos, duplicados e tipos.
2. **Divisão dos dados:** treino e validação (75% / 25%) para cada região.
3. **Modelo:** Regressão Linear, avaliada por RMSE e volume médio previsto.
4. **Cálculo de lucro:** seleção dos melhores poços pelas previsões e cálculo do lucro com os volumes reais.
5. **Bootstrapping:** estimativa de lucro médio, intervalo de confiança de 95% e probabilidade de prejuízo por região.

## Resultados

_Preencher ao final do projeto._

| Região | RMSE | Lucro médio | IC 95% | Risco de prejuízo |
|---|---|---|---|---|
| 0 | | | | |
| 1 | | | | |
| 2 | | | | |

**Região recomendada:** _a definir_

## Conclusão

_Resumo da recomendação e justificativa._

## Como executar

```bash
# 1. Clonar o repositório
git clone https://github.com/SEU_USUARIO/OilyGiant_s10_Project.git
cd OilyGiant_s10_Project

# 2. Criar e ativar ambiente virtual (Windows PowerShell)
python -m venv .venv
.venv\Scripts\Activate.ps1

# 3. Instalar dependências
pip install -r requirements.txt

# 4. Abrir o notebook
jupyter notebook
```

## Estrutura do projeto

```
OilyGiant_s10_Project/
├── data/            # arquivos de dados (não versionados)
├── notebooks/       # notebook principal da análise
├── requirements.txt
├── .gitignore
└── README.md
```

## Tecnologias

Python, pandas, NumPy, scikit-learn, matplotlib/seaborn, Jupyter.

## Autora