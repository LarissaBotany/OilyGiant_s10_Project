# Qual a melhor região para novos poços de petróleo?


## Contexto
Nesse projeto, atuarei como uma cientista de dados de uma empresa de mineração OilyGiant. Minha tarefa é  **identificar a região com maior margem de lucro** para o desenvolvimento de novos poços de petróleo, usando um modelo de regressão para prever o volume de reservas e a técnica de **Bootstrapping** para avaliar lucro potencial e risco.

## Objetivos
Para realizar essa tarefa vou executar os seguintes etapas:
1. Ler os arquivos com parâmetros coletados de poços de petróleo na região selecionada: a quantidade de petróleo e o volume de reservas;
2. Construir um modelo para predizer o volume de reservas em novos poços;
3. Escolher os poços de petróleo que têm os maiores valores estimados;
4. Escolher a região com o maior lucro total para os poços de petróleo selecionados.

## Dados
Tenho em mãos dados sobre amostras de petróleo de três regiões com parâmetros de cada poço de petróleo na região já são conhecidos.

Os dados são sintéticos e não incluem nenhum detalhe de contratos ou características de poços.

### Descrição de dados
| Coluna | Descrição |
|---|---|
| `id` | Identificador único do poço |
| `f0`, `f1`, `f2` | Características (features) do poço |
| `product` | Volume de reservas (mil barris), variável-alvo |


## Condições de negócio

Há algumas condições, que preciso considerar, para encontrar os melhores lugares:
- Apenas regressão linear deve ser usada para o treinamento do modelo.
- Ao explorar a região, um estudo de 500 pontos é realizado e os melhores 200 pontos são selecionados para calcular o lucro.
- O orçamento para o desenvolvimento de 200 poços de petróleo é 100 milhões de dólares.
- Um barril de petróleo bruto traz 4.5 dólares de receita. A receita de uma unidade de produto é 4.500 dólares (o volume de reservas está em milhares de barris).
- Depois de ter avaliado os riscos, mantenha apenas as regiões com o risco de perdas inferior a 2.5%. Entre aquelas que se enquadram no critério, você precisa selecionar a região com o lucro médio mais alto.

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
Larissa Areal de Carvalho Muller

Esse projeto faz parte dos projetos desenvolvidos durante bootcamp de Ciência de Dados.