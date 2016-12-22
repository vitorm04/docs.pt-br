---
title: "Operador ~ (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "~_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "~ [C#], Operador de complemento bit a bit"
  - "Operador ~ [C#]"
  - "Operador de complemento bit a bit [C#]"
  - "Operador de complemento de um: til (~) [C#]"
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador ~ (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `~` operador executa uma operação bit a bit complemento no seu operando, que tem o efeito de reverter cada bit.  Operadores bit a bit complemento são predefinidos para  [int](../../../csharp/language-reference/keywords/int.md),  [uint](../../../csharp/language-reference/keywords/uint.md),  [longo](../../../csharp/language-reference/keywords/long.md), e  [ulong](../../../csharp/language-reference/keywords/ulong.md).  
  
> [!NOTE]
>  O `~` símbolo também é usado para declarar os destruidores.  Para obter mais informações, consulte [Destruidores](../../../csharp/programming-guide/classes-and-structs/destructors.md).  
  
## Comentários  
 Tipos definidos pelo usuário podem sobrecarregar o `~` operador.  Para obter mais informações, consulte  [operador](../../../csharp/language-reference/keywords/operator.md).  Geralmente, as operações em tipos integrais são permitidas na enumeração.  
  
## Exemplo  
 [!CODE [csRefOperators#25](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#25)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)   
 [Destruidores](../../../csharp/programming-guide/classes-and-structs/destructors.md)