---
title: "Opera&#231;&#245;es aritm&#233;ticas em ponteiros (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "ponteiros [C#], operações aritméticas"
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Opera&#231;&#245;es aritm&#233;ticas em ponteiros (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Este tópico aborda o uso de operadores aritméticos `+` e  **–** para manipular ponteiros.  
  
> [!NOTE]
>  Você não pode executar quaisquer operações aritméticas nos ponteiros void.  
  
## Adição e subtração de valores numéricos para ou de ponteiros  
 You can add a value `n` of type [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), or [ulong](../../../csharp/language-reference/keywords/ulong.md) to a pointer, `p`,of any type except `void*`.  O resultado `p+n` é o ponteiro resultante da adição de `n * sizeof(p) to the address of p`.  Da mesma forma, `p-n` é o ponteiro resultantes da subtração de `n * sizeof(p)` do endereço do `p`.  
  
## A subtração de ponteiros  
 Você também pode subtrair ponteiros do mesmo tipo.  O resultado é sempre do tipo `long`.  Por exemplo, se `p1` e `p2` são ponteiros do tipo `pointer-type*`, em seguida, a expressão `p1-p2` resulta em:  
  
 `((long)p1 - (long)p2)/sizeof(pointer_type)`  
  
 Não permitir exceções são geradas quando a operação aritmética estoura o domínio do ponteiro e o resultado depende da implementação.  
  
## Exemplo  
 [!CODE [csProgGuidePointers#14](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuidePointers#14)]  
  
 [!CODE [csProgGuidePointers#15](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuidePointers#15)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [Expressões de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)   
 [Manipulando ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)   
 [Tipos de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [Tipos](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)