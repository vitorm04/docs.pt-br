---
title: "Como: criar uma união do C C++ usando atributos (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bcb5291737a9f4763f680daaf625c58d308423f8
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a>Como: criar uma união do C/C++ usando atributos (Visual Basic)
Usando atributos, você pode personalizar como structs são dispostos na memória. Por exemplo, você pode criar o que é conhecido como uma união no C/C++ usando os atributos `StructLayout(LayoutKind.Explicit)` e `FieldOffset`.  
  
## <a name="example"></a>Exemplo  
 Neste segmento de código, todos os campos de `TestUnion` são iniciados no mesmo local na memória.  
  
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
  
## <a name="example"></a>Exemplo  
 A seguir, temos outro exemplo em que os campos são iniciados em locais diferentes definidos explicitamente.  
  
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
  
 Os dois campos inteiros, `i1` e `i2`, compartilham os mesmos locais de memória que `lg`. Esse tipo de controle sobre o layout do struct é útil ao usar a invocação de plataforma.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [Guia de programação do Visual Basic](../../../../visual-basic/programming-guide/index.md)  
 [Atributos](../../../../../docs/standard/attributes/index.md)  
 [Reflexão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [Atributos (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)  
 [Criando atributos personalizados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [Acessando atributos usando reflexão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
