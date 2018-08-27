---
title: Estouro (erro de tempo de execução do Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: 7546676b85465577b357b7ad0757b4db8d40dbe3
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934433"
---
# <a name="overflow-visual-basic-run-time-error"></a>Estouro (erro de tempo de execução do Visual Basic)
Um estouro durante a tentativa de uma atribuição que excede os limites do destino da atribuição de resultados.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Certifique-se de que os resultados do tipo de dados, cálculos e atribuições de conversões não são muito grande para ser representado dentro do intervalo de coluna não são permitidos para esse tipo de valor e atribua o valor a uma variável de um tipo que podem conter um intervalo maior de valores , se necessário.  
  
2.  Certifique-se de atribuições às propriedades se encaixam no intervalo da propriedade à qual elas são feitas.  
  
3.  Certifique-se de que números usados em cálculos que são forçados em inteiros não tem resultados maiores do que os inteiros.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Int32.MaxValue?displayProperty=nameWithType>  
 <xref:System.Double.MaxValue?displayProperty=nameWithType>  
 [Tipos de Dados](../../../visual-basic/language-reference/data-types/index.md)  
 [Tipos de Erro](../../../visual-basic/programming-guide/language-features/error-types.md)
