---
title: Estouro (erro de tempo de execução do Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: 9db79071c4895d49680352bde2d0824a3756d941
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594169"
---
# <a name="overflow-visual-basic-run-time-error"></a>Estouro (erro de tempo de execução do Visual Basic)
Um estouro ocorre quando você tentar uma atribuição que excede os limites de destino da atribuição.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Certifique-se de que os resultados do tipo de dados, cálculos e atribuições de conversões não são muito grande para ser representado dentro do intervalo permitido para esse tipo de valor de variáveis e atribuir o valor a uma variável de um tipo que podem conter um intervalo maior de valores , se necessário.  
  
2.  Certifique-se de atribuições às propriedades ajustar o intervalo da propriedade ao qual eles são feitos.  
  
3.  Certifique-se de que números usados em cálculos que são forçados em inteiros não tem resultados maiores que inteiros.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Int32.MaxValue?displayProperty=nameWithType>  
 <xref:System.Double.MaxValue?displayProperty=nameWithType>  
 [Tipos de Dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Tipos de Erro](../../../visual-basic/programming-guide/language-features/error-types.md)
