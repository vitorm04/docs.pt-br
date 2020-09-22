---
title: Estouro (erro de tempo de execução do Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: e287d6c24eca75d8bf20181a201056f467d6fc4e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871215"
---
# <a name="overflow-visual-basic-run-time-error"></a>Estouro (erro de tempo de execução do Visual Basic)

Um estouro resulta quando você tenta uma atribuição que excede os limites do destino da atribuição.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Verifique se os resultados de atribuições, cálculos e conversões de tipo de dados não são muito grandes para serem representados no intervalo de variáveis permitidas para esse tipo de valor e atribua o valor a uma variável de um tipo que possa conter um intervalo maior de valores, se necessário.  
  
2. Certifique-se de que as atribuições às propriedades caibam no intervalo da propriedade na qual elas são feitas.  
  
3. Verifique se os números usados em cálculos que são conforçados em inteiros não têm resultados maiores do que os inteiros.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Int32.MaxValue?displayProperty=nameWithType>
- <xref:System.Double.MaxValue?displayProperty=nameWithType>
- [Data Types](../data-types/index.md)
- [Tipos de erro](../../programming-guide/language-features/error-types.md)
