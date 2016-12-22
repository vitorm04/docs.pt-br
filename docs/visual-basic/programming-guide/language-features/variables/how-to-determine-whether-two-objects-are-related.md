---
title: "Como determinar se dois objetos est&#227;o relacionados (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "herança, objetos do Visual Basic"
  - "variáveis de objeto, determinando a relação"
  - "objetos [Visual Basic], herança"
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como determinar se dois objetos est&#227;o relacionados (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode comparar dois objetos para determinar a relação, se houver, entre as classes a partir do qual eles são criados.  O <xref:System.Type.IsInstanceOfType%2A> método da <xref:System.Type?displayProperty=fullName> classe retorna `True` se a classe especificada herda da classe atual, ou se o tipo atual é uma interface com o apoio da classe especificada.  
  
### Para determinar se um objeto herda da classe ou interface de outro objeto.  
  
1.  No objeto que você acha que pode ser do tipo base, chamar o <xref:System.Object.GetType%2A> método.  
  
2.  Sobre o <xref:System.Type?displayProperty=fullName> objeto retornado por <xref:System.Object.GetType%2A>, invocar o <xref:System.Type.IsInstanceOfType%2A> método.  
  
3.  Na lista de argumentos para <xref:System.Type.IsInstanceOfType%2A>, especifique o objeto que você acha que pode ser do tipo derivado.  
  
     <xref:System.Type.IsInstanceOfType%2A>Retorna `True` se o seu tipo de argumento herda o <xref:System.Type?displayProperty=fullName> tipo de objeto.  
  
## Exemplo  
 O exemplo a seguir determina se um objeto representa uma classe derivada da classe do objeto.  
  
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
  
 Observe a colocação inesperada das variáveis duas objeto na chamada para <xref:System.Type.IsInstanceOfType%2A>.  O tipo base suposto é usado para gerar o <xref:System.Type?displayProperty=fullName> classe e o tipo derivado suposto é passado como um argumento para o <xref:System.Type.IsInstanceOfType%2A> método.  
  
## Consulte também  
 <xref:System.Object.GetType%2A>   
 <xref:System.Type?displayProperty=fullName>   
 <xref:System.Type.IsInstanceOfType%2A>   
 [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Valores de variável de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [Como determinar se dois objetos são idênticos](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)