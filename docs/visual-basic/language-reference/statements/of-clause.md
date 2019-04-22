---
title: Cláusula Of (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Of
- vb.Of
- vb.of
helpviewer_keywords:
- Of keyword [Visual Basic]
- arguments [Visual Basic], data types
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
ms.openlocfilehash: 880570c714292b0c11eef4e2cd4c4b410bb075f1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58823435"
---
# <a name="of-clause-visual-basic"></a>Cláusula Of (Visual Basic)
Apresenta uma `Of` cláusula, que identifica uma *parâmetro de tipo* em uma *genérico* classe, estrutura, interface, delegado ou procedimento. Para obter informações sobre tipos genéricos, consulte [tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).  
  
## <a name="using-the-of-keyword"></a>Usando a palavra-chave  
 O seguinte exemplo de código usa o `Of` palavra-chave para definir o contorno de uma classe que usa dois parâmetros de tipo. Ele *restringe* o `keyType` parâmetro com o <xref:System.IComparable> interface, o que significa que o código de consumo deve fornecer um argumento de tipo que implementa <xref:System.IComparable>. Isso é necessário para que o `add` procedimento pode chamar o <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> método. Para obter mais informações sobre restrições, consulte [lista de tipos](../../../visual-basic/language-reference/statements/type-list.md).  
  
```  
Public Class Dictionary(Of entryType, keyType As IComparable)  
    Public Sub add(ByVal e As entryType, ByVal k As keyType)  
        Dim dk As keyType  
        If k.CompareTo(dk) = 0 Then  
        End If  
    End Sub  
    Public Function find(ByVal k As keyType) As entryType  
    End Function  
End Class  
```  
  
 Se você concluir a definição de classe anterior, você pode construir uma variedade de `dictionary` classes dele. Os tipos que você fornece ao `entryType` e `keyType` determinar que tipo de entrada a classe contém e o tipo de chave associa a cada entrada. Por causa da restrição, você deve fornecer a `keyType` um tipo que implementa <xref:System.IComparable>.  
  
 O exemplo de código a seguir cria um objeto que retém `String` entradas e associa um `Integer` chave com cada um deles. `Integer` implementa <xref:System.IComparable> e, portanto, satisfaz a restrição em `keyType`.  
  
```  
Dim d As New dictionary(Of String, Integer)  
```  
  
 O `Of` palavra-chave pode ser usada nesses contextos:  
  
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Consulte também

- <xref:System.IComparable>
- [Lista de Tipos](../../../visual-basic/language-reference/statements/type-list.md)
- [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Saída](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
