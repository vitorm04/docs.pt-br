---
title: Transformações de dados do aprendizado de máquina – ML.NET
description: Explore os componentes de engenharia de recursos com suporte no ML.NET.
author: JRAlexander
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: c311aa59426b716ffcd2c53e890d2e3e380360a7
ms.sourcegitcommit: 81bd16c7435a8c9183d2a7e878a2a5eff7d04584
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/12/2019
ms.locfileid: "54249119"
---
# <a name="machine-learning-data-transforms---mlnet"></a>Transformações de dados do aprendizado de máquina – ML.NET

As tabelas a seguir contêm informações sobre todas as transformações de dados compatíveis com o ML.NET.

> [!NOTE]
> O ML.NET está atualmente na Versão Prévia. Nem todas as transformações de dados têm suporte atualmente. Para solicitar uma determinada transformação, abra um problema no repositório do GitHub [dotnet/machinelearning](https://github.com/dotnet/machinelearning/issues).

## <a name="combiners-and-segregators"></a>Combinadores e segregadores

| Transformar | Definição |
| --- | --- |
| <xref:Microsoft.ML.Transforms.GroupTransform> | Agrupa valores de uma coluna escalar em um vetor com base em uma ID de grupo contígua. |
| <xref:Microsoft.ML.Legacy.Transforms.FeatureCombiner> | Combina todos os recursos em uma única coluna de recursos. |
| <xref:Microsoft.ML.Legacy.Transforms.ManyHeterogeneousModelCombiner> | Combina uma sequência de TransformModels e um PredictorModel em um único PredictorModel. |
| <xref:Microsoft.ML.Legacy.Transforms.ModelCombiner> | Combina uma sequência de TransformModels em um único modelo. |
| <xref:Microsoft.ML.Legacy.Transforms.Segregator> | Desagrupa colunas de vetor em sequências de linhas, ou seja, o inverso da transformação de grupo. |
| <xref:Microsoft.ML.Legacy.Transforms.TwoHeterogeneousModelCombiner> | Combina um TransformModel e um PredictorModel em um único PredictorModel. |
| <xref:Microsoft.ML.Transforms.UngroupTransform> | Desagrupa colunas de vetor em sequências de linhas, o inverso da transformação de Grupo. |

## <a name="conversions"></a>Conversões 

| Transformar | Definição |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Conversions.HashingTransformer> | Cria hashes de colunas com valor único ou colunas de vetor. Para colunas de vetor, cria hashes de cada slot separadamente. Pode criar hashes de valores de texto ou valores de chave. |
| <xref:Microsoft.ML.Legacy.Transforms.HashConverter> | Converte os valores de coluna em hashes. Essa transformação aceita entradas numéricas e de texto, colunas únicas e com valores de vetor. |
| <xref:Microsoft.ML.Transforms.Conversions.HashJoiningTransform> | Converte vários valores de coluna em hashes. Essa transformação aceita entradas numéricas e de texto, colunas únicas e com valores de vetor. |
| <xref:Microsoft.ML.Transforms.Conversions.KeyToBinaryVectorMappingTransformer> | Converte uma chave em uma coluna de vetor binária. |
| <xref:Microsoft.ML.Transforms.Conversions.KeyToValueMappingTransformer > | Utiliza metadados KeyValues para mapear os índices de chave para os valores correspondentes nos metadados KeyValues. |
| <xref:Microsoft.ML.Transforms.Conversions.KeyToVectorMappingTransformer> | Converte uma chave em uma coluna de vetor. |
| <xref:Microsoft.ML.Transforms.Conversions.TypeConvertingTransformer> | Altera o tipo da coluna subjacente, desde que o tipo possa ser convertido. |
| <xref:Microsoft.ML.Transforms.Conversions.ValueToKeyMappingTransformer> | Converte os valores de entrada (palavras, números, etc.) em um índice em um dicionário. |


## <a name="deep-learning"></a>Aprendizado profundo

| Transformar | Definição |
| --- | --- |
| <xref:Microsoft.ML.Transforms.OnnxTransform> | Fornece dados para um modelo ONNX existente e retorna a pontuação (previsão). |
| <xref:Microsoft.ML.Transforms.TensorFlowTransform> | Pode pontuar com o modelo pré-treinado do TensorFlow ou treinar o modelo do TensorFlow novamente. |

## <a name="feature-extraction"></a>Extração de recursos

| Transformar | Definição |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Text.CustomStopWordsRemovingTransform> | Remove a lista especificada de palavras irrelevantes (stop words) comparando tokens individuais (comparação que não diferencia maiúsculas de minúsculas) com as palavras irrelevantes.| 
| <xref:Microsoft.ML.Runtime.ImageAnalytics.ImageGrayscaleTransform> | Usa uma ou mais colunas ImageType e converte-as em uma representação em escala de cinza da mesma imagem.|
| <xref:Microsoft.ML.Runtime.ImageAnalytics.ImageLoaderTransform> | Usa uma ou mais colunas ReadOnlyMemory e carrega-as como um ImageType. |
| <xref:Microsoft.ML.Runtime.ImageAnalytics.ImagePixelExtractorTransform> | Usa uma ou mais colunas ImageType e converte-as em uma representação de vetor.|
| <xref:Microsoft.ML.Runtime.ImageAnalytics.ImageResizerTransform> | Usa uma ou mais colunas ImageType e redimensiona-as para a altura e a largura fornecidas.|
| <xref:Microsoft.ML.Transforms.Text.LatentDirichletAllocationTransformer> | Implementa o LightLDA, uma implementação de última geração da Alocação de Dirichlet Latente.|
| <xref:Microsoft.ML.Transforms.LoadTransform> | Carrega transformações específicas do arquivo de modelo especificado. Permite transformações 'cherry-picking' de uma cadeia serializada ou aplica uma transformação pré-treinada a uma exibição de dados diferente (mas ainda compatível). |
| <xref:Microsoft.ML.Transforms.Text.NgramExtractingTransformer> | Produz um recipiente de contagens de ngramas (sequências de valores consecutivos de comprimento 1 – n) em um determinado vetor de chaves. Ele faz isso criando um dicionário de ngramas e usando a ID no dicionário como o índice no recipiente. | 
| <xref:Microsoft.ML.Transforms.Text.NgramExtractorTransform> | Transforma uma coleção de textos indexados (vetor de ReadOnlyMemory) ou vetores de chaves em vetores de recurso numérico. Os vetores de recurso são contagens de ngrams (sequências de tokens consecutivos – palavras ou chaves – de tamanho 1-n). | 
| <xref:Microsoft.ML.Transforms.Text.NgramHashExtractingTransformer> | Transforma uma coleção de textos indexados (vetor de ReadOnlyMemory) em vetores de recurso numérico usando o hash. | 
| <xref:Microsoft.ML.Transforms.Text.NgramHashingTransformer> | Produz um recipiente de contagens de ngrams (sequências de palavras consecutivas de tamanho 1-n) em determinado texto. | 
| <xref:Microsoft.ML.Transforms.Categorical.OneHotEncodingTransformer> | Converte o valor categórico em uma matriz de indicador criando um dicionário de categorias com base nos dados e usando a ID no dicionário como o índice na matriz |
| <xref:Microsoft.ML.Transforms.Projections.PcaTransform> | Calcula a projeção do vetor de recurso em um subespaço de classificação baixa. |
| <xref:Microsoft.ML.Transforms.Text.SentimentAnalyzingTransformer> | Usa um modelo de sentimento previamente treinado para pontuar cadeias de caracteres de entrada. |
| <xref:Microsoft.ML.Transforms.Text.StopWordsRemovingTransformer> | Remove a lista específica a um idioma de palavras irrelevantes (palavras comuns, em sua maioria) comparando tokens individuais (comparação que não diferencia maiúsculas de minúsculas) com as palavras irrelevantes. |
| <xref:Microsoft.ML.Transforms.Categorical.TermLookupTransformer> | Mapeia colunas de valores de texto para novas colunas usando um conjunto de dados de mapa fornecido por meio de seus argumentos. |
| <xref:Microsoft.ML.Transforms.Text.WordBagBuildingTransformer> | Produz um recipiente de contagens de ngrams (sequências de palavras consecutivas) em determinado texto. Ele faz isso criando um dicionário de ngramas e usando a ID no dicionário como o índice no recipiente. |
| <xref:Microsoft.ML.Transforms.Text.WordHashBagProducingTransformer> | Produz um recipiente de contagens de ngrams (sequências de palavras consecutivas de tamanho 1-n) em determinado texto. Isso é feito pela criação de um hash de cada ngram e pelo uso do valor de hash como o índice no recipiente. |
| <xref:Microsoft.ML.Transforms.Text.WordTokenizingTransformer> | Divide o texto em palavras usando os caracteres separadores. |


## <a name="image-model-featurizers"></a>Recursos do modelo de imagem

| Transformar | Definição |
| --- | --- |
| <xref:Microsoft.ML.Transforms.AlexNetExtension> | Esse é um método de extensão a ser usado com o <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> para usar um modelo pré-treinado [AlexNet](https://en.wikipedia.org/wiki/AlexNet). O NuGet que contém essa extensão também garante a inclusão do arquivo de modelo binário. | 
| <xref:Microsoft.ML.Transforms.ResNet18Extension> | Esse é um método de extensão a ser usado com o <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> para usar um modelo pré-treinado ResNet18. O NuGet que contém essa extensão também garante a inclusão do arquivo de modelo binário. |
| <xref:Microsoft.ML.Transforms.ResNet50Extension> | Esse é um método de extensão a ser usado com o <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> para usar um modelo pré-treinado ResNet50. O NuGet que contém essa extensão também garante a inclusão do arquivo de modelo binário. |
| <xref:Microsoft.ML.Transforms.ResNet101Extension> | Esse é um método de extensão a ser usado com o <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> para usar um modelo pré-treinado ResNet101. O NuGet que contém essa extensão também garante a inclusão do arquivo de modelo binário. |

## <a name="label-parsing"></a>Análise de rótulo

| Transformar | Definição |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.Dictionarizer> | Converte os valores de entrada (palavras, números, etc.) em um índice em um dicionário. |
| <xref:Microsoft.ML.Legacy.Transforms.LabelColumnKeyBooleanConverter> | Transforma o rótulo em uma chave ou em um booliano (se necessário) para torná-lo adequado para classificação. |
| <xref:Microsoft.ML.Transforms.LabelConvertTransform> |  Converte os rótulos. |
| <xref:Microsoft.ML.Transforms.LabelIndicatorTransform> | Remapeia rótulos multiclasse para rótulos binários True, False, principalmente para uso com o OVA.|
| <xref:Microsoft.ML.Legacy.Transforms.LabelToFloatConverter> | Transforma o rótulo em float para torná-lo adequado para a regressão. |
| <xref:Microsoft.ML.Legacy.Transforms.PredictedLabelColumnOriginalValueConverter> | Transforma uma coluna de rótulo previsto em seus valores originais, a menos que ela seja do tipo booliano. |

## <a name="missing-values"></a>Valores ausentes

| Transformar | Definição |
| --- | --- |
| <xref:Microsoft.ML.Transforms.MissingValueDroppingTransformer> | Remove valores ausentes de colunas. |
| <xref:Microsoft.ML.Transforms.MissingValueIndicatorTransform> | Cria uma coluna de saída booliana com o mesmo número de slots da coluna de entrada, em que o valor de saída é true se o valor na coluna de entrada está ausente. |
| <xref:Microsoft.ML.Transforms.MissingValueReplacingTransformer> | Trata valores ausentes substituindo-os pelo valor padrão ou pelo valor médio/mín./máx. (apenas para colunas que não são de texto). |

## <a name="normalization"></a>Normalização

| Transformar | Definição |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Projections.LpNormalizingTransformer> | Transformação de normalização de Lp-Norm (por vetor/linha). |
| <xref:Microsoft.ML.Transforms.Normalizers.MeanVarDblAggregator> | Calcula a média e a variação de uma coluna com valor de vetor. Acompanha a média atual e o M2 (soma das comparações quadradas dos valores da média), o número de NaNs e o número de elementos diferentes de zero. |
| <xref:Microsoft.ML.Transforms.Normalizers.MeanVarSngAggregator> | Calcula a média e a variação de uma coluna com valor de vetor. Acompanha a média atual e o M2 (soma das comparações quadradas dos valores da média), o número de NaNs e o número de elementos diferentes de zero. |
| <xref:Microsoft.ML.Transforms.Normalizers.MinMaxDblAggregator> | Acompanha mín., máx., número de valores não esparsos (vCount) e número de chamadas ProcessValue() (trainCount) de uma coluna com valor de vetor. |
| <xref:Microsoft.ML.Transforms.Normalizers.MinMaxSngAggregator> | Acompanha mín., máx., número de valores não esparsos (vCount) e número de chamadas ProcessValue() (trainCount) de uma coluna com valor de vetor. |
| <xref:Microsoft.ML.Transforms.Normalizers.NormalizeTransform> | Padroniza os intervalos de recurso. |
| <xref:Microsoft.ML.Transforms.Normalizers.NormalizingTransformer> |Padroniza os intervalos de recurso. |

## <a name="onnx"></a>ONNX

| Transformar | Definição |
| --- | --- |
| <xref:Microsoft.ML.Transforms.OnnxTransform> | Pontua os modelos pré-treinados ONNX que usam o padrão ONNX v1.2 |

## <a name="preprocessing"></a>Pré-processamento
| Transformar | Definição |
| --- | --- |
| <xref:Microsoft.ML.Transforms.BootstrapSamplingTransformer> | Aproxima a amostragem de inicialização usando a amostragem de Poisson. |
| <xref:Microsoft.ML.Transforms.Projections.RandomFourierFeaturizingTransformer> | Produz um recurso de Fourier aleatório. |
| <xref:Microsoft.ML.Transforms.Text.TokenizingByCharactersTransformer> | Criador de token orientado a caracteres em que o texto é considerado uma sequência de caracteres. |
| <xref:Microsoft.ML.Transforms.Projections.VectorWhiteningTransformer> | Simplifica a otimização para ajudar na identificação de pesos. |

## <a name="row-filters"></a>Filtros de linha

| Transformar | Definição |
| --- | --- |
| <xref:Microsoft.ML.Transforms.RowShufflingTransformer> | Embaralha uma tentativa de cursor aleatória de executar usando um pool de determinado número de linhas.  |
| <xref:Microsoft.ML.Transforms.SkipFilter> | Permite limitar a entrada a um subconjunto de linhas, ignorando um número de linhas. |
| <xref:Microsoft.ML.Transforms.SkipTakeFilter> | Permite limitar a entrada a um subconjunto de linhas em um deslocamento opcional. Pode ser usado para implementar a paginação de dados. Quando criado com SkipTakeFilter.SkipArguments, comporta-se como `SkipFilter`.
| <xref:Microsoft.ML.Transforms.TakeFilter> | Permite limitar a entrada a um subconjunto de linhas aproveitando as N primeiras linhas. |


## <a name="schema"></a>Esquema

| Transformar | Definição |
| --- | --- |
| <xref:Microsoft.ML.Transforms.ColumnCopyingTransformer> | Duplica as colunas do conjunto de dados.|
| <xref:Microsoft.ML.Transforms.ColumnSelectingTransformer> | Seleciona um conjunto de colunas a serem removidas ou mantidas de determinada entrada. |
| <xref:Microsoft.ML.Transforms.FeatureSelection.SlotsDroppingTransformer> | Remove slots de colunas.|
| <xref:Microsoft.ML.Legacy.Transforms.KeyToTextConverter> | KeyToValueTransform utiliza metadados KeyValues para mapear os índices de chave aos valores correspondentes nos metadados KeyValues. |
| <xref:Microsoft.ML.Transforms.OptionalColumnTransform> | Cria uma coluna com o tipo especificado e os valores padrão. |
| <xref:Microsoft.ML.Transforms.RangeFilter> | Filtra uma dataview em uma coluna do tipo Single, Double ou Key (contígua). Mantém os valores que estão no intervalo mín./máx. especificados. NaNs sempre são filtrados. Se a entrada for do tipo Key, os mín./máx. serão considerados porcentagens do número de valores. |

## <a name="tensorflow"></a>TensorFlow

| Transformar | Definição |
| --- | --- |
| <xref:Microsoft.ML.Transforms.TensorFlowTransform> | Pontua com o modelo pré-treinado do TensorFlow ou treina o modelo do TensorFlow novamente. |

## <a name="text-processing-and-featurization"></a>Processamento de texto e personalização

| Transformar | Definição |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Text.TextNormalizingTransformer> | Uma transformação de normalização de texto que permite a normalização de maiúsculas e minúsculas do texto, removendo marcas diacríticas, sinais de pontuação e/ou números. A transformação opera na entrada de texto, bem como no vetor de tokens/texto (vetor de ReadOnlyMemory). |
| <xref:Microsoft.ML.Transforms.Text.TokenizingByCharactersTransformer> | Criador de token orientado a caracteres em que o texto é considerado uma sequência de caracteres. |

## <a name="time-series"></a>Série temporal

| Transformar | Definição |
| --- | --- |
| <xref:Microsoft.ML.Runtime.TimeSeriesProcessing.ExponentialAverageTransform> | Usa uma média ponderada dos valores: ExpAvg(y_t) = a * y_t + (1-a) * ExpAvg(y_(t-1)). |
| <xref:Microsoft.ML.Runtime.TimeSeriesProcessing.IidChangePointDetector> | Implementa a transformação de detector de ponto de alteração para uma sequência i.i.d. (amostra aleatória) com base em martingales e na estimativa de densidade de kernel adaptável. |
| <xref:Microsoft.ML.Runtime.TimeSeriesProcessing.IidSpikeDetector> | Implementa a transformação de detector de pico para uma sequência i.i.d. (amostra aleatória) com base na estimativa de densidade de kernel adaptável. |
| <xref:Microsoft.ML.Runtime.TimeSeriesProcessing.MovingAverageTransform> | Fornece uma média ponderada dos valores da janela deslizante. |
| <xref:Microsoft.ML.Runtime.TimeSeriesProcessing.PercentileThresholdTransform> | Decide se o valor atual da série temporal pertence ao percentil dos valores máximos da janela deslizante. |
| <xref:Microsoft.ML.Runtime.TimeSeriesProcessing.PValueTransform> | Calcula o valor p empírico do valor atual da série com base nos outros valores da janela deslizante. |
| <xref:Microsoft.ML.Runtime.TimeSeriesProcessing.SlidingWindowTransform> | Gera uma janela deslizante em uma série temporal do tipo Single. |
| <xref:Microsoft.ML.Runtime.TimeSeriesProcessing.SsaChangePointDetector> | Implementa a transformação de detector de ponto de alteração com base na modelagem de Singular Spectrum da série temporal. |
| <xref:Microsoft.ML.Runtime.TimeSeriesProcessing.SsaSpikeDetector> | Implementa a transformação de detector de pico com base na modelagem de Singular Spectrum da série temporal. |

## <a name="miscellaneous"></a>Diversos

| Transformar | Definição |
| --- | --- |
| <xref:Microsoft.ML.Transforms.CompositeTransformer> | Cria uma DataTransform de composição. |
| <xref:Microsoft.ML.Transforms.CustomMappingTransformer%602> | Gera colunas adicionais para a `IDataView` fornecida. Não altera o número de linhas e pode ser visto como um resultado da aplicação da função do usuário a cada linha dos dados de entrada.|
| <xref:Microsoft.ML.Transforms.GenerateNumberTransform> | Adiciona uma coluna com uma sequência de números gerada. |
| <xref:Microsoft.ML.Transforms.ProduceIdTransform> | Produz uma coluna com a ID do cursor como uma coluna. |
| <xref:Microsoft.ML.Transforms.RandomNumberGenerator> | Gera um número aleatório. |
| <xref:Microsoft.ML.Transforms.ScoringTransformer> | Combina informações de vários modelos preditivos para gerar um novo modelo no pipeline, usando as pontuações de um modelo já treinado. |
