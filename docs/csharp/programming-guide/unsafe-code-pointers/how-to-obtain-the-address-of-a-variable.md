---
title: "Como obter o endere&#231;o de uma vari&#225;vel (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "expressões de ponteiro [C#], Operador address-of"
  - "ponteiros [C#], Operador &"
  - "variáveis [C#], address of"
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como obter o endere&#231;o de uma vari&#225;vel (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Para obter o endereço de um unário expressão, que é avaliada como uma variável fixa, use o operador adress\-of:  
  
```  
int number;  
int* p = &number; //address-of operator &  
```  
  
 O operador adress\-of só pode ser aplicado a uma variável.  Se a variável for uma variável moveable, você pode usar o  [fixo instrução](../../../csharp/language-reference/keywords/fixed-statement.md) para corrigir temporariamente a variável antes de obter seu endereço.  
  
 É sua responsabilidade assegurar que a variável é inicializada.  O compilador não emitirá uma mensagem de erro se a variável não for inicializada.  
  
 Você não pode obter o endereço de uma constante ou um valor.  
  
## Exemplo  
 Neste exemplo, um ponteiro para `int`, `p`, é declarada e atribuída ao endereço de uma variável de inteiro, `number`.  A variável `number` é inicializado como resultado de uma atribuição para \* p.  Se você tornar esta instrução de atribuição um comentário, a inicialização da variável `number` será removido, mas nenhum erro de tempo de compilação é emitido.  Observe o uso da  [Acesso de membro](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md) operador `->` para obter e exibir o endereço armazenado no ponteiro.  
  
 [!CODE [csProgGuidePointers#7](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuidePointers#7)]  
  
 [!CODE [csProgGuidePointers#8](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuidePointers#8)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Expressões de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [Tipos de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [Tipos](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)