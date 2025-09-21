# Atividade Ponderada de Tradução Automática

Aluna: Heloisa Oliveira

Este repositório apresenta o desenvolvimento da aluna em relação a ponderada de Tradução Automática, uma implementação da seção 9.5 do Dive into Deep Learning, que é um estudo de caso de tradução automática.

## Exercícios

### 1. Tente valores diferentes do argumento num_examples na função load_data_nmt. Como isso afeta os tamanhos do vocabulário do idioma de origem e do idioma de destino?

&emsp;&emsp; Como observados nos testes realizados no notebook do repositório, para num_examples como 200 e 1200, percebe-se que ao passar um número menor, o conjunto de frases respectivamente será menor, pois menos palavras únicas aparecem, então muitas palavras mais raras ficam de fora, resultando em um vocabulário menor. O contrário acontece com um valor maior de num_examples, que o conjunto de frases será maior, mais palavras únicas aparecem e o vocabulário crece, porque mais termos diferentes aparecem com frequência >= 2.

### 2. O texto em alguns idiomas, como chinês e japonês, não tem indicadores de limite de palavras (por exemplo, espaço). A tokenização em nível de palavra ainda é uma boa ideia para esses casos? Por que ou por que não?

&emsp;&emsp; Utilizando como base a explicação de tokenização do site: https://www.datacamp.com/pt/blog/what-is-tokenization.

A tokenização em palavras não é uma boa ideia para linguagens que não possuem marcadores de divisões claras, como o carctere espaço (" "). Dessa forma, outros tipos de tokenização ganham espaço como:

- Tokenização de caracteres: segmenta o texto em caracteres individuais; útil para idiomas sem limites claros de palavras ou tarefas que exigem análise granular.

- Tokenização de subpalavras: quebra o texto em unidades maiores que caracteres, mas menores que palavras; útil para idiomas com morflogia complexa ou para lidar com palavras fora do vocabulário.

Alguns idiomas, como chinês, japonês ou tailandês, não têm espaços claros entre as palavras, o que torna a tokenização mais complexa. Determinar onde uma palavra termina e outra começa é um desafio significativo nesses idiomas.

Para resolver isso, os avanços nos modelos de tokenização multilíngue fizeram progressos significativos. Por exemplo:

- O XLM-R (Cross-lingual Language Model - RoBERTa) usa tokenização de subpalavras e pré-treinamento em larga escala para lidar com mais de 100 idiomas de forma eficaz, inclusive aqueles sem limites claros de palavras.

- O mBERT (Multilingual BERT) utiliza a tokenização do WordPiece e demonstrou um bom desempenho em vários idiomas, destacando-se na compreensão de estruturas sintáticas e semânticas, mesmo em idiomas com poucos recursos.

Esses modelos não apenas tokenizam o texto com eficiência, mas também aproveitam vocabulários de subpalavras compartilhados entre idiomas, melhorando a tokenização de scripts que normalmente são mais difíceis de processar.