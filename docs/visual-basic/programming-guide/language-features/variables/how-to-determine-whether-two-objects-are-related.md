---
title: 'Como: Determinar se dois objetos estão relacionados (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: 2b17be4ef5a7dabfc4779ab6f5675cc2baec9c3c
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626561"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>Como: Determinar se dois objetos estão relacionados (Visual Basic)

Você pode comparar dois objetos para determinar a relação, se houver, entre as classes das quais elas são criadas. O <xref:System.Type.IsInstanceOfType%2A> método `True` da classe retorna se a classe especificada herda da classe atual ou se o tipo atual é uma interface com suporte da classe especificada. <xref:System.Type?displayProperty=nameWithType>

### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>Para determinar se um objeto herda da classe ou interface de outro objeto

1. No objeto que você acredita que pode ser do tipo base, invoque o <xref:System.Object.GetType%2A> método.

2. No objeto retornado por <xref:System.Object.GetType%2A>, invoque o <xref:System.Type.IsInstanceOfType%2A> método. <xref:System.Type?displayProperty=nameWithType>

3. Na lista de argumentos para <xref:System.Type.IsInstanceOfType%2A>, especifique o objeto que você acredita que pode ser do tipo derivado.

    <xref:System.Type.IsInstanceOfType%2A>retorna `True` se o tipo de argumento herda <xref:System.Type?displayProperty=nameWithType> do tipo de objeto.

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

Observe o posicionamento inesperado das duas variáveis de objeto na chamada <xref:System.Type.IsInstanceOfType%2A>para. O tipo base esperado é usado para gerar a <xref:System.Type?displayProperty=nameWithType> classe e o tipo derivado esperado é passado como um argumento para o <xref:System.Type.IsInstanceOfType%2A> método.

## <a name="see-also"></a>Consulte também

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [Tipo de Dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Valores de Variável de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Como: Determinar se dois objetos são idênticos](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
