---
title: "Executando a convers&#227;o boxing de tipos anul&#225;veis (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "boxing [C#], tipos anuláveis"
  - "tipos anuláveis [C#], boxing e unboxing"
  - "unboxing [C#], tipos anuláveis"
ms.assetid: bdb5b626-abc0-405d-8f64-0f0a0bf883a4
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Executando a convers&#227;o boxing de tipos anul&#225;veis (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Objetos com base em tipos anuláveis são in a box somente se o objeto não for nulo.  Se <xref:System.Nullable%601.HasValue%2A> é `false`, a referência de objeto é atribuída a `null` em vez de boxe.  Por exemplo:  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Se o objeto não for nulo – se <xref:System.Nullable%601.HasValue%2A> é `true` – então boxing ocorre, mas somente o tipo subjacente que o objeto anulável se baseia for in a box.  Boxing um tipo de valor nulo de não\-nulos caixas o tipo de valor em si, não o <xref:System.Nullable%601?displayProperty=fullName> que envolve o tipo de valor.  Por exemplo:  
  
```  
bool? b = false;  
int? i = 44;  
object bBoxed = b; // bBoxed contains a boxed bool.  
object iBoxed = i; // iBoxed contains a boxed int.  
```  
  
 Os dois objetos in a box são idênticos aos criados por tipos de conversão boxing não anuláveis.  E, assim como os tipos de processador in a box não anuláveis, eles podem ser desemoldurados para tipos anuláveis, como no exemplo a seguir:  
  
```  
bool? b2 = (bool?)bBoxed;  
int? i2 = (int?)iBoxed;  
```  
  
## Comentários  
 O comportamento dos tipos anuláveis quando o processador in a box oferece duas vantagens:  
  
1.  Objetos anuláveis e sua contraparte in a box podem ser testados para null:  
  
    ```  
    bool? b = null;  
    object boxedB = b;  
    if (b == null)  
    {  
      // True.  
    }  
    if (boxedB == null)  
    {  
      // Also true.  
    }  
    ```  
  
2.  Processador in a box tipos anuláveis totalmente suportam a funcionalidade do tipo subjacente:  
  
    ```  
    double? d = 44.4;  
    object iBoxed = d;  
    // Access IConvertible interface implemented by double.  
    IConvertible ic = (IConvertible)iBoxed;  
    int i = ic.ToInt32(null);  
    string str = ic.ToString();  
    ```  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Tipos anuláveis](../../../csharp/programming-guide/nullable-types/index.md)   
 [Como identificar um tipo anulável](../../../csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type.md)