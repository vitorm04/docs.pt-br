---
title: Números de ponto flutuante
ms.date: 03/30/2017
ms.assetid: 73c218c6-1c44-4402-a167-4f6262629a91
ms.openlocfilehash: a30252d7d25b3c3e09dd5e59f364d94aa40dd272
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55903964"
---
# <a name="floating-point-numbers"></a>Números de ponto flutuante
Este tópico descreve alguns dos problemas que os desenvolvedores geralmente encontram ao trabalhar com números de ponto flutuantes em [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. Esses problemas são causados pela maneira como que os computadores armazenam números de ponto flutuante e não são específicas para um provedor específico, como <xref:System.Data.SqlClient> ou <xref:System.Data.OracleClient>.  
  
 Números de ponto flutuante geralmente não têm uma representação binária exata. Em vez disso, o computador armazena uma aproximação do número. Em momentos diferentes, os números diferentes de dígitos binários podem ser usados para representar o número. Quando um flutuante ponto número é convertido de uma representação para outra representação, os dígitos menos significantes desse número pode variar um pouco. Normalmente, a conversão ocorre quando o número é convertido de um tipo em outro tipo. A variação ocorre se a conversão ocorre dentro de um banco de dados entre os tipos que representam valores de banco de dados ou entre tipos. Por causa dessas alterações, números logicamente seria iguais podem ter alterações em seus dígitos menos significativos que fazem com que têm valores diferentes. O número de dígitos de precisão no número pode ser maior ou menor que o esperado. Quando formatado como uma cadeia de caracteres, o número não pode mostrar o valor esperado.  
  
 Para minimizar esses efeitos, você deve usar a correspondência mais próxima entre tipos numéricos que estão disponíveis para você. Por exemplo, se você estiver trabalhando com o SQL Server, o valor numérico exato pode alterar se você converter um valor de Transact-SQL de tipo real para um valor do tipo float. No [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], convertendo um <xref:System.Single> para um <xref:System.Double> também pode produzir resultados inesperados. Em ambos os casos, uma boa estratégia é fazer todos os valores em do aplicativo, use o mesmo tipo numérico. Você também pode usar um tipo decimal de precisão fixa ou converter números de ponto flutuante para um tipo decimal de precisão fixa antes de trabalhar com eles.  
  
 Para solucionar problemas com a comparação de igualdade, considere a possibilidade de codificação do seu aplicativo para que as variações nos dígitos menos significantes são ignoradas. Por exemplo, em vez de comparar para ver se os dois números são iguais, subtrai um número de outro número. Se a diferença for dentro de uma margem aceitável de arredondamento, seu aplicativo pode tratar os números como se eles forem iguais.  
  
## <a name="see-also"></a>Consulte também
- [Por que números de ponto flutuante podem perder a precisão](/cpp/build/reference/why-floating-point-numbers-may-lose-precision)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
