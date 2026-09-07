# Causality for Data Scientists

Material de apoio do minicurso **"Causality for Data Scientists: Discovery, Causal Inference, and Applications in Machine Learning"**, apresentado no SBBD 2026 por Gustavo Ferreira Viegas de Oliveira, Fabrício Aguiar Silva e Marcus Henrique Soares Mendes (Universidade Federal de Viçosa — UFV, NESPeD Lab).

## Onde as coisas estão

Os quatro notebooks ficam em `notebooks/`, numerados na ordem em que aparecem no curso:

1. [Paradoxo de Simpson](notebooks/1_simpsons_paradox_example.ipynb)
2. [Descoberta causal](notebooks/2_causal_discovery.ipynb)
3. [Estimativa causal](notebooks/3_causal_estimation.ipynb)
4. [Seleção causal de atributos](notebooks/4_causal_feature_selection.ipynb) 

Dentro de `notebooks/extras/` estão dois notebooks bônus: [efeitos heterogêneos com meta-learners (S/T/X-learner)](notebooks/extras/5_heterogeneous_effects.ipynb) e [SHAP vs. DiCE para explicações contrafactuais](notebooks/extras/6_counterfactual_explanations.ipynb).

Os datasets que não vêm de um pacote Python (o dataset de vacinação por Covid-19 usado no Paradoxo de Simpson, e o dataset de sinalização de proteínas de Sachs et al. usado na descoberta causal) estão em `datasets/`. Toda figura gerada por algum notebook é salva em `figures/`, e algumas dessas figuras reaparecem nos slides.

Os slides usados estão em `presentation/`: o fonte em LaTeX (`main.tex` e a pasta `sections/`) e o PDF já compilado (`presentation/main.pdf`, também disponível na raiz do repositório como `slides.pdf`).

## Rodando localmente

O projeto usa [uv](https://docs.astral.sh/uv/) e Python 3.13. Com o uv instalado:

```bash
git clone git@github.com:gfviegas/causality-for-data-scientists-course.git
cd causality-for-data-scientists-course

uv sync
uv run jupyter lab
```

Isso já traz todas as bibliotecas que qualquer notebook do curso usa (causal-learn, DoWhy, EconML, SHAP, DiCE, etc.), então não precisa reinstalar nada notebook por notebook, a célula de `%pip install` no topo de cada um é só para quem for rodar no Colab.

## Rodando no Google Colab

Nenhum notebook exige nada instalado na sua máquina, dá pra rodar tudo direto no navegador:

1. Abra [colab.research.google.com](https://colab.research.google.com).
2. Na caixa de diálogo "Abrir notebook", clique na aba **GitHub** e cole `gfviegas/causality-for-data-scientists-course` (ou a URL completa do repositório). O Colab lista todos os `.ipynb` do repositório — escolha o que quiser em `notebooks/` ou `notebooks/extras/`.
3. Antes de rodar o resto, adicione uma célula logo abaixo da primeira com:
   ```python
   !git clone https://github.com/gfviegas/causality-for-data-scientists-course.git
   %cd causality-for-data-scientists-course/notebooks
   ```
   (troque `notebooks` por `notebooks/extras` se for um dos dois notebooks bônus). Isso garante que os caminhos relativos que os notebooks usam pra ler dataset em `../datasets/` e salvar figura em `../figures/` funcionem — sem esse passo, um notebook aberto direto do GitHub não tem essas pastas ao lado dele.
4. Rode a célula `%pip install ...` que já é a primeira de cada notebook. Ela instala só o que aquele notebook específico precisa por cima do que o Colab já traz.
5. Depois disso é só `Ambiente de execução > Executar tudo`, ou ir célula por célula acompanhando as explicações.

Nenhum notebook precisa de GPU. Todos rodam em CPU em poucos minutos.
