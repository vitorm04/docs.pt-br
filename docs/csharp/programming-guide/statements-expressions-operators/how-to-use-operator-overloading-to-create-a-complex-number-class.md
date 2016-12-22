---
title: "Como usar sobrecarga de operador para criar uma classe de n&#250;mero complexo (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "classes [C#], sobrecarga de operador"
  - "números complexos [C#]"
  - "sobrecarga de Operador [C#], números complexos"
  - "sobrecarga de Operador [C#], usando para criar classes"
  - "operadores [C#], sobrecarregando para criar uma classe de números complexos"
ms.assetid: c9b8d982-5112-413f-bae3-b42ae3248ddf
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como usar sobrecarga de operador para criar uma classe de n&#250;mero complexo (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Este exemplo mostra como você pode usar a sobrecarga de operador para criar uma classe para números complexos `Complex` que define adição de complexos.  O programa exibe o imaginários e as partes reais de números e a adição resultam usando uma substituição da `ToString` método.  
  
## Exemplo  
 [!code-cs[csProgGuideStatements#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-operator-overloading-to-create-a-complex-number-class_1.cs)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)   
 [operator](../../../csharp/language-reference/keywords/operator.md)   
 [Por que são operadores sobrecarregados sempre estáticos em C\#?](http://go.microsoft.com/fwlink/?LinkId=112383)