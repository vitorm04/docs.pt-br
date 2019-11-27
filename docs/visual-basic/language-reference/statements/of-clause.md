---
title: Cláusula Of
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
ms.openlocfilehash: d88c43efe858d6b81b7d8d2470b234ff5d40632a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353840"
---
# <a name="of-clause-visual-basic"></a>Cláusula Of (Visual Basic)
Apresenta uma cláusula `Of`, que identifica um *parâmetro de tipo* em uma classe *genérica* , estrutura, interface, delegado ou procedimento. Para obter informações sobre tipos genéricos, consulte [tipos genéricos em Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).  
  
## <a name="using-the-of-keyword"></a>Usando a palavra-chave of  
 O exemplo de código a seguir usa a palavra-chave `Of` para definir o contorno de uma classe que usa dois parâmetros de tipo. Ele *restringe* o parâmetro `keyType` pela interface <xref:System.IComparable>, o que significa que o código de consumo deve fornecer um argumento de tipo que implemente <xref:System.IComparable>. Isso é necessário para que o procedimento de `add` possa chamar o método <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType>. Para obter mais informações sobre restrições, consulte [lista de tipos](../../../visual-basic/language-reference/statements/type-list.md).  
  
```vb  
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
  
 Se você concluir a definição de classe anterior, poderá construir uma variedade de classes de `dictionary` a partir dela. Os tipos fornecidos para `entryType` e `keyType` determinam que tipo de entrada a classe contém e que tipo de chave ela associa a cada entrada. Devido à restrição, você deve fornecer a `keyType` um tipo que implementa <xref:System.IComparable>.  
  
 O exemplo de código a seguir cria um objeto que contém `String` entradas e associa uma chave de `Integer` a cada uma. `Integer` implementa <xref:System.IComparable> e, portanto, satisfaz a restrição em `keyType`.  
  
```vb  
Dim d As New dictionary(Of String, Integer)  
```  
  
 A palavra-chave `Of` pode ser usada nesses contextos:  
  
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
