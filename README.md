# Qual a melhor região para novos poços de petróleo?


## Contexto
Nesse projeto, atuarei como uma cientista de dados de uma empresa de mineração OilyGiant. Minha tarefa é  **identificar a região com maior margem de lucro** para o desenvolvimento de novos poços de petróleo, usando um modelo de regressão para prever o volume de reservas e a técnica de **Bootstrapping** para avaliar lucro potencial e risco.

## Objetivos
Para realizar essa tarefa vou executar os seguintes etapas:
1. Ler os arquivos com parâmetros coletados de poços de petróleo na região selecionada: a quantidade de petróleo e o volume de reservas;
2. Construir um modelo para predizer o volume de reservas em novos poços;
3. Escolher os poços de petróleo que têm os maiores valores estimados;
4. Escolher, entre as regiões com risco de prejuízo inferior a 2,5%, a de maior lucro médio.

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

1. **Preparação dos dados:** verificação de nulos, duplicados e tipos; análise descritiva e de correlação. IDs repetidos foram inspecionados e mantidos, pois correspondem a poços distintos.
2. **Divisão dos dados:** treino e validação (75% / 25%) para cada região, com padronização das características ajustada apenas no treino.
3. **Modelo:** Regressão Linear, avaliada por RMSE, volume médio previsto e comparação com um modelo constante (média do treino).
4. **Cálculo de lucro:** seleção dos 200 poços com maiores previsões e cálculo do lucro com os volumes reais.
5. **Bootstrapping:** 1.000 amostras de 500 poços com reposição; seleção dos 200 melhores em cada amostra; estimativa de lucro médio, IC de 95% e probabilidade de prejuízo.

## Resultados

### Desempenho do modelo (conjunto de validação)

| Região | Volume médio previsto (mil barris) | RMSE (mil barris) | Redução do erro vs. modelo constante |
|---|---|---|---|
| 0 | 92,59 | 37,58 | 15,2% |
| 1 | 68,73 | 0,89 | 98,1% |
| 2 | 94,97 | 40,03 | 10,9% |

### Lucro e risco (bootstrapping: 1.000 amostras de 500 poços, 200 melhores)

| Região | RMSE | Lucro médio | IC 95% | Risco de prejuízo | Atende risco < 2,5%? |
|---|---|---|---|---|---|
| 0 | 37,58 | US$ 3,96 mi | [-1,11 ; 9,10] mi | 6,9% | Não |
| 1 | 0,89 | US$ 4,56 mi | [0,34 ; 8,52] mi | 1,5% | **Sim** |
| 2 | 40,03 | US$ 4,04 mi | [-1,63 ; 9,50] mi | 7,6% | Não |

**Região recomendada: Região 1**
## Conclusão

A **Região 1** é a recomendada: é a única com risco de prejuízo abaixo de 2,5% (1,5%) e também tem o maior lucro médio (US$ 4,56 milhões), com intervalo de confiança de 95% totalmente positivo.

- **Por que o risco difere tanto?** Na Região 1, `f2` tem correlação quase perfeita com `product`, o que resulta em um modelo muito preciso (RMSE de 0,89). Nas Regiões 0 e 2 o RMSE é de cerca de 40 mil barris (~41% do volume médio), e a seleção dos melhores poços é menos confiável.
- **A análise de risco mudou a decisão.** Selecionando os 200 melhores poços entre todos os da validação, a Região 0 tinha o maior lucro potencial (US$ 33,2 milhões). Porém, esse cenário é otimista e não mede incerteza. Ao simular a exploração de 500 pontos por bootstrapping, as Regiões 0 e 2 ultrapassaram o limite de risco.
- **Limitações:** os dados são sintéticos, a margem de lucro é pequena frente ao investimento de US$ 100 milhões (~4%), e as diferenças entre os lucros médios das regiões são pequenas, então o critério de risco é o que decide a escolha.

## Como executar

```bash
# 1. Clonar o repositório
git clone https://github.com/LarissaBotany/OilyGiant_s10_Project.git
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
├── dataset/            # arquivos de dados (não versionados)
├── .gitignore
└── README.md
```

## Tecnologias

Python, pandas, NumPy, scikit-learn, matplotlib/seaborn, Jupyter.

## Autora
Larissa Areal de Carvalho Muller

Esse projeto faz parte dos projetos desenvolvidos durante bootcamp de Ciência de Dados.