---
title: "Operador -&gt; (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "->_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador -> [C#]"
  - "Operador de acesso a membro (->) [C#]"
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador -&gt; (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `->` operador combina acesso de membro e de referência do ponteiro.  
  
## Comentários  
 Uma expressão do formulário,  
  
```  
x->y  
```  
  
 \(onde `x` é um ponteiro de tipo `T*` e `y` é um membro do `T`\) é equivalente a,  
  
```  
(*x).y  
```  
  
 O `->` pode ser usado somente no código que está marcado como  [não seguros](../../../csharp/language-reference/keywords/unsafe.md).  
  
 O `->` operador não pode ser sobrecarregado.  
  
## Exemplo  
 [!CODE [csRefOperators#15](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#15)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)