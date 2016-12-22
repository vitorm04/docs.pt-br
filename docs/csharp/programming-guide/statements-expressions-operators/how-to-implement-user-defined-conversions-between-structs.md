---
title: "Como implementar convers&#245;es definidas pelo usu&#225;rio entre structs (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "conversões definidas pelo usuário [C#]"
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como implementar convers&#245;es definidas pelo usu&#225;rio entre structs (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Este exemplo define duas estruturas, `RomanNumeral` e `BinaryNumeral`e demonstra conversões entre eles.  
  
## Exemplo  
 [!code-cs[csProgGuideStatements#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_1.cs)]  
  
## Programação robusta  
  
-   No exemplo anterior, a instrução:  
  
     [!code-cs[csProgGuideStatements#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_2.cs)]  
  
     executa uma conversão de um `RomanNumeral` para um `BinaryNumeral`.  Porque não há nenhuma conversão direta de `RomanNumeral` para `BinaryNumeral`, a projeção é usada para converter de um `RomanNumeral` para um `int`e outra projeção para converter de um `int` para um `BinaryNumeral`.  
  
-   Além disso, a instrução  
  
     [!code-cs[csProgGuideStatements#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_3.cs)]  
  
     executa uma conversão de um `BinaryNumeral` para um `RomanNumeral`.  Porque `RomanNumeral` define uma conversão implícita de `BinaryNumeral`, nenhuma conversão é necessária.  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores de conversão](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)