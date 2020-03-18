---
title: Métricas do ML.NET
description: Entenda as métricas que são usadas para avaliar o desempenho de um modelo do ML.NET
ms.date: 12/17/2019
ms.openlocfilehash: 8e823fd8cc344c1b8e0ecd709b527137368cbfa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399213"
---
# <a name="evaluate-your-mlnet-model-with-metrics"></a>Avalie seu modelo de ML.NET com métricas

Entenda as métricas utilizadas para avaliar um modelo ML.NET.

As métricas de avaliação são específicas para o tipo de tarefa de aprendizado de máquina que um modelo realiza.

Por exemplo, para a tarefa de classificação, o modelo é avaliado medindo o quão bem uma categoria prevista corresponde à categoria real. E para agrupamento, a avaliação baseia-se no quão próximos os itens agrupados estão entre si, e quanta separação há entre os clusters.

## <a name="evaluation-metrics-for-binary-classification"></a>Métricas de avaliação para Classificação Binária

| Métricas   |      Descrição      |  Procurar |
|-----------|-----------------------|-----------|
| **Precisão** |  [Precisão](https://en.wikipedia.org/wiki/Accuracy_and_precision#In_binary_classification) é a proporção de previsões corretas com um conjunto de dados de teste. É a taxa do número de previsões corretas para o número total de amostras de entrada. Funciona bem se houver um número semelhante de amostras pertencentes a cada classe.| **Quanto mais próximo de 1,00, melhor**. Mas exatamente 1,00 indica um problema (geralmente: vazamento de rótulo/destino, ajuste excessivo ou teste com os dados de treinamento). Quando os dados do teste são desequilibrados (onde a maioria das instâncias pertence a uma das classes), o conjunto de dados é pequeno, ou as pontuações se aproximam de 0,00 ou 1,00, então a precisão realmente não captura a eficácia de um classificador e você precisa verificar métricas adicionais. |
| **AUC** |    [aucROC](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) ou *Área a curva* mede a área a curva criada varrendo a verdadeira taxa positiva versus a taxa falsa positiva.  |   **Quanto mais próximo de 1,00, melhor**. Deve ser maior que 0,50 para um modelo ser aceitável. Um modelo com AUC de 0,50 ou menos é inútil. |
| **AUCPR** | [aucPR](https://www.coursera.org/lecture/ml-classification/precision-recall-curve-rENu8) ou *Área a curva de uma curva Precisão-Recall*: Medida útil de sucesso da previsão quando as classes estão desequilibradas (conjuntos de dados altamente distorcidos). |  **Quanto mais próximo de 1,00, melhor**. Pontuações elevadas próximas de 1,00 mostram que o classificador retorna resultados precisos (precisão alta), além de retornar uma maioria de todos os resultados positivos (recall alto). |
| **Pontuação F1** | A [pontuação F1](https://en.wikipedia.org/wiki/F1_score), também conhecida como *pontuação F balanceada ou medida F*. É a média harmônica da precisão e do recall. A pontuação F1 é útil quando você deseja buscar um equilíbrio entre a precisão e o recall.| **Quanto mais próximo de 1,00, melhor**.  Uma pontuação F1 atinge seu melhor valor em 1,00 e o pior em 0,00. Ela informa o nível de precisão do classificador. |

Para obter mais detalhes sobre as métricas de classificação binária, leia os artigos a seguir:

- [Precisão, precisão, recall ou F1?](https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9)
- [Classe de métricas de classificação binária](xref:Microsoft.ML.Data.BinaryClassificationMetrics)
- [A relação entre a recall de precisão e curvas ROC](http://pages.cs.wisc.edu/~jdavis/davisgoadrichcamera2.pdf)

## <a name="evaluation-metrics-for-multi-class-classification"></a>Métricas de avaliação para classificação multiclasse

| Métricas   |      Descrição      |  Procurar |
|-----------|-----------------------|-----------|
| **Microprecisão** |  A [precisão de micromédia](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MicroAccuracy) agrega as contribuições de todas as classes para computar a métrica média. Ela é a fração de instâncias previstas corretamente. A micromédia não leva membros da classe em consideração. Basicamente, cada par de classe de exemplo contribui igualmente para a métrica de precisão. | **Quanto mais próximo de 1,00, melhor**. Em uma tarefa de classificação multiclasse, a microprecisão será preferível à macroprecisão se você suspeitar que há desequilíbrio de classe (ou seja, você pode ter muitos outros exemplos de uma classe do que de outras classes).|
| **Macroprecisão** | A [precisão de macromédia](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MacroAccuracy) é a precisão média no nível de classe. A precisão para cada classe é calculada e a macroprecisão é a média desses precisões. Basicamente, cada classe contribui igualmente para a métrica de precisão. Classes minoritárias recebem o mesmo peso que as classes maiores. A métrica de macromédia fornece o mesmo peso a cada classe, não importa quantas instâncias dessa classe o conjunto de dados contém. |  **Quanto mais próximo de 1,00, melhor**.  Ele calcula a métrica de forma independente para cada classe e, em seguida, usa a média (tratando assim todas as classes igualmente) |
| **Perda de log**| A [perda logarítmica](http://wiki.fast.ai/index.php/Log_Loss) mede o desempenho de um modelo de classificação em que a entrada de previsão é um valor de probabilidade entre 0,00 e 1,00. A perda logarítmica aumenta à medida que a probabilidade prevista diverge do rótulo real. | **Quanto mais próximo de 0,00, melhor**. Um modelo perfeito teria uma perda logarítmica de 0,00. A meta dos nossos modelos de machine learning é minimizar esse valor.|
| **Redução de perda logarítmica** | A [redução de perda logarítmica](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.LogLossReduction) pode ser interpretada como a vantagem do classificador sobre uma previsão aleatória.| **Varia de -inf a 1,00, em que 1,00 é uma previsão perfeita e 0,00 indica previsões péssimas**. Por exemplo, se o valor for igual a 0,20, ele poderá ser interpretado como "a probabilidade de uma previsão correta é 20% melhor do que a previsão aleatória"|

A microprecisão geralmente se alinha melhor com as necessidades de negócios de previsões de ML. Se você desejar selecionar uma única métrica para escolher a qualidade de uma tarefa de classificação multiclasse, geralmente ela deverá ser microprecisão.

Exemplo de uma tarefa de classificação do tíquete de suporte: (mapeia tíquetes de entrada para equipes de suporte)

- Microprecisão – com que frequência um tíquete de entrada é classificado para a equipe certa?
- Macroprecisão – para uma equipe de média, com que frequência um tíquete de entrada é correto para sua equipe?

O excesso de macroprecisão sobrepeso das pequenas equipes neste exemplo; uma equipe pequena que recebe apenas 10 ingressos por ano conta tanto quanto um grande time com 10mil ingressos por ano. Nesse caso, a microprecisão se correlaciona melhor com a necessidade de negócios de "a quantidade de tempo e dinheiro que a empresa pode salvar automatizando meu processo de roteamento de tíquetes".

Para obter mais detalhes sobre métricas de classificação multiclasse, leia os artigos a seguir:

- [Micro e Macro-média de Precisão, Recall e Pontuação F](https://rushdishams.blogspot.com/2011/08/micro-and-macro-average-of-precision.html)
- [Classificação multiclasse com conjunto de dados em desequilíbrio](https://towardsdatascience.com/machine-learning-multiclass-classification-with-imbalanced-data-set-29f6a177c1a)

## <a name="evaluation-metrics-for-regression-and-recommendation"></a>Métricas de avaliação para Regressão e Recomendação

Tanto as tarefas de regressão quanto de recomendação prevêem um número. No caso de regressão, o número pode ser qualquer propriedade de saída que seja influenciada pelas propriedades de entrada. Para recomendação, o número é geralmente um valor de classificação (entre 1 e 5, por exemplo), ou uma recomendação sim/não (representada por 1 e 0, respectivamente).

| Métrica   |      Descrição      |  Procurar |
|----------|-----------------------|-----------|
| **R quadrado** |  O [R2 (R quadrado)](https://en.wikipedia.org/wiki/Coefficient_of_determination) ou *coeficiente de determinação* representa a capacidade de previsão do modelo como um valor entre -inf e 1,00. 1,00 significa que há um ajuste perfeito e o ajuste pode ser arbitrariamente ruim. Portanto, as pontuações podem ser negativas. Uma pontuação de 0,00 significa quo modelo está adivinhando o valor esperado para o rótulo. R2 mede o quão próximos os valores de dados de teste reais são dos valores previstos. | **Quanto mais próximo de 1,00, melhor a qualidade**. No entanto, às vezes, valores de R quadrado baixos (por exemplo, 0,50) podem ser totalmente normais suficientemente bons para seu cenário, enquanto valores de R quadrado altos nem sempre são bons. Convém sempre suspeitar. |
| **Perda absoluta** |  A [perda absoluta](https://en.wikipedia.org/wiki/Mean_absolute_error) ou *MAE (erro de média absoluta)* mede o quão próximas as previsões são dos resultados reais. É a média de todos os erros do modelo, em que o erro do modelo é a distância absoluta entre o valor de rótulo previsto e o valor de rótulo correto. Esse erro de previsão é calculado para cada registro do conjunto de dados de teste. Por fim, o valor médio é calculado para todos os erros absolutos gravados.| **Quanto mais próximo de 0,00, melhor a qualidade.** O erro absoluto médio usa a mesma escala que os dados que estão sendo medidos (não é normalizado para faixa específica). Perda absoluta, perda quadrática e perda de RMS somente podem ser usadas para fazer comparações entre modelos para o mesmo conjunto de dados ou com um conjunto de dados com uma distribuição de valor de rótulo similar. |
| **Perda quadrada** |  [A perda quadrada](https://en.wikipedia.org/wiki/Mean_squared_error) ou *erro quadrado médio (MSE)*, também chamado *de Desvio Quadrado Médio (MSD),* informa o quão perto uma linha de regressão é de um conjunto de valores de dados de teste, tomando as distâncias dos pontos para a linha de regressão (essas distâncias são os erros E) e esquartejando-os. Elevar ao quadrado dá mais peso para diferenças maiores. | É sempre positivo, e **valores mais próximos de 0,00 são melhores**. Dependendo de seus dados, pode ser impossível obter um valor muito pequeno para o erro médio quadrático.|
| **Perda de RMS** |  [RMS-loss](https://en.wikipedia.org/wiki/Root-mean-square_deviation) ou *Root Mean Squared Error (RMSE)* (também chamado *de Root Mean Square Deviation, RMSD*), mede a diferença entre os valores previstos por um modelo e os valores observados do ambiente que está sendo modelado. A perda de RMS é a raiz quadrada da perda quadrática e tem as mesmas unidades que o rótulo, de modo semelhante à perda absoluta, mas dando mais peso para diferenças maiores. A raiz do erro médio quadrático normalmente é usada em climatologia, previsão e análise de regressão para verificar resultados experimentais. | É sempre positivo, e **valores mais próximos de 0,00 são melhores**. RMSD é uma medida de precisão, para comparar os erros de previsão de modelos diferentes para um conjunto de dados específico e não entre conjuntos de dados, já que ela é dependente de escala.|

Para obter mais detalhes sobre as métricas de regressão, leia os artigos a seguir:

- [Análise de regressão: Como interpreto r-quadrado e avalio a bondade do ajuste?](https://blog.minitab.com/blog/adventures-in-statistics-2/regression-analysis-how-do-i-interpret-r-squared-and-assess-the-goodness-of-fit)
- [Como interpretar R quadrado na análise de regressão](https://statisticsbyjim.com/regression/interpret-r-squared-regression)
- [Definição de R quadrado](https://www.investopedia.com/terms/r/r-squared.asp)
- [Definição de erro médio quadrático](https://www.statisticshowto.datasciencecentral.com/mean-squared-error/)
- [O que são o erro médio quadrático e a raiz do erro médio quadrático?](https://www.vernier.com/til/1014/)

## <a name="evaluation-metrics-for-clustering"></a>Métricas de avaliação para Clustering

| Métrica   |      Descrição      |  Procurar |
|----------|-----------------------|-----------|
|**Distância média**|Média da distância entre os pontos de dados e o centro de seu cluster atribuído. A distância média é uma medida de proximidade dos pontos de dados para centrosides de cluster. É uma medida de quão "apertado" o cluster é.|Valores mais próximos de **0** são melhores. Quanto mais perto de zero a distância média é, mais agrupados os dados são. Observe, porém, que essa métrica diminuirá se o número de clusters for aumentado, e no caso extremo (onde cada ponto de dados distinto é seu próprio cluster) será igual a zero.
|**Índice Davies Bouldin**|A razão média de distâncias dentro do cluster para distâncias entre os aglomerados. Quanto mais apertado o cluster, e quanto mais distantes forem os aglomerados, menor será esse valor.|Valores mais próximos de **0** são melhores. Clusters mais distantes e menos dispersos resultarão em uma pontuação melhor.|
|**Informações mútuas normalizadas**|Pode ser usado quando os dados de treinamento usados para treinar o modelo de clustering também vêm com etiquetas de verdade moída (ou seja, clustering supervisionado). A métrica Normalized Mutual Information mede se pontos de dados semelhantes são atribuídos ao mesmo cluster e pontos de dados diferentes são atribuídos a diferentes clusters. Informação mútua normalizada é um valor entre 0 e 1|Valores mais próximos de **1** são melhores|

## <a name="evaluation-metrics-for-ranking"></a>Métricas de avaliação para Ranking

| Métrica   |      Descrição      |  Procurar |
|----------|-----------------------|-----------|
|**Ganhos acumulados descontados**|O ganho acumulado descontado (DCG) é uma medida da qualidade do ranking. É derivado de duas suposições. Um: Itens altamente relevantes são mais úteis quando aparecem mais alto na ordem de classificação. Dois: A utilidade rastreia a relevância que é, quanto maior a relevância, mais útil é um item. O ganho acumulado descontado é calculado para uma posição específica na ordem de classificação. Ele resume a classificação de relevância dividida pelo logaritmo do índice de classificação até a posição de interesse. Ele é calculado usando $\sum_{i=0}^{p} \frac {rel_i} {\log_{e}{i+1}}$ Classificações de relevância são fornecidas a um algoritmo de treinamento de classificação como rótulos de verdade terrestre. Um valor DCG é fornecido para cada posição na tabela de classificação, daí o nome **Ganhos Acumulados**Descontados . |**Valores mais altos são melhores**|
|**Ganhos acumulados descontados normalizados**|A normalização do DCG permite que a métrica seja comparada para listas de classificação de diferentes comprimentos|**Valores mais próximos de 1 são melhores**|

## <a name="evaluation-metrics-for-anomaly-detection"></a>Métricas de avaliação para detecção de anomalias

| Métrica   |      Descrição      |  Procurar |
|----------|-----------------------|-----------|
|**Área curva ROC**|A área a curva do operador receptor mede o quão bem o modelo separa pontos de dados anômalos e usuais.|**Valores mais próximos de 1 são melhores**. Apenas valores superiores a 0,5 demonstram eficácia do modelo. Valores de 0,5 ou abaixo indicam que o modelo não é melhor do que alocar aleatoriamente as entradas para categorias anômalas e usuais|
|**Taxa de detecção em contagem falsa positiva**|Taxa de detecção na contagem de falsos positivos é a razão do número de anomalias corretamente identificadas com o número total de anomalias em um conjunto de testes, indexada por cada falso positivo. Ou seja, há um valor para taxa de detecção em falsa contagem positiva para cada item falso positivo.|**Valores mais próximos de 1 são melhores**. Se não há falsos positivos, então este valor é 1|
