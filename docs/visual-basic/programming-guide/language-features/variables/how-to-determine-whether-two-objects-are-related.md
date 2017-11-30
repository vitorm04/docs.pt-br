---
title: "Como determinar se dois objetos estão relacionados (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7824742459fca355c0043ad8ed20a26330402c05
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>Como determinar se dois objetos estão relacionados (Visual Basic)
Você pode comparar dois objetos para determinar a relação, se houver, entre as classes do qual eles são criados. O <xref:System.Type.IsInstanceOfType%2A> método o <xref:System.Type?displayProperty=nameWithType> classe retorna `True` se a classe especificada herda da classe atual, ou se o tipo atual é uma interface com suporte a classe especificada.  
  
### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>Para determinar se um objeto herda da classe ou interface de outro objeto.  
  
1.  No objeto que você acha que pode ser do tipo base, invoque o <xref:System.Object.GetType%2A> método.  
  
2.  Sobre o <xref:System.Type?displayProperty=nameWithType> objeto retornado por <xref:System.Object.GetType%2A>, invocar o <xref:System.Type.IsInstanceOfType%2A> método.  
  
3.  Na lista de argumentos para <xref:System.Type.IsInstanceOfType%2A>, especifique o objeto que você acha que pode ser do tipo derivado.  
  
     <xref:System.Type.IsInstanceOfType%2A>Retorna `True` se seu tipo de argumento herda o <xref:System.Type?displayProperty=nameWithType> tipo de objeto.  
  
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
  
 Observe o posicionamento inesperado de variáveis de dois objeto na chamada para <xref:System.Type.IsInstanceOfType%2A>. O tipo base suposto é usado para gerar o <xref:System.Type?displayProperty=nameWithType> classe e o tipo derivado suposto é passado como um argumento para o <xref:System.Type.IsInstanceOfType%2A> método.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Object.GetType%2A>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Type.IsInstanceOfType%2A>  
 [Tipo de Dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Valores de Variável de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Como determinar se dois objetos são idênticos](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
