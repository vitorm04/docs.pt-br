---
title: Estouro (erro de tempo de execução do Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: 63223a815e1c4ff8d4e0afbb6c732fff90aad465
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59345541"
---
# <a name="overflow-visual-basic-run-time-error"></a>Estouro (erro de tempo de execução do Visual Basic)
Um estouro durante a tentativa de uma atribuição que excede os limites do destino da atribuição de resultados.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Certifique-se de que os resultados do tipo de dados, cálculos e atribuições de conversões não são muito grande para ser representado dentro do intervalo de coluna não são permitidos para esse tipo de valor e atribua o valor a uma variável de um tipo que podem conter um intervalo maior de valores , se necessário.  
  
2. Certifique-se de atribuições às propriedades se encaixam no intervalo da propriedade à qual elas são feitas.  
  
3. Certifique-se de que números usados em cálculos que são forçados em inteiros não tem resultados maiores do que os inteiros.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Int32.MaxValue?displayProperty=nameWithType>
- <xref:System.Double.MaxValue?displayProperty=nameWithType>
- [Tipos de Dados](../../../visual-basic/language-reference/data-types/index.md)
- [Tipos de Erro](../../../visual-basic/programming-guide/language-features/error-types.md)
