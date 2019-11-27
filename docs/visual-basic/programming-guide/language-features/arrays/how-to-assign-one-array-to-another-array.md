---
title: Como atribuir uma matriz a outra matriz
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: be5337e36c2cc7ad9f9b32182b8575ac66bb4a50
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351886"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a>Como atribuir uma matriz a outra matriz (Visual Basic)

Como as matrizes são objetos, você pode usá-las em instruções de atribuição como outros tipos de objeto. Uma variável de matriz contém um ponteiro para os dados que constituem os elementos de matriz e as informações de classificação e comprimento, e uma atribuição copia apenas esse ponteiro.

### <a name="to-assign-one-array-to-another-array"></a>Para atribuir uma matriz a outra matriz

1. Verifique se as duas matrizes têm a mesma classificação (número de dimensões) e tipos de dados de elemento compatíveis.

2. Use uma instrução de atribuição padrão para atribuir a matriz de origem à matriz de destino. Não siga o nome da matriz com parênteses.

    ```vb
    Dim formArray() As System.Windows.Forms.Form
    Dim controlArray() As System.Windows.Forms.Control
    controlArray = formArray
    ```

Quando você atribui uma matriz a outra, as seguintes regras se aplicam:

- **Classificações iguais.** A classificação (número de dimensões) da matriz de destino deve ser a mesma da matriz de origem.

  Desde que as classificações das duas matrizes sejam iguais, as dimensões não precisam ser iguais. O número de elementos em uma determinada dimensão pode ser alterado durante a atribuição.

- **Tipos de elemento.** Ambas as matrizes devem ter elementos de *tipo de referência* ou ambas as matrizes devem ter elementos de *tipo de valor* . Para obter mais informações, consulte [tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).

  - Se ambas as matrizes tiverem elementos de tipo de valor, os tipos de dados de elemento deverão ser exatamente iguais. A única exceção é que você pode atribuir uma matriz de elementos de `Enum` a uma matriz do tipo base do `Enum`.

  - Se ambas as matrizes tiverem elementos de tipo de referência, o tipo de elemento de origem deverá derivar do tipo de elemento de destino. Quando esse for o caso, as duas matrizes terão a mesma relação de herança que seus elementos. Isso é chamado de *covariância de matriz*.

O compilador relatará um erro se as regras acima forem violadas, por exemplo, se os tipos de dados não forem compatíveis ou se as classificações forem desiguais. Você pode adicionar tratamento de erros ao seu código para certificar-se de que as matrizes são compatíveis antes de tentar uma atribuição. Você também pode usar a palavra-chave do [Operador TryCast](../../../../visual-basic/language-reference/operators/trycast-operator.md) se quiser evitar lançar uma exceção.

## <a name="see-also"></a>Consulte também

- [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Solução de problemas de matrizes](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [Instrução Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [Conversões de Matriz](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
