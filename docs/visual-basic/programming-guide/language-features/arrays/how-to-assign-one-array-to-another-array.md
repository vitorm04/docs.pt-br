---
title: 'Como: atribuir uma matriz a outra matriz (Visual Basic) | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
caps.latest.revision: 18
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fe97ec82205d89b18532758c93c719e4b30a335d
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a>Como atribuir uma matriz a outra matriz (Visual Basic)
Como matrizes são objetos, você pode usá-los em instruções de atribuição como outros tipos de objeto. Uma variável de matriz contém um ponteiro para os dados que constituem os elementos da matriz e as informações de posição e comprimento, e uma atribuição copia somente esse ponteiro.  
  
### <a name="to-assign-one-array-to-another-array"></a>Para atribuir uma matriz a outra matriz  
  
1.  Verifique se as duas matrizes têm a mesma classificação (número de dimensões) e tipos de dados de elemento compatíveis.  
  
2.  Use uma instrução de atribuição padrão para atribuir a matriz de origem para a matriz de destino. Não siga o nome da matriz com parênteses.  
  
    ```  
    Dim formArray() As System.Windows.Forms.Form  
    Dim controlArray() As System.Windows.Forms.Control  
    controlArray = formArray  
    ```  
  
 Quando você atribuir uma matriz a outra, as seguintes regras se aplicam:  
  
-   **Ordens iguais.** A classificação (número de dimensões) da matriz de destino deve ser o mesmo que a matriz de origem.  
  
     Desde que as classificações de duas matrizes forem iguais, as dimensões não precisam ser iguais. O número de elementos em uma determinada dimensão pode mudar durante a atribuição.  
  
-   **Tipos de elemento.** A ambas as matrizes devem ter *tipo de referência* elementos ou ambas as matrizes devem ter *tipo de valor* elementos. Para obter mais informações, consulte [tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
    -   Se as duas matrizes têm elementos de tipo de valor, os tipos de dados do elemento devem ser exatamente o mesmo. A única exceção a isso é que você pode atribuir uma matriz de `Enum` elementos em uma matriz do tipo base do que `Enum`.  
  
    -   Se as duas matrizes têm referência a elementos de tipo, o tipo de elemento de origem deve derivar do tipo de elemento de destino. Quando esse for o caso, as duas matrizes têm a mesma relação de herança que seus elementos. Isso é chamado de *covariância de matriz*.  
  
 O compilador relatará um erro se as regras acima são violadas, por exemplo, se os tipos de dados não forem compatíveis ou as classificações são diferentes. Você pode adicionar tratamento de erros em seu código para certificar-se de que as matrizes são compatíveis antes de tentar uma atribuição. Você também pode usar o [operador TryCast](../../../../visual-basic/language-reference/operators/trycast-operator.md) palavra-chave se você quiser evitar lançar uma exceção.  
  
## <a name="see-also"></a>Consulte também  
 [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Solucionando problemas de matrizes](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)   
 [Instrução Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Conversões de Matriz](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
