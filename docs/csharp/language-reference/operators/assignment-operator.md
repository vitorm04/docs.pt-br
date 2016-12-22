---
title: "Operador = (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador = [C#]"
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador = (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O operador de atribuição \(`=`\) armazena o valor do operando seu direito no local de armazenamento, propriedade ou indexador indicado pelo seu operando esquerdo e retorna o valor como seu resultado.  Os operandos devem ser do mesmo tipo \(ou operando direito deve ser implicitamente conversível para o tipo do operando esquerdo\).  
  
## Comentários  
 O operador de atribuição não pode ser sobrecarregado.  No entanto, você pode definir os operadores de conversão implícita para um tipo, que permitem que você use o operador de atribuição com esses tipos.  Para obter mais informações, consulte [Usando operadores de conversão](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).  
  
## Exemplo  
 [!CODE [csRefOperators#49](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#49)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)