---
title: O que é o Construtor de Modelo e como ele funciona?
description: Como usar o Construtor de Modelo do ML.NET para treinar automaticamente um modelo de machine learning
ms.date: 01/07/2020
ms.custom: overview
ms.openlocfilehash: ac704b7961a8442a9174cdef5a4cd2a619236a4e
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777401"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a>O que é o Construtor de Modelo e como ele funciona?

O Construtor de Modelo do ML.NET é uma extensão gráfica do Visual Studio intuitiva para criar, treinar e implantar modelos de aprendizado de máquina personalizados.

O Construtor de Modelo usa o aprendizado de máquina automatizado (AutoML) para explorar os algoritmos diferentes de aprendizado de máquina e as configurações para ajudar você a encontrar o que melhor atende ao seu cenário.

Não é necessário ter experiência de aprendizado de máquina para usar o Construtor de Modelo. Você só precisa de um problema para resolver e alguns dados. O Construtor de Modelo gera o código para adicionar o modelo em seu aplicativo .NET.

![Animação de interface do usuário da extensão do Visual Studio do Construtor de Modelo](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> O Construtor de Modelo está atualmente na Versão Prévia.

## <a name="scenarios"></a>Cenários

Você pode trazer vários cenários diferentes para o Construtor de Modelo para gerar um modelo de machine learning para seu aplicativo.

Um cenário é uma descrição do tipo de previsão que você deseja fazer usando seus dados. Por exemplo:

- prever o volume de vendas futuras do produto com base em dados históricos de vendas
- classificar sentimentos como positivos ou negativos com base em revisões de cliente
- detectar se uma transação bancária é fraudulenta
- encaminhar problemas de comentários de clientes para a equipe correta em sua empresa

### <a name="which-machine-learning-scenario-is-right-for-me"></a>Qual cenário do aprendizado de máquina é adequado para mim?

No construtor de modelos, você precisa selecionar um cenário. O tipo de cenário depende do tipo de previsão que você está tentando fazer.

#### <a name="predict-a-category-when-there-are-only-two-categories"></a>Prever uma categoria (quando há apenas duas categorias)

A classificação binária é usada para classificar dados em duas categorias (sim/não; aprovados/reprovados, verdadeiros/falsos; positivos/negativos).

![Diagrama mostrando exemplos de classificação binária incluindo detecção de fraude, mitigação de risco e triagem de aplicativo](media/binary-classification-examples.png)

A análise de sentimento pode ser usada para prever o sentimento positivo ou negativo de comentários do cliente. É um exemplo da tarefa de aprendizado de máquina de classificação binária.

Se seu cenário exigir a classificação em duas categorias, você poderá usar esse modelo com seu próprio conjunto de dados.

#### <a name="predict-a-category-when-there-are-three-or-more-categories"></a>Prever uma categoria (quando há três ou mais categorias)

A classificação multiclasse pode ser usada para categorizar os dados em três ou mais classes.

![Os exemplos de classificação multiclasse que incluem a classificação de documentos e de produtos, roteamento de tíquete de suporte e priorização de problemas do cliente](media/multiclass-classification-examples.png)

A classificação de problema pode ser usada para categorizar os problemas de comentários (por exemplo, sobre o GitHub) do cliente usando o título do problema e a descrição. É um exemplo da tarefa de aprendizado de máquina de classificação de várias classes.

Você poderá usar o modelo de classificação do problema para seu cenário se quiser categorizar os dados em três ou mais categorias.

#### <a name="predict-a-number"></a>Prever um número

A regressão é usada para prever números.

![Diagrama mostrando exemplos de regressão, como a previsão de preços, a previsão de vendas e a manutenção preditiva](media/regression-examples.png)

A previsão de preço pode ser usada para prever preços de casas usando local, tamanho e outras características da casa. É um exemplo da tarefa de aprendizado de máquina de regressão.

Você poderá usar o modelo de previsão de preço para o seu cenário se quiser prever um valor numérico com seu próprio conjunto de dados.

#### <a name="classify-images-into-categories"></a>Classificar imagens em categorias

Esse cenário é um caso especial de classificação multiclasse, em que os dados de entrada a serem categorizados são um conjunto de imagens.

A classificação de imagem pode ser usada para identificar imagens de diferentes categorias. Por exemplo, tipos diferentes de terrenos, animais ou defeitos de fabricação.

Você pode usar o modelo de classificação de imagem para seu cenário se tiver um conjunto de imagens e quiser classificar as imagens em diferentes categorias.

#### <a name="custom-scenario"></a>Cenário personalizado

O cenário personalizado permite que você escolha manualmente seu cenário.

## <a name="data"></a>Dados

Depois de escolher seu cenário, o construtor de modelos solicitará que você forneça um conjunto de um. Os dados são usados para treinar, avaliar e escolher o melhor modelo para seu cenário.

![Diagrama mostrando as etapas do Construtor de Modelos](media/model-builder-steps.png)

O construtor de modelos dá suporte a conjuntos de dados nos formatos. TSV,. csv,. txt, bem como no formato de banco de dados SQL. Se você tiver um arquivo. txt, as colunas deverão ser separadas com `,`, `;` ou `/t` e o arquivo deverá ter uma linha de cabeçalho.

Se o conjunto de ativos for composto de imagens, os tipos de arquivo com suporte serão `.jpg` e `.png`.

Para obter mais informações, consulte [carregar dados de treinamento no construtor de modelos](how-to-guides/load-data-model-builder.md).

### <a name="choose-the-output-to-predict-label"></a>Escolha a saída para prever (rótulo)

Um conjunto de dados é uma tabela de linhas de exemplos de treinamento e colunas de atributos. Cada linha tem:

- um **rótulo** (o atributo que você deseja prever)
- **recursos** (atributos que são usados como entradas para prever o rótulo).

Para o cenário de previsão do preço das casas, os recursos podem ser:

- os metros quadrados da casa
- o número de quartos e banheiros
- o código postal

O rótulo é o preço histórico de casas para essa linha de valores de metro quadrado, quarto e banheiro e código postal.

![Tabela mostrando linhas e colunas de dados de preços de casas com recursos que consistem em quartos de tamanho de código postal e etiqueta de preço](media/model-builder-data.png)

### <a name="example-datasets"></a>Conjuntos de dados de amostra

Se você ainda não tiver seus próprios dados, experimente um desses conjuntos de dados:

|Cenário|Tarefa ML|Dados|Rótulo|Recursos|
|-|-|-|-|-|
|Previsão de preço|regressão|[dados de tarifas de táxi](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|Tarifa|Tempo da corrida, distância|
|Detecção de anomalias|classificação binária|[dados de vendas do produto](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|Vendas do Produto|Mês|
|Análise de Sentimento|classificação binária|[dados de comentário do site](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|Rótulo (0 quando o sentimento é negativo, 1 quando é positivo)|Comentário, ano|
|Detecção de fraude|classificação binária|[dados do cartão de crédito](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|Classe (1 quando fraudulenta, caso contrário, 0)|Quantidade, V1-V28 (recursos anônimos)|
|Classificação de texto|classificação multiclasse|[dados de problema do GitHub](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|Área|Título, Descrição|
|Classificação de imagens|classificação multiclasse|[Imagens de flores](http://download.tensorflow.org/example_images/flower_photos.tgz)|O tipo de flor: Margarida, dandelion, rosas, flores, tulips|Os próprios dados da imagem|

## <a name="train"></a>Treinar

Depois de selecionar seu cenário, dados e rótulo, o Construtor de Modelo treina o modelo.

### <a name="what-is-training"></a>O que é o treinamento?

O treinamento é um processo automático pelo qual Construtor de Modelo ensina seu modelo a responder perguntas para seu cenário. Depois de treinado, seu modelo pode fazer previsões com dados de entrada não vistos antes. Por exemplo, se estiver prevendo preços de casas e uma nova casa for oferecida no mercado, você poderá prever o preço de venda.

Como o Construtor de Modelo usa aprendizado de máquina automatizado (AutoML), ele não requer nenhuma entrada ou ajuste de você durante o treinamento.

### <a name="how-long-should-i-train-for"></a>Por quanto tempo devo treinar?

O construtor de modelos usa AutoML para explorar vários modelos para encontrar o modelo de melhor desempenho.

Períodos de treinamento mais longos permitem que o AutoML Explore mais modelos com uma ampla gama de configurações.

A tabela a seguir resume o tempo médio necessário para obter um bom desempenho para um conjunto de conjuntos de data de exemplo, em um computador local.

|Tamanho do conjunto de um|Tempo médio para treinar|
|------------|---------------------|
|0-10 MB|10 s|
|10-100 MB|10 min|
|100-500 MB|30 min|
|500-1 GB|60 min|
|1 GB +|mais de 3 horas|

Esses números são apenas um guia. O tamanho exato do treinamento depende de:

- o número de recursos (colunas) que estão sendo usados como entrada para o modelo
- o tipo de colunas
- a tarefa ML
- o desempenho de CPU, disco e memória do computador usado para treinamento

## <a name="evaluate"></a>Avaliar o

A avaliação é o processo de medir a qualidade do seu modelo. O construtor de modelos usa o modelo treinado para fazer previsões com novos dados de teste e, em seguida, mede a qualidade das previsões.

O Construtor de Modelo divide os dados de treinamento em um conjunto de treinamento e um conjunto de teste. Os dados de treinamento (80%) são usados para treinar seu modelo e os dados de teste (20%) são retidos para avaliar seu modelo. 

### <a name="how-do-i-understand-my-model-performance"></a>Como fazer entender o desempenho do meu modelo?

Um cenário é mapeado para uma tarefa de aprendizado de máquina. Cada tarefa ML tem seu próprio conjunto de métricas de avaliação.

#### <a name="regression-for-example-price-prediction"></a>Regressão (por exemplo, previsão de preço)

A métrica padrão para problemas de regressão é RSquared, o valor de RSquared intervalos entre 0 e 1. 1 é o melhor valor possível ou, em outras palavras, quanto mais perto o valor de RSquared para 1 melhor o seu modelo está sendo executado.

Outras métricas relatadas como perda absoluta, perda de quadrado e perda de RMS são métricas adicionais, que podem ser usadas para entender como o modelo está sendo executado e compará-lo com outros modelos de regressão.

#### <a name="binary-classification-for-example-sentiment-analysis"></a>Classificação binária (por exemplo, Análise de Sentimento)

A métrica padrão para problemas de classificação é a precisão. A precisão define a proporção de previsões corretas que seu modelo está fazendo sobre o conjunto de testes. Quanto mais perto de 100% ou 1,0, melhor será.

Outras métricas relatadas como AUC (área sob a curva), que mede a taxa positiva real versus a taxa de falsos positivos deve ser maior que 0,50 para que os modelos sejam aceitáveis.

Métricas adicionais, como a pontuação F1, podem ser usadas para controlar o equilíbrio entre precisão e RECALL.

#### <a name="multi-class-classification-for-example-issue-classification-image-classification"></a>Classificação de várias classes (por exemplo, classificação de emissão, classificação de imagem)

A métrica padrão para classificação de várias classes é micro exatidão. Quanto mais próximo for a 100% ou 1,0, melhor será.

Outra métrica importante para a classificação de várias classes é a precisão da macro, semelhante à superprecisão mais próxima de 1,0 a melhor delas. Uma boa maneira de pensar sobre esses dois tipos de precisão é:

- Micro-exatidão: com que frequência um tíquete de entrada é classificado para a equipe certa?
- Precisão da macro: para uma equipe média, com que frequência um tíquete de entrada é correto para sua equipe?

### <a name="more-information-on-evaluation-metrics"></a>Mais informações sobre métricas de avaliação

Para obter mais informações, consulte [métricas de avaliação de modelo](resources/metrics.md).

## <a name="improve"></a>Aprimorar

Se a sua pontuação de desempenho do modelo não for tão boa quanto deseja, você poderá:

- Treinar por um período maior de tempo. Com mais tempo, usar o mecanismo de aprendizado de máquina automatizado para experimentar mais algoritmos e configurações.

- Adicionar mais dados. Às vezes, a quantidade de dados não é suficiente para treinar um modelo de machine learning de alta qualidade.

- Balancear seus dados. Para tarefas de classificação, certifique-se de que o conjunto de treinamento esteja equilibrado nas categorias. Por exemplo, se você tiver quatro classes para 100 exemplos de treinamento e as duas primeiras classes (tag1 e tag2) forem usadas para 90 registros, mas as outras duas (tag3 e tag4) forem usadas apenas nos 10 registros restantes, a falta de dados balanceados poderá fazer com que seu modelo tenha dificuldades para prever corretamente o tag3 ou o tag4.

## <a name="code"></a>Código

Após a fase de avaliação, o Construtor de Modelo gera um arquivo de modelo e o código que você pode usar para adicionar o modelo ao seu aplicativo. Modelos do ML.NET são salvos como um arquivo zip. O código para carregar e usar o modelo é adicionado como um novo projeto em sua solução. O Construtor de Modelo também adiciona um aplicativo de console de exemplo que você pode executar para ver seu modelo em ação.

Além disso, o Construtor de Modelo cria o código que gerou o modelo para que você possa entender as etapas usadas na geração do modelo. Você também pode usar o código de treinamento do modelo para treinar novamente seu modelo com novos dados.

## <a name="whats-next"></a>O que vem a seguir?

[Instalar](how-to-guides/install-model-builder.md) a extensão do Visual Studio do Construtor de Modelos

Experimente a [previsão de preço ou qualquer cenário de regressão](tutorials/predict-prices-with-model-builder.md)
