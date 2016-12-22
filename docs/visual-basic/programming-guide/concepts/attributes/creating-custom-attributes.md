---
title: "Criando atributos personalizados (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Criando atributos personalizados (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode criar seus próprios atributos personalizados, definindo uma classe de atributo, uma classe que deriva diretamente ou indiretamente de <xref:System.Attribute>, que faz com que identifica as definições de atributo nos metadados rápida e fácil. Suponha que você queira para tipos de marca com o nome do programador que escreveu o tipo. Você pode definir um personalizado `Author` classe de atributo:  
  
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
  
 O nome da classe é o nome do atributo, `Author`. Ela é derivada de `System.Attribute`, portanto, é uma classe de atributo personalizado. Parâmetros do construtor são parâmetros posicionais do atributo personalizado. Neste exemplo, `name` é um parâmetro posicional. Quaisquer propriedades ou campos públicos de leitura \/ gravação são parâmetros nomeadas. Nesse caso, `version` é o único parâmetro nomeado. Observe o uso do `AttributeUsage` atributo para tornar o `Author` válido apenas na classe de atributo e `Structure` declarações.  
  
 Você pode usar esse novo atributo da seguinte maneira:  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 `AttributeUsage` tem um parâmetro nomeado, `AllowMultiple`, com o qual você pode fazer um atributo personalizado multiuse ou de uso único. No exemplo de código a seguir, um atributo multiuse é criado.  
  
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
>  Se sua classe de atributo contém uma propriedade, essa propriedade deve ser leitura \/ gravação.  
  
## Consulte também  
 <xref:System.Reflection>   
 [Guia de programação do Visual Basic](../../../../visual-basic/programming-guide/index.md)   
 [Escrevendo atributos personalizados](../Topic/Writing%20Custom%20Attributes.md)   
 [Reflexão \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/reflection.md)   
 [Atributos](../../../../visual-basic/language-reference/attributes.md)   
 [Acessando atributos usando reflexão \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)   
 [AttributeUsage \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)