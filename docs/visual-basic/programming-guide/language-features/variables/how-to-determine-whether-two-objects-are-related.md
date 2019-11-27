---
title: Como determinar se dois objetos estão relacionados
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: b3f5fc017166ba9cf28359db5de850c81b73bd69
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348624"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>Como determinar se dois objetos estão relacionados (Visual Basic)

Você pode comparar dois objetos para determinar a relação, se houver, entre as classes das quais elas são criadas. O método <xref:System.Type.IsInstanceOfType%2A> da classe <xref:System.Type?displayProperty=nameWithType> retorna `True` se a classe especificada herda da classe atual ou se o tipo atual é uma interface com suporte da classe especificada.

### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>Para determinar se um objeto herda da classe ou interface de outro objeto

1. No objeto que você acredita que pode ser do tipo base, invoque o método <xref:System.Object.GetType%2A>.

2. No objeto <xref:System.Type?displayProperty=nameWithType> retornado por <xref:System.Object.GetType%2A>, invoque o método <xref:System.Type.IsInstanceOfType%2A>.

3. Na lista de argumentos para <xref:System.Type.IsInstanceOfType%2A>, especifique o objeto que você acredita que pode ser do tipo derivado.

    <xref:System.Type.IsInstanceOfType%2A> retornará `True` se o tipo de argumento herdar do tipo de objeto <xref:System.Type?displayProperty=nameWithType>.

## <a name="example"></a>Exemplo
 O exemplo a seguir determina se um objeto representa uma classe derivada da classe de outro objeto.

```vb
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

Observe o posicionamento inesperado das duas variáveis de objeto na chamada para <xref:System.Type.IsInstanceOfType%2A>. O tipo base esperado é usado para gerar a classe <xref:System.Type?displayProperty=nameWithType> e o tipo derivado esperado é passado como um argumento para o método <xref:System.Type.IsInstanceOfType%2A>.

## <a name="see-also"></a>Consulte também

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [Tipo de Dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Valores de Variável de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Como determinar se dois objetos são idênticos](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
