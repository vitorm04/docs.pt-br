---
title: "Como acessar um membro com um ponteiro (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "ponteiros [C#], acesso de membro"
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como acessar um membro com um ponteiro (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Para acessar um membro de uma estrutura que é declarado em um contexto sem segurança, você pode usar o operador de acesso de membro como mostrado no exemplo a seguir, na qual `p` é um ponteiro para uma  [struct](../../../csharp/language-reference/keywords/struct.md) que contém um membro `x`.  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## Exemplo  
 Neste exemplo, um  [struct](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, que contém duas coordenadas `x` e `y` é declarada e instanciada.  Usando o operador de acesso de membro `->` e um ponteiro para a instância `home`, `x` e `y` são valores atribuídos.  
  
> [!NOTE]
>  Observe que a expressão `p->x` é equivalente à expressão `(*p).x`, e você pode obter o mesmo resultado usando uma das duas expressões.  
  
 [!CODE [csProgGuidePointers#9](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuidePointers#9)]  
  
 [!CODE [csProgGuidePointers#10](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuidePointers#10)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Expressões de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [Tipos de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [Tipos](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)