---
title: "value (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "value_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave value [C#]"
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# value (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A palavra\-chave contextual `value` é usado em o acessador set nas declarações de propriedade comum.  Ele é semelhante a um parâmetro de entrada em um método.  A palavra `value` faz referência ao valor que o código do cliente está tentando atribuir à propriedade.  No exemplo a seguir, `MyDerivedClass` tem uma propriedade chamada `Name` que usa a `value` parâmetro para atribuir uma nova seqüência de caracteres para o campo de backup `name`.  Do ponto de vista do código do cliente, a operação é gravada como uma atribuição simple.  
  
 [!code-cs[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/value_1.cs)]  
  
 Para obter mais informações sobre o uso de `value`, consulte [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md).  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)