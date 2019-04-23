---
title: 'Como: Atribuir uma matriz a outra matriz (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: 78497de3a9aea55320639c55a151a1260a960159
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59303083"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a>Como: Atribuir uma matriz a outra matriz (Visual Basic)
Como as matrizes são objetos, você pode usá-los em instruções de atribuição como outros tipos de objeto. Uma variável de matriz contém um ponteiro para os dados que constituem os elementos da matriz e as informações de classificação e o comprimento e uma atribuição copia somente esse ponteiro.  
  
### <a name="to-assign-one-array-to-another-array"></a>Para atribuir uma matriz a outra matriz  
  
1. Certifique-se de que as duas matrizes têm a mesma classificação (número de dimensões) e tipos de dados do elemento compatível.  
  
2. Use uma instrução de atribuição padrão para atribuir a matriz de origem para a matriz de destino. Não siga o nome da matriz com parênteses.  
  
    ```  
    Dim formArray() As System.Windows.Forms.Form  
    Dim controlArray() As System.Windows.Forms.Control  
    controlArray = formArray  
    ```  
  
 Quando você atribuir uma matriz a outra, as seguintes regras se aplicam:  
  
-   **Classificações iguais.** A classificação (número de dimensões) da matriz de destino deve ser o mesmo que uma matriz de origem.  
  
     Desde que as classificações de duas matrizes forem iguais, as dimensões não precisam ser iguais. O número de elementos em uma determinada dimensão pode mudar durante a atribuição.  
  
-   **Tipos de elemento.** Qualquer um dos ambas as matrizes devem ter *tipo de referência* elementos ou ambas as matrizes devem ter *tipo de valor* elementos. Para obter mais informações, consulte [tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
    -   Se as duas matrizes têm elementos de tipo de valor, os tipos de dados do elemento devem ser exatamente o mesmo. A única exceção a isso é que você pode atribuir uma matriz de `Enum` elementos em uma matriz do tipo base do que `Enum`.  
  
    -   Se as duas matrizes têm referência a elementos do tipo, o tipo de elemento de origem deve derivar do tipo de elemento de destino. Quando esse for o caso, as duas matrizes têm a mesma relação de herança que seus elementos. Isso é chamado *covariância de matriz*.  
  
 O compilador relatará um erro se as regras acima forem violadas, por exemplo se os tipos de dados não são compatíveis ou as classificações são diferentes. Você pode adicionar ao seu código para certificar-se de que as matrizes são compatíveis antes de tentar uma atribuição de tratamento de erros. Você também pode usar o [operador TryCast](../../../../visual-basic/language-reference/operators/trycast-operator.md) palavra-chave se você quiser evitar lançar uma exceção.  
  
## <a name="see-also"></a>Consulte também

- [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Solução de problemas de matrizes](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [Instrução Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [Conversões de Matriz](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
