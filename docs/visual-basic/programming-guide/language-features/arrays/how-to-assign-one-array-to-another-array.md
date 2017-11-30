---
title: Como atribuir uma matriz a outra matriz (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0dd2d678bbfdeaa6b12b5b5a4f69d0fbca8c1944
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a>Como atribuir uma matriz a outra matriz (Visual Basic)
Como matrizes são objetos, você pode usá-los em instruções de atribuição como outros tipos de objeto. Uma variável de matriz contém um ponteiro para os dados que constituem os elementos da matriz e as informações de classificação e comprimento, e uma atribuição copia somente esse ponteiro.  
  
### <a name="to-assign-one-array-to-another-array"></a>Para atribuir uma matriz a outra matriz  
  
1.  Certifique-se de que as duas matrizes têm a mesma classificação (número de dimensões) e tipos de dados de elemento compatíveis.  
  
2.  Use uma instrução de atribuição padrão para atribuir a matriz de origem para a matriz de destino. Não execute o nome da matriz com parênteses.  
  
    ```  
    Dim formArray() As System.Windows.Forms.Form  
    Dim controlArray() As System.Windows.Forms.Control  
    controlArray = formArray  
    ```  
  
 Quando você atribui uma matriz para outro, as seguintes regras se aplicam:  
  
-   **Ordens iguais.** A classificação (número de dimensões) da matriz de destino deve ser a mesma que a matriz de origem.  
  
     Desde que as classificações de duas matrizes forem iguais, as dimensões não precisam ser iguais. O número de elementos em uma determinada dimensão pode mudar durante a atribuição.  
  
-   **Tipos de elemento.** Ou ambas as matrizes devem ter *fazem referência a tipo* elementos ou ambas as matrizes devem ter *tipo de valor* elementos. Para obter mais informações, consulte [tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
    -   Se as duas matrizes têm elementos de tipo de valor, os tipos de dados do elemento devem ser exatamente os mesmos. A única exceção a isso é que você pode atribuir uma matriz de `Enum` elementos em uma matriz do tipo base do que `Enum`.  
  
    -   Se as duas matrizes têm referência a elementos de tipo, o tipo de elemento de origem deve derivar do tipo de elemento de destino. Quando esse for o caso, as duas matrizes têm a mesma relação de herança que seus elementos. Isso é chamado de *covariância*.  
  
 O compilador relata um erro se as regras acima forem violadas, por exemplo, se os tipos de dados não são compatíveis ou as classificações são diferentes. Você pode adicionar ao seu código para certificar-se de que as matrizes são compatíveis antes de tentar uma atribuição de tratamento de erros. Você também pode usar o [operador TryCast](../../../../visual-basic/language-reference/operators/trycast-operator.md) palavra-chave se você quiser evitar lançar uma exceção.  
  
## <a name="see-also"></a>Consulte também  
 [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Solução de problemas de matrizes](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [Instrução Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Conversões de Matriz](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
