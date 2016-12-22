---
title: "Convers&#245;es de ponteiro (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "ponteiros [C#], conversões"
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Convers&#245;es de ponteiro (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A tabela a seguir mostra as conversões de ponteiro implícito predefinidos.  Conversões implícitas podem ocorrer em diversas situações, incluindo chamadas de métodos e instruções de atribuição de valores a variáveis ou propriedades.  
  
## Conversões de ponteiro implícito  
  
|From|Para|  
|----------|----------|  
|Qualquer tipo de ponteiro|void \*|  
|Nulo|Qualquer tipo de ponteiro|  
  
 Conversão explícita de ponteiro é usado para realizar conversões, para o qual não há nenhuma conversão implícita, por meio de uma expressão de conversão.  A tabela a seguir mostra estas conversões.  
  
## Conversões explícitas de ponteiro  
  
|From|Para|  
|----------|----------|  
|Qualquer tipo de ponteiro|Qualquer outro tipo de ponteiro|  
|SByte, byte, short, ushort, int, uint, long ou ulong|Qualquer tipo de ponteiro|  
|Qualquer tipo de ponteiro|SByte, byte, short, ushort, int, uint, long ou ulong|  
  
## Exemplo  
 No exemplo a seguir, um ponteiro para `int` é convertido em um ponteiro para `byte`.  Observe que o ponteiro aponta para o byte da variável addressed menor.  Quando você sucessivamente incrementa o resultado, até o tamanho do `int` \(4 bytes\), você pode exibir os bytes restantes da variável.  
  
 [!CODE [csProgGuidePointers#3](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuidePointers#3)]  
  
 [!CODE [csProgGuidePointers#4](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuidePointers#4)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Expressões de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [Tipos de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [Tipos](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)