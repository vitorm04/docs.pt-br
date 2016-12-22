---
title: "Como incrementar e diminuir ponteiros (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "expressões de ponteiro [C#], incremento e decremento"
  - "ponteiros [C#], incremento e decremento"
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como incrementar e diminuir ponteiros (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Use o incremento e os operadores de decréscimo, `++` e `--`, para alterar o local do ponteiro por  [sizeof](../../../csharp/language-reference/keywords/sizeof.md) \(`pointer-type`\) para um ponteiro de ponteiro de tipo\-tipo \*.  As expressões increment e decrement tirar da seguinte forma:  
  
```  
++p;  
p++;  
--p;  
p--;  
```  
  
 Os operadores increment e decrement podem ser aplicados a ponteiros de qualquer tipo, exceto o tipo de `void*`.  
  
 O efeito da aplicação do operador de incremento para um ponteiro do tipo `pointer-type` é adicionar  [sizeof](../../../csharp/language-reference/keywords/sizeof.md) \(`pointer-type`\) para o endereço contido na variável de ponteiro.  
  
 O efeito de aplicar o operador de decremento para um ponteiro do tipo `pointer-type` é subtrair `sizeof` \(`pointer-type`\) do endereço contido na variável de ponteiro.  
  
 Não permitir exceções são geradas quando a operação estoura o domínio do ponteiro e o resultado depende da implementação.  
  
## Exemplo  
 Neste exemplo, você percorrer uma matriz, aumentando o ponteiro pelo tamanho do `int`.  Em cada etapa, você pode exibir o endereço e o conteúdo do elemento da matriz.  
  
 [!CODE [csProgGuidePointers#3](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuidePointers#3)]  
  
 [!CODE [csProgGuidePointers#13](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuidePointers#13)]  
  
  **Valor: 0 @ endereço: 12860272**  
**Valor: 1 @ endereço: 12860276**  
**Valor: 2 @ endereço: 12860280**  
**Valor: 3 @ endereço: 12860284**  
**Valor: 4 @ endereço: 12860288**   
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Expressões de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)   
 [Manipulando ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)   
 [Tipos de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [Tipos](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)