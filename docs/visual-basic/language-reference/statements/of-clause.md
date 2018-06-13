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
ms.openlocfilehash: 9ace0ad55d9eb1618dbdafb0d49d1ff4b169a877
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603945"
---
# <a name="of-clause-visual-basic"></a>Cláusula Of (Visual Basic)
Apresenta um `Of` cláusula que identifica um *parâmetro de tipo* em uma *genérico* classe, estrutura, interface, delegado ou procedimento. Para obter informações sobre tipos genéricos, consulte [tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).  
  
## <a name="using-the-of-keyword"></a>Usando a palavra-chave Of  
 O seguinte exemplo de código usa o `Of` palavra-chave para definir o contorno de uma classe que usa dois parâmetros de tipo. Ele *restringe* o `keyType` parâmetro pelo <xref:System.IComparable> interface, o que significa que o código deve fornecer um argumento de tipo que implementa <xref:System.IComparable>. Isso é necessário para que o `add` procedimento pode chamar o <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> método. Para obter mais informações sobre restrições, consulte [lista tipo](../../../visual-basic/language-reference/statements/type-list.md).  
  
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
  
 Se você concluir a definição de classe anterior, você pode construir uma variedade de `dictionary` classes dele. Os tipos que você fornece para `entryType` e `keyType` determinar que tipo de entrada a classe contém e o tipo de chave que ela associa a cada entrada. Por causa da restrição, você deve fornecer a `keyType` um tipo que implementa <xref:System.IComparable>.  
  
 O exemplo de código a seguir cria um objeto que contém `String` entradas e associa um `Integer` chave com cada um deles. `Integer` implementa <xref:System.IComparable> e portanto satisfaz a restrição em `keyType`.  
  
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
 <xref:System.IComparable>  
 [Lista de Tipos](../../../visual-basic/language-reference/statements/type-list.md)  
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [Saída](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
