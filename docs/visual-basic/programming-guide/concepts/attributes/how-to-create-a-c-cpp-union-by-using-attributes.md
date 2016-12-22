---
title: "Como: criar uma uni&#227;o C C++ usando atributos (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como: criar uma uni&#227;o C/C++ usando atributos (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Usando atributos, você pode personalizar como estruturas são dispostas na memória. Por exemplo, você pode criar o que é conhecido como uma união do C\/C\+\+ usando o `StructLayout(LayoutKind.Explicit)` e `FieldOffset` atributos.  
  
## Exemplo  
 Nesse segmento de código, todos os campos de `TestUnion` Iniciar no mesmo local na memória.  
  
```vb  
' Add an Imports statement for System.Runtime.InteropServices.  
  
<System.Runtime.InteropServices.StructLayout(   
      System.Runtime.InteropServices.LayoutKind.Explicit)>   
Structure TestUnion  
    <System.Runtime.InteropServices.FieldOffset(0)>   
    Public i As Integer  
  
    <System.Runtime.InteropServices.FieldOffset(0)>   
    Public d As Double  
  
    <System.Runtime.InteropServices.FieldOffset(0)>   
    Public c As Char  
  
    <System.Runtime.InteropServices.FieldOffset(0)>   
    Public b As Byte  
End Structure  
```  
  
## Exemplo  
 Este é outro exemplo onde o início de campos em diferentes explicitamente definir locais.  
  
```vb  
' Add an Imports statement for System.Runtime.InteropServices.  
  
 <System.Runtime.InteropServices.StructLayout(   
      System.Runtime.InteropServices.LayoutKind.Explicit)>   
Structure TestExplicit  
     <System.Runtime.InteropServices.FieldOffset(0)>   
     Public lg As Long  
  
     <System.Runtime.InteropServices.FieldOffset(0)>   
     Public i1 As Integer  
  
     <System.Runtime.InteropServices.FieldOffset(4)>   
     Public i2 As Integer  
  
     <System.Runtime.InteropServices.FieldOffset(8)>   
     Public d As Double  
  
     <System.Runtime.InteropServices.FieldOffset(12)>   
     Public c As Char  
  
     <System.Runtime.InteropServices.FieldOffset(14)>   
     Public b As Byte  
 End Structure  
```  
  
 Os campos de dois inteiros, `i1` e `i2`, compartilham os mesmos locais de memória `lg`. Esse tipo de controle sobre o layout de struct é útil ao usar invocação de plataforma.  
  
## Consulte também  
 <xref:System.Reflection>   
 <xref:System.Attribute>   
 [Guia de programação do Visual Basic](../../../../visual-basic/programming-guide/index.md)   
 [Atributos](../Topic/Extending%20Metadata%20Using%20Attributes.md)   
 [Reflexão \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/reflection.md)   
 [Atributos](../../../../visual-basic/language-reference/attributes.md)   
 [Criando atributos personalizados \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)   
 [Acessando atributos usando reflexão \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)