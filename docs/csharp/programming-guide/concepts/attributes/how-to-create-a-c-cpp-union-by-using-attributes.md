---
title: "Como: criar uma uni&#227;o C C++ usando atributos (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como: criar uma uni&#227;o C/C++ usando atributos (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Usando atributos, você pode personalizar como estruturas são dispostas na memória. Por exemplo, você pode criar o que é conhecido como uma união do C\/C\+\+ usando o `StructLayout(LayoutKind.Explicit)` e `FieldOffset` atributos.  
  
## Exemplo  
 Nesse segmento de código, todos os campos de `TestUnion` Iniciar no mesmo local na memória.  
  
```c#  
// Add a using directive for System.Runtime.InteropServices.  
  
       [System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]  
       struct TestUnion  
       {  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public int i;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public double d;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public char c;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public byte b;  
       }  
```  
  
## Exemplo  
 Este é outro exemplo onde o início de campos em diferentes explicitamente definir locais.  
  
```c#  
// Add a using directive for System.Runtime.InteropServices.  
  
       [System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]  
       struct TestExplicit  
       {  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public long lg;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public int i1;  
  
           [System.Runtime.InteropServices.FieldOffset(4)]  
           public int i2;  
  
           [System.Runtime.InteropServices.FieldOffset(8)]  
           public double d;  
  
           [System.Runtime.InteropServices.FieldOffset(12)]  
           public char c;  
  
           [System.Runtime.InteropServices.FieldOffset(14)]  
           public byte b;  
       }  
```  
  
 Os campos de dois inteiros, `i1` e `i2`, compartilham os mesmos locais de memória `lg`. Esse tipo de controle sobre o layout de struct é útil ao usar invocação de plataforma.  
  
## Consulte também  
 <xref:System.Reflection>   
 <xref:System.Attribute>   
 [Guia de Programação em C\#](../../../../csharp/programming-guide/index.md)   
 [Atributos](../Topic/Extending%20Metadata%20Using%20Attributes.md)   
 [Reflexão \(c\#\)](../../../../csharp/programming-guide/concepts/reflection.md)   
 [Atributos \(c\#\)](../../../../csharp/programming-guide/concepts/attributes/index.md)   
 [Criando atributos personalizados \(c\#\)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)   
 [Acessando atributos usando reflexão \(c\#\)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)