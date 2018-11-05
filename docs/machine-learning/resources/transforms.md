---
title: Transformações de dados
description: Explore as diferentes transformações de dados com suporte do ML.NET.
ms.date: 10/16/2018
ms.openlocfilehash: 5df4598de6fcd08689d72c378f51d792860ef49c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187735"
---
# <a name="data-transforms"></a>Transformações de dados

As tabelas a seguir contêm informações sobre todas as transformações de dados com suporte do ML.NET (selecione o tipo de transformação de dados para navegar para a tabela correspondente):

* [Categórico](#categorical)
* [Combinadores e segregadores](#combiners-and-segregators)
* [Seleção de recursos](#feature-selection)
* [Personalizadores](#featurizers)
* [Análise de rótulo](#label-parsing)
* [Valores ausentes](#missing-values)
* [Normalização](#normalization)
* [Filtros de linha](#row-filters)
* [Esquema](#schema)
* [Processamento de texto e personalização](#text-processing-and-featurization)
* [Diversos](#miscellaneous)

> [!NOTE]
> O ML.NET está atualmente na Versão Prévia. Nem todas as transformações de dados têm suporte atualmente. Para solicitar uma determinada transformação, abra um problema no repositório do GitHub [dotnet/machinelearning](https://github.com/dotnet/machinelearning/issues).

## <a name="categorical"></a>Categórico

| Transformar | Definição |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.CategoricalHashOneHotVectorizer> | Codifica a variável categórica com codificação baseada em hash. |
| <xref:Microsoft.ML.Legacy.Transforms.CategoricalOneHotVectorizer> | Codifica a variável categórica com codificação one-hot baseada em um dicionário de termos. |

## <a name="combiners-and-segregators"></a>Combinadores e segregadores

| Transformar | Definição |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.CombinerByContiguousGroupId> | Agrupa valores de uma coluna escalar em um vetor com base em uma ID de grupo contígua. |
| <xref:Microsoft.ML.Legacy.Transforms.FeatureCombiner> | Combina todos os recursos em uma única coluna de recursos. |
| <xref:Microsoft.ML.Legacy.Transforms.ManyHeterogeneousModelCombiner> | Combina uma sequência de TransformModels e um PredictorModel em um único PredictorModel. |
| <xref:Microsoft.ML.Legacy.Transforms.ModelCombiner> | Combina uma sequência de TransformModels em um único modelo. |
| <xref:Microsoft.ML.Legacy.Transforms.Segregator> | Desagrupa colunas de vetor em sequências de linhas, ou seja, o inverso da transformação de grupo. |
| <xref:Microsoft.ML.Legacy.Transforms.TwoHeterogeneousModelCombiner> | Combina um TransformModel e um PredictorModel em um único PredictorModel. |

## <a name="feature-selection"></a>Seleção de recursos

| Transformar | Definição |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.FeatureSelectorByCount> | Seleciona os slots para os quais a contagem de valores não padrão é maior ou igual a um limite. |
| <xref:Microsoft.ML.Legacy.Transforms.FeatureSelectorByMutualInformation> | Seleciona os mil slots principais em todas as colunas especificadas, ordenados por suas informações mútuas com a coluna de rótulo. |

## <a name="featurizers"></a>Personalizadores

| Transformar | Definição |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.HashConverter> | Converte os valores de coluna em hashes. Essa transformação aceita entradas numéricas e de texto, colunas únicas e com valores de vetor. |
| <xref:Microsoft.ML.Legacy.Transforms.TreeLeafFeaturizer> | Treina um ensemble de árvore, ou carrega-o de um arquivo e, em seguida, mapeia um vetor de recurso numérico para três saídas: 1. Um vetor que contém as saídas da árvore individual do ensemble de árvore. 2. Um vetor que indica a folha em que o vetor de recurso se enquadra no ensemble de árvore. 3. Um vetor que indica os caminhos em que o vetor de recurso se enquadra no ensemble de árvore. Se um arquivo de modelo e um treinador forem especificados, o vetor usará o arquivo de modelo. Se nenhum deles for especificado, o vetor treinará um modelo FastTree padrão. Essa opção pode lidar com rótulos de chave treinando um modelo de regressão em seus índices permutados opcionalmente. |

## <a name="label-parsing"></a>Análise de rótulo

| Transformar | Definição |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.Dictionarizer> | Converte os valores de entrada (palavras, números, etc.) em um índice em um dicionário. |
| <xref:Microsoft.ML.Legacy.Transforms.LabelColumnKeyBooleanConverter> | Transforma o rótulo em uma chave ou em um booliano (se necessário) para torná-lo adequado para classificação. |
| <xref:Microsoft.ML.Legacy.Transforms.LabelIndicator> | Remapeador de rótulo usado pelo OVA. |
| <xref:Microsoft.ML.Legacy.Transforms.LabelToFloatConverter> | Transforma o rótulo em float para torná-lo adequado para a regressão. |
| <xref:Microsoft.ML.Legacy.Transforms.PredictedLabelColumnOriginalValueConverter> | Transforma uma coluna de rótulo previsto em seus valores originais, a menos que ela seja do tipo booliano. |

## <a name="missing-values"></a>Valores ausentes

| Transformar | Definição |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.MissingValueHandler> | Trata valores ausentes substituindo-os pelo valor padrão ou pelo valor médio/mín./máx. (apenas para colunas que não são de texto). Uma coluna de indicador pode, opcionalmente, ser concatenada quando o tipo de coluna de entrada é numérico. |
| <xref:Microsoft.ML.Legacy.Transforms.MissingValueIndicator> | Cria uma coluna de saída booliana com o mesmo número de slots que a coluna de entrada, em que o valor de saída será true se o valor na coluna de entrada estiver ausente. |
| <xref:Microsoft.ML.Legacy.Transforms.MissingValuesDropper> | Remove NAs das colunas de vetor. |
| <xref:Microsoft.ML.Legacy.Transforms.MissingValuesRowDropper> | Filtra as linhas que contêm valores ausentes. |
| <xref:Microsoft.ML.Legacy.Transforms.MissingValueSubstitutor> | Cria uma coluna de saída do mesmo tipo e tamanho da coluna de entrada, em que os valores ausentes são substituídos pelo o valor padrão ou pelo valor médio/mín./máx. (apenas para colunas que não são de texto). |

## <a name="normalization"></a>Normalização

| Transformar | Definição |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.BinNormalizer> | Os valores são atribuídos em compartimentos de mesma densidade e um valor é mapeado para seu bin_number/number_of_bins. |
| <xref:Microsoft.ML.Legacy.Transforms.ConditionalNormalizer> | Normalize as colunas somente se necessário. |
| <xref:Microsoft.ML.Legacy.Transforms.GlobalContrastNormalizer> | Executa uma normalização de contraste global em valores de entrada: Y = (s * X - M) / D, em que s é uma escala, M é a média e D é a norma L2 ou o desvio padrão. | 
| <xref:Microsoft.ML.Legacy.Transforms.LogMeanVarianceNormalizer> | Normaliza os dados com base na média calculada e na variação do logaritmo dos dados. |
| <xref:Microsoft.ML.Legacy.Transforms.LpNormalizer> | Normaliza vetores (linhas) individualmente redimensionando-os para a norma de unidade (L2, L1 ou LInf). Executa a seguinte operação em um vetor X: Y = (X - M) / D, em que M é a média e D é a norma L2, a norma L1 ou a norma LInf. |
| <xref:Microsoft.ML.Legacy.Transforms.MeanVarianceNormalizer> | Normaliza os dados com base na média calculada e na variação de dados. |
| <xref:Microsoft.ML.Legacy.Transforms.MinMaxNormalizer> | Normaliza os dados com base nos valores mínimos e máximo observados nos dados. |

## <a name="row-filters"></a>Filtros de linha

| Transformar | Definição |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.RowRangeFilter> | Filtra uma dataview em uma coluna do tipo Single, Double ou Key (contígua). Mantém os valores que estão no intervalo mín./máx. especificados. NaNs sempre são filtrados. Se a entrada for do tipo Key, os mín./máx. serão considerados porcentagens do número de valores. |
| <xref:Microsoft.ML.Legacy.Transforms.RowSkipAndTakeFilter> | Permite limitar a entrada a um subconjunto de linhas em um deslocamento opcional. Pode ser usado para implementar a paginação de dados. |
| <xref:Microsoft.ML.Legacy.Transforms.RowSkipFilter> | Permite limitar a entrada a um subconjunto de linhas, ignorando um número de linhas. |
| <xref:Microsoft.ML.Legacy.Transforms.RowTakeFilter> | Permite limitar a entrada a um subconjunto de linhas aproveitando as N primeiras linhas. |

## <a name="schema"></a>Esquema

| Transformar | Definição |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.ColumnConcatenator> | Concatena duas colunas do mesmo tipo de item. |
| <xref:Microsoft.ML.Legacy.Transforms.ColumnCopier> | Duplica as colunas do conjunto de dados.|
| <xref:Microsoft.ML.Legacy.Transforms.ColumnDropper> | Remove as colunas do conjunto de dados. |
| <xref:Microsoft.ML.Legacy.Transforms.ColumnSelector> | Seleciona um conjunto de colunas, removendo todas as outras. |
| <xref:Microsoft.ML.Legacy.Transforms.ColumnTypeConverter> | Converte uma coluna em um tipo diferente, usando conversões padrão. |
| <xref:Microsoft.ML.Legacy.Transforms.KeyToTextConverter> | KeyToValueTransform utiliza metadados KeyValues para mapear os índices de chave aos valores correspondentes nos metadados KeyValues. |
| <xref:Microsoft.ML.Legacy.Transforms.NGramTranslator> | Produz um recipiente de contagens de ngramas (sequências de valores consecutivos de comprimento 1 – n) em um determinado vetor de chaves. Ele faz isso criando um dicionário de ngramas e usando a ID no dicionário como o índice no recipiente. | 
| <xref:Microsoft.ML.Legacy.Transforms.OptionalColumnCreator> | Se a coluna de origem não existir após a desserialização, crie uma coluna do tipo correto e com os valores padrão. |

## <a name="text-processing-and-featurization"></a>Processamento de texto e personalização

| Transformar | Definição |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.CharacterTokenizer> | Criador de token orientado a caracteres em que o texto é considerado uma sequência de caracteres. |
| <xref:Microsoft.ML.Legacy.Transforms.TextFeaturizer> | Uma transformação que transforma uma coleção de documentos de texto em vetores de recurso numérico. Os vetores de recurso são contagens normalizadas de ngramas (palavra e/ou caractere) em um determinado texto indexado. |
| <xref:Microsoft.ML.Legacy.Transforms.TextToKeyConverter> | Converte os valores de entrada (palavras, números, etc.) em um índice em um dicionário. |
| <xref:Microsoft.ML.Legacy.Transforms.WordEmbeddings> | Uma transformação que converte os vetores de tokens de texto em vetores numéricos usando um modelo previamente treinado. Para obter mais informações sobre a técnica, confira a página [Word embedding](https://en.wikipedia.org/wiki/Word_embedding) (Incorporação de palavras) da Wikipédia. |
| <xref:Microsoft.ML.Legacy.Transforms.WordTokenizer> | A entrada para essa transformação é texto e a saída é um vetor de texto que contém as palavras (tokens) no texto original. O separador é um espaço, mas é possível especificar qualquer outro caractere (ou vários caracteres). |

## <a name="miscellaneous"></a>Diversos

| Transformar | Definição |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.ApproximateBootstrapSampler> | Amostragem de inicialização aproximada. |
| <xref:Microsoft.ML.Legacy.Transforms.BinaryPredictionScoreColumnsRenamer> | Para previsão binária, renomeia as colunas PredictedLabel e Score para incluir o nome da classe positiva.|
| <xref:Microsoft.ML.Legacy.Transforms.DataCache> | Armazena em cache usando a opção de cache especificada. |
| <xref:Microsoft.ML.Legacy.Transforms.DatasetScorer> | Pontua um conjunto de dados com um modelo de previsão. |
| <xref:Microsoft.ML.Legacy.Transforms.DatasetTransformScorer> | Pontua um conjunto de dados com um modelo de transformação. |
| <xref:Microsoft.ML.Legacy.Transforms.NoOperation> | Não agir. |
| <xref:Microsoft.ML.Legacy.Transforms.RandomNumberGenerator> | Adiciona uma coluna com uma sequência de números gerada. |
| <xref:Microsoft.ML.Legacy.Transforms.ScoreColumnSelector> | Seleciona apenas a última colunas de pontuação e as colunas extras especificadas nos argumentos. |
| <xref:Microsoft.ML.Legacy.Transforms.Scorer> | Transforma o modelo de previsão em um modelo de transformação. |
| <xref:Microsoft.ML.Legacy.Transforms.SentimentAnalyzer> | Usa um modelo de sentimento previamente treinado para pontuar cadeias de caracteres de entrada. |
| <xref:Microsoft.ML.Legacy.Transforms.TrainTestDatasetSplitter> | Divide o conjunto de dados em conjuntos de treinamento e teste. |
