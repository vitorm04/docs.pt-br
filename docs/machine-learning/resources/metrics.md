---
title: Métricas do ML.NET
description: Entenda as métricas que são usadas para avaliar o desempenho de um modelo do ML.NET
ms.date: 04/29/2019
author: natke
ms.openlocfilehash: 45176902a195906e7b5cffd24fc9da839406ad9d
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410527"
---
# <a name="model-evaluation-metrics-in-mlnet"></a>Métricas de avaliação de modelo do ML.NET

## <a name="metrics-for-binary-classification"></a>Métricas para classificação binária

| Métricas   |      DESCRIÇÃO      |  Procurar |
|-----------|-----------------------|-----------|
| **Precisão** |  [Precisão](https://en.wikipedia.org/wiki/Accuracy_and_precision#In_binary_classification) é a proporção de previsões corretas com um conjunto de dados de teste. É a taxa do número de previsões corretas para o número total de amostras de entrada. Ele funcionará bem apenas se houver um número semelhante de amostras que pertencem a cada classe.| **Quanto mais próximo de 1,00, melhor**. Mas exatamente 1,00 indica um problema (geralmente: vazamento de rótulo/destino, ajuste excessivo ou teste com os dados de treinamento). Quando os dados de teste estão desbalanceados (em que a maioria das instâncias pertence a uma das classes), o conjunto de dados é muito pequeno ou as pontuações se aproximam de 0,00 ou 1,00, a precisão realmente não captura a eficácia de um classificador e você precisa verificar métricas adicionais. |
| **AUC** |    [aucROC](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) ou *área sob a curva*: Isso está medindo a área sob a curva criada varrendo a taxa de positivos verdadeiros versus a taxa de falsos positivos.  |   **Quanto mais próximo de 1,00, melhor**. Ela deve ser maior que 0.50 para que um modelo seja aceitável; um modelo com AUC de 0.50 ou menos é inútil. |
| **AUCPR** | [aucPR](https://www.coursera.org/lecture/ml-classification/precision-recall-curve-rENu8) ou *área sob a curva de uma curva de recall de precisão*: Medida útil de sucesso da previsão quando as classes estão muito desequilibradas (conjuntos de dados altamente distorcidos). |  **Quanto mais próximo de 1,00, melhor**. Pontuações elevadas próximas de 1,00 mostram que o classificador retorna resultados precisos (precisão alta), além de retornar uma maioria de todos os resultados positivos (recall alto). |
| **Pontuação F1** | A [pontuação F1](https://en.wikipedia.org/wiki/F1_score), também conhecida como *pontuação F balanceada ou medida F*. É a média harmônica da precisão e do recall. A pontuação F1 é útil quando você deseja buscar um equilíbrio entre a precisão e o recall.| **Quanto mais próximo de 1,00, melhor**.  Uma pontuação F1 atinge seu melhor valor em 1,00 e o pior em 0,00. Ela informa o nível de precisão do classificador. |

Para obter mais detalhes sobre as métricas de classificação binária, leia os artigos a seguir:

- [Exatidão, Precisão, Recall ou F1?](https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9)
- [Classe de métricas de classificação binária](xref:Microsoft.ML.Data.BinaryClassificationMetrics)
- [A relação entre a recall de precisão e curvas ROC](http://pages.cs.wisc.edu/~jdavis/davisgoadrichcamera2.pdf)

## <a name="metrics-for-multi-class-classification"></a>Métricas para classificação multiclasse

| Métricas   |      DESCRIÇÃO      |  Procurar |
|-----------|-----------------------|-----------|
| **Microprecisão** |  A [precisão de micromédia](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MicroAccuracy) agrega as contribuições de todas as classes para computar a métrica média. Ela é a fração de instâncias previstas corretamente. A micromédia não leva membros da classe em consideração. Basicamente, cada par de classe de exemplo contribui igualmente para a métrica de precisão. | **Quanto mais próximo de 1,00, melhor**. Em uma tarefa de classificação multiclasse, a microprecisão será preferível à macroprecisão se você suspeitar que há desequilíbrio de classe (ou seja, você pode ter muitos outros exemplos de uma classe do que de outras classes).|
| **Macroprecisão** | A [precisão de macromédia](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MacroAccuracy) é a precisão média no nível de classe. A precisão para cada classe é calculada e a macroprecisão é a média desses precisões. Basicamente, cada classe contribui igualmente para a métrica de precisão. Classes minoritárias recebem o mesmo peso que as classes maiores. A métrica de macromédia fornece o mesmo peso a cada classe, não importa quantas instâncias dessa classe o conjunto de dados contém. |  **Quanto mais próximo de 1,00, melhor**.  Ele calcula a métrica de forma independente para cada classe e, em seguida, usa a média (tratando assim todas as classes igualmente) |
| **Perda logarítmica**| A [perda logarítmica](http://wiki.fast.ai/index.php/Log_Loss) mede o desempenho de um modelo de classificação em que a entrada de previsão é um valor de probabilidade entre 0,00 e 1,00. A perda logarítmica aumenta à medida que a probabilidade prevista diverge do rótulo real. | **Quanto mais próximo de 0,00, melhor**. Um modelo perfeito teria uma perda logarítmica de 0,00. A meta dos nossos modelos de machine learning é minimizar esse valor.|
| **Redução de perda logarítmica** | A [redução de perda logarítmica](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.LogLossReduction) pode ser interpretada como a vantagem do classificador sobre uma previsão aleatória.| **Varia de -inf a 1,00, em que 1,00 é uma previsão perfeita e 0,00 indica previsões péssimas**. Por exemplo, se o valor for igual a 0,20, ele poderá ser interpretado como "a probabilidade de uma previsão correta é 20% melhor do que a previsão aleatória"|

A microprecisão geralmente se alinha melhor com as necessidades de negócios de previsões de ML. Se você desejar selecionar uma única métrica para escolher a qualidade de uma tarefa de classificação multiclasse, geralmente ela deverá ser microprecisão.

Exemplo de uma tarefa de classificação do tíquete de suporte: (mapeia tíquetes de entrada para equipes de suporte)

- Microprecisão – com que frequência um tíquete de entrada é classificado para a equipe certa?
- Macroprecisão – para uma equipe de média, com que frequência um tíquete de entrada é correto para sua equipe?

A macroprecisão sobrecarrega equipes pequenas neste exemplo; uma equipe pequena, que obtém apenas dez tíquetes por ano, conta tanto quanto uma equipe grande, com dez mil tíquetes por ano. Nesse caso, a microprecisão se correlaciona melhor com a necessidade de negócios de "a quantidade de tempo e dinheiro que a empresa pode salvar automatizando meu processo de roteamento de tíquetes".

Para obter mais detalhes sobre métricas de classificação multiclasse, leia os artigos a seguir:

- [Micro e macromédia de precisão, recall e pontuação F](http://rushdishams.blogspot.com/2011/08/micro-and-macro-average-of-precision.html)
- [Classificação multiclasse com conjunto de dados em desequilíbrio](https://towardsdatascience.com/machine-learning-multiclass-classification-with-imbalanced-data-set-29f6a177c1a)

## <a name="metrics-for-regression"></a>Métricas de regressão

| Métricas   |      DESCRIÇÃO      |  Procurar |
|-----------|-----------------------|-----------|
| **R quadrado** |  O [R2 (R quadrado)](https://en.wikipedia.org/wiki/Coefficient_of_determination) ou *coeficiente de determinação* representa a capacidade de previsão do modelo como um valor entre -inf e 1,00. 1,00 significa que há um ajuste perfeito e o ajuste pode ser arbitrariamente ruim. Portanto, as pontuações podem ser negativas. Uma pontuação de 0,00 significa quo modelo está adivinhando o valor esperado para o rótulo. R2 mede o quão próximos os valores de dados de teste reais são dos valores previstos. | **Quanto mais próximo de 1,00, melhor a qualidade**. No entanto, às vezes, valores de R quadrado baixos (por exemplo, 0,50) podem ser totalmente normais suficientemente bons para seu cenário, enquanto valores de R quadrado altos nem sempre são bons. Convém sempre suspeitar. |
| **Perda absoluta** |  A [perda absoluta](https://en.wikipedia.org/wiki/Mean_absolute_error) ou *MAE (erro de média absoluta)* mede o quão próximas as previsões são dos resultados reais. É a média de todos os erros do modelo, em que o erro do modelo é a distância absoluta entre o valor de rótulo previsto e o valor de rótulo correto. Esse erro de previsão é calculado para cada registro do conjunto de dados de teste. Por fim, o valor médio é calculado para todos os erros absolutos gravados.| **Quanto mais próximo de 0,00, melhor a qualidade.** Observe que o erro de média absoluta usa a mesma escala que os dados que estão sendo medidos (não são normalizados para o intervalo específico). Perda absoluta, perda quadrática e perda de RMS somente podem ser usadas para fazer comparações entre modelos para o mesmo conjunto de dados ou com um conjunto de dados com uma distribuição de valor de rótulo similar. |
| **Perda quadrática** |  [Perda quadrática](https://en.wikipedia.org/wiki/Mean_squared_error) ou *MSE (erro médio quadrático)* , também chamado de *MSD (desvio médio quadrático)* , informa como fechar uma linha de regressão é para um conjunto de valores de dados de teste. Ele faz isso utilizando as distâncias entre os pontos e a linha de regressão (essas distâncias são os erros E) e elevando-as ao quadrado. Elevar ao quadrado dá mais peso para diferenças maiores. | É sempre positivo, e **valores mais próximos de 0,00 são melhores**. Dependendo de seus dados, pode ser impossível obter um valor muito pequeno para o erro médio quadrático.|
| **Perda de RMS** |  A [perda de RMS](https://en.wikipedia.org/wiki/Root-mean-square_deviation) ou *RMSE (raiz do erro médio quadrático)* , também chamada de *RMSD (raiz do desvio médio quadrático*), mede a diferença entre valores previstos por um modelo e os valores realmente observados no ambiente que está sendo modelado. A perda de RMS é a raiz quadrada da perda quadrática e tem as mesmas unidades que o rótulo, de modo semelhante à perda absoluta, mas dando mais peso para diferenças maiores. A raiz do erro médio quadrático normalmente é usada em climatologia, previsão e análise de regressão para verificar resultados experimentais. | É sempre positivo, e **valores mais próximos de 0,00 são melhores**. RMSD é uma medida de precisão, para comparar os erros de previsão de modelos diferentes para um conjunto de dados específico e não entre conjuntos de dados, já que ela é dependente de escala.|

Para obter mais detalhes sobre as métricas de regressão, leia os artigos a seguir:

- [Análise de regressão: como interpretar R quadrado e avaliar a adequação do ajuste?](https://blog.minitab.com/blog/adventures-in-statistics-2/regression-analysis-how-do-i-interpret-r-squared-and-assess-the-goodness-of-fit)
- [Como interpretar R quadrado na análise de regressão](https://statisticsbyjim.com/regression/interpret-r-squared-regression)
- [Definição de R quadrado](https://www.investopedia.com/terms/r/r-squared.asp)
- [Definição de erro médio quadrático](https://www.statisticshowto.datasciencecentral.com/mean-squared-error/)
- [O que são o erro médio quadrático e a raiz do erro médio quadrático?](https://www.vernier.com/til/1014/)
