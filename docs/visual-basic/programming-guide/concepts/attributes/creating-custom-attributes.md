---
title: Criando atributos personalizados (Visual Basic) | Documentos do Microsoft
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
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1aa97a591fdbdfab931a8b5e4f70ec3c00762332
ms.lasthandoff: 03/13/2017

---
# <a name="creating-custom-attributes-visual-basic"></a>Criando atributos personalizados (Visual Basic)
Você pode criar seus próprios atributos personalizados, definindo uma classe de atributo, uma classe que deriva diretamente ou indiretamente de <xref:System.Attribute>, que faz com que identifica as definições de atributo nos metadados rápida e fácil.</xref:System.Attribute> Suponha que você queira para tipos de marca com o nome do programador que escreveu o tipo. Você pode definir um personalizado `Author` classe de atributo:  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct)>   
Public Class Author  
    Inherits System.Attribute  
    Private name As String  
    Public version As Double  
    Sub New(ByVal authorName As String)  
        name = authorName  
        version = 1.0  
    End Sub  
End Class  
```  
  
 O nome da classe é o nome do atributo, `Author`. Ela é derivada de `System.Attribute`, portanto, é uma classe de atributo personalizado. Parâmetros do construtor são parâmetros posicionais do atributo personalizado. Neste exemplo, `name` é um parâmetro posicional. Quaisquer propriedades ou campos públicos de leitura / gravação são parâmetros nomeadas. Nesse caso, `version` é o único parâmetro nomeado. Observe o uso do `AttributeUsage` atributo para tornar o `Author` válido apenas na classe de atributo e `Structure` declarações.  
  
 Você pode usar esse novo atributo da seguinte maneira:  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 `AttributeUsage`tem um parâmetro nomeado, `AllowMultiple`, com o qual você pode fazer um atributo personalizado multiuse ou de uso único. No exemplo de código a seguir, um atributo multiuse é criado.  
  
```vb  
' multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
```  
  
 No exemplo de código a seguir, vários atributos do mesmo tipo são aplicados a uma classe.  
  
```vb  
<Author("P. Ackerman", Version:=1.1),   
Author("R. Koch", Version:=1.2)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
    ' R. Koch's code goes here...  
End Class  
```  
  
> [!NOTE]
>  Se sua classe de atributo contém uma propriedade, essa propriedade deve ser leitura / gravação.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Reflection></xref:System.Reflection>   
 [Guia de programação em Visual Basic](../../../../visual-basic/programming-guide/index.md)   
 [Escrevendo atributos personalizados](http://msdn.microsoft.com/library/97216f69-bde8-49fd-ac40-f18c500ef5dc)   
 [Reflexão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)   
 [Atributos (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)   
 [Acessando atributos usando reflexão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)   
 [AttributeUsage (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
