---
title: 'Como: Determinar se dois objetos estão relacionados (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: 62c0280e3773d2e3ff15bc164d9e0e6cacb7bd4d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544582"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>Como: Determinar se dois objetos estão relacionados (Visual Basic)
Você pode comparar dois objetos para determinar a relação, se houver, entre as classes da qual eles são criados. O <xref:System.Type.IsInstanceOfType%2A> método da <xref:System.Type?displayProperty=nameWithType> classe retorna `True` se a classe especificada herda da classe atual, ou se o tipo atual é uma interface compatível com a classe especificada.  
  
### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>Para determinar se um objeto herda da classe ou interface de outro objeto.  
  
1.  No objeto que você acha que podem ser do tipo base, invocar o <xref:System.Object.GetType%2A> método.  
  
2.  Sobre o <xref:System.Type?displayProperty=nameWithType> objeto retornado por <xref:System.Object.GetType%2A>, invocar o <xref:System.Type.IsInstanceOfType%2A> método.  
  
3.  Na lista de argumentos para <xref:System.Type.IsInstanceOfType%2A>, especifique o objeto que você acha que pode ser do tipo derivado.  
  
     <xref:System.Type.IsInstanceOfType%2A> Retorna `True` se seu tipo de argumento herda o <xref:System.Type?displayProperty=nameWithType> tipo de objeto.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir determina se um objeto representa uma classe derivada da classe de outro objeto.  
  
```  
Public Class baseClass  
End Class  
Public Class derivedClass : Inherits baseClass  
End Class  
Public Class testTheseClasses  
    Public Sub seeIfRelated()  
        Dim baseObj As Object = New baseClass()  
        Dim derivedObj As Object = New derivedClass()  
        Dim related As Boolean  
        related = baseObj.GetType().IsInstanceOfType(derivedObj)  
        MsgBox(CStr(related))  
    End Sub  
End Class  
```  
  
 Observe a colocação inesperada das variáveis na chamada para dois objetos <xref:System.Type.IsInstanceOfType%2A>. O tipo base suposto é usado para gerar a <xref:System.Type?displayProperty=nameWithType> classe e o tipo derivado suposto é passada como um argumento para o <xref:System.Type.IsInstanceOfType%2A> método.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [Tipo de Dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Valores de Variável de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Como: Determinar se dois objetos são idênticos](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
