---
title: "Como: determinar se dois objetos estão relacionados (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- inheritance, Visual Basic objects
- objects [Visual Basic], inheritance
- object variables, determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
caps.latest.revision: 7
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
ms.openlocfilehash: b4055edbf2293017c6586b337437db797f7eb525
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>Como determinar se dois objetos estão relacionados (Visual Basic)
Você pode comparar dois objetos para determinar a relação, se houver, entre as classes no qual eles são criados. O <xref:System.Type.IsInstanceOfType%2A>método o <xref:System.Type?displayProperty=fullName>classe retorna `True` se a classe especificada herda da classe atual, ou se o tipo atual é uma interface com suporte a classe especificada.</xref:System.Type?displayProperty=fullName> </xref:System.Type.IsInstanceOfType%2A>  
  
### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>Para determinar se um objeto herda da classe ou interface de outro objeto  
  
1.  No objeto que você acha que podem ser do tipo base, chamar o <xref:System.Object.GetType%2A>método.</xref:System.Object.GetType%2A>  
  
2.  Sobre o <xref:System.Type?displayProperty=fullName>objeto retornado por <xref:System.Object.GetType%2A>, chamar o <xref:System.Type.IsInstanceOfType%2A>método.</xref:System.Type.IsInstanceOfType%2A> </xref:System.Object.GetType%2A> </xref:System.Type?displayProperty=fullName>  
  
3.  Na lista de argumentos para <xref:System.Type.IsInstanceOfType%2A>, especifique o objeto que você acha que pode ser do tipo derivado.</xref:System.Type.IsInstanceOfType%2A>  
  
     <xref:System.Type.IsInstanceOfType%2A>Retorna `True` se seu tipo de argumento herda o <xref:System.Type?displayProperty=fullName>tipo de objeto.</xref:System.Type?displayProperty=fullName></xref:System.Type.IsInstanceOfType%2A>  
  
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
  
 Observe a colocação inesperada de variáveis de dois objeto na chamada para <xref:System.Type.IsInstanceOfType%2A>.</xref:System.Type.IsInstanceOfType%2A> O tipo base suposto é usado para gerar o <xref:System.Type?displayProperty=fullName>classe e o tipo derivado suposto é passado como um argumento para o <xref:System.Type.IsInstanceOfType%2A>método.</xref:System.Type.IsInstanceOfType%2A> </xref:System.Type?displayProperty=fullName>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Object.GetType%2A></xref:System.Object.GetType%2A>   
 <xref:System.Type?displayProperty=fullName></xref:System.Type?displayProperty=fullName>   
 <xref:System.Type.IsInstanceOfType%2A></xref:System.Type.IsInstanceOfType%2A>   
 [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Valores de variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [Como determinar se dois objetos são idênticos](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
