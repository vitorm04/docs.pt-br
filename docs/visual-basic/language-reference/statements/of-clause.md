---
title: "Cláusula of (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- Of
- vb.Of
- vb.of
dev_langs:
- VB
helpviewer_keywords:
- Of keyword
- arguments [Visual Basic], data types
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- parameters, type
- types [Visual Basic], generic
- parameters, generic
- type parameters
- data type arguments
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
caps.latest.revision: 17
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
ms.openlocfilehash: 920b13514566e496adf45fb3db9f08145c5ab4c8
ms.lasthandoff: 03/13/2017

---
# <a name="of-clause-visual-basic"></a>Cláusula Of (Visual Basic)
Apresenta um `Of` cláusula que identifica uma *parâmetro de tipo* em uma *genérico* classe, estrutura, interface, representante ou procedimento. Para obter informações sobre tipos genéricos, consulte [tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).  
  
## <a name="using-the-of-keyword"></a>Usando a palavra-chave Of  
 O seguinte exemplo de código usa o `Of` palavra-chave para definir o contorno de uma classe que leva dois parâmetros de tipo. Ele *restringe* o `keyType` parâmetro pela <xref:System.IComparable>interface, que significa que o código consumido deve fornecer um argumento de tipo que implementa <xref:System.IComparable>.</xref:System.IComparable> </xref:System.IComparable> Isso é necessário para que o `add` procedimento pode chamar o <xref:System.IComparable.CompareTo%2A?displayProperty=fullName>método.</xref:System.IComparable.CompareTo%2A?displayProperty=fullName> Para obter mais informações sobre restrições, consulte [tipo lista](../../../visual-basic/language-reference/statements/type-list.md).  
  
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
  
 Se você concluir a definição de classe anterior, você pode construir uma variedade de `dictionary` classes dela. Os tipos que você fornece para `entryType` e `keyType` determinam que tipo de entrada a classe contém e o tipo de chave que ela associa a cada entrada. Por causa da restrição, você deve fornecer a `keyType` um tipo que implementa <xref:System.IComparable>.</xref:System.IComparable>  
  
 O exemplo de código a seguir cria um objeto que contém `String` entradas e associa um `Integer` chave com cada um deles. `Integer`implementa <xref:System.IComparable>e portanto satisfaz a restrição em `keyType`.</xref:System.IComparable>  
  
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
 <xref:System.IComparable></xref:System.IComparable>   
 [Lista de tipos](../../../visual-basic/language-reference/statements/type-list.md)   
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Em](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)   
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
