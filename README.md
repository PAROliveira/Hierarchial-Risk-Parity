# Hierarchial-Risk-Parity

# Comparativo entre MVP e HRP: Hierarchical Risk Parity e Markowitz Portfolio

## Índice
- [Resumo](#resumo)
- [Introdução](#introdução)
- [Metodologia](#metodologia)
  - [Carregamento de Dados](#carregamento-de-dados)
  - [Preparação dos Dados](#preparação-dos-dados)
  - [Construção de Portfólios](#construção-de-portfólios)
    - [Hierarchical Risk Parity (HRP)](#hierarchical-risk-parity-hrp)
    - [Markowitz Minimum-Variance Portfolio (MVP)](#markowitz-minimum-variance-portfolio-mvp)
  - [Backtesting e Resultados](#backtesting-e-resultados)
    - [In-Sample](#in-sample)
    - [Out-of-Sample](#out-of-sample)
- [Relatório QuantStats](#relatório-quantstats)
- [Conclusão](#conclusão)

---

## Resumo
Este projeto analisa dois métodos de alocação de ativos: o portfólio de mínima variância de Markowitz (MVP) e o Hierarchical Risk Parity (HRP). Os resultados in-sample e out-of-sample são comparados em termos de retornos acumulados, índice Sharpe e risco, além de um benchmark com o S&P 500.

## Introdução
Portfólios eficientes são essenciais para investidores que buscam otimizar retornos ajustados ao risco. O MVP utiliza variância mínima para distribuir pesos, enquanto o HRP emprega técnicas de clustering hierárquico para uma distribuição mais diversificada.

## Metodologia

### Carregamento de Dados
Os dados históricos dos ativos foram carregados a partir de um dataset local. Além disso, os dados do índice S&P 500 foram obtidos via Yahoo Finance para benchmarking.

### Preparação dos Dados
1. **Limpeza de Dados:**
   - Exclusão de colunas com mais de 30% de valores nulos.
   - Preenchimento de valores faltantes com o último valor conhecido.
2. **Divisão em Conjuntos:**
   - 80% dos dados para treinamento (in-sample).
   - 20% para teste (out-of-sample).
3. **Cálculo de Retornos:** Retornos percentuais diários foram calculados para os ativos e para o S&P 500.

### Construção de Portfólios

#### Hierarchical Risk Parity (HRP)
1. **Distância por Correlação:** Matriz de distância baseada na correlação dos ativos.
2. **Clustering Hierárquico:** Algoritmo de agrupamento com o método de linkage single.
3. **Quasi-Diagonalização:** Reorganização da matriz de covariância.
4. **Bissecção Recursiva:** Alocação de pesos baseada na variância de clusters.

#### Markowitz Minimum-Variance Portfolio (MVP)
1. **Matriz de Covariância:** Calculada a partir dos retornos do conjunto de treinamento.
2. **Programção Quadrática:** Otimização dos pesos para minimizar o risco.

### Backtesting e Resultados

#### In-Sample
- Avaliação dos resultados nos dados de treinamento.
- Retornos cumulativos e índice Sharpe foram calculados.

#### Out-of-Sample
- Aplicação dos portfólios nos dados de teste.
- Comparativo com o índice S&P 500.

Os retornos diários e cumulativos foram visualizados em gráficos para ambos os conjuntos.

## Relatório QuantStats
Relatórios interativos foram gerados utilizando a biblioteca QuantStats, comparando:
- **HRP vs. S&P 500:** Desempenho do portfólio HRP contra o benchmark.
- **MVP vs. S&P 500:** Desempenho do portfólio MVP contra o benchmark.

Os relatórios incluem:
1. Retornos cumulativos.
2. Índice Sharpe.
3. Drawdowns.
4. Estatísticas gerais de desempenho.

## Conclusão
O HRP apresentou maior diversificação e desempenho superior ao MVP em out-of-sample. Ambos os métodos superaram o benchmark em determinados períodos, mas o HRP demonstrou maior robustez em condições de mercado voláteis.
