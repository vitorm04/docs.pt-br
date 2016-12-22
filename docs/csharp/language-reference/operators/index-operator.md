---
title: "Operador(Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "[]_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador [] [C#]"
  - "Operador indexing [C#]"
  - "Operador square brackets [ ] [C#]"
  - "Operador subscript [C#]"
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador(Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Colchetes \(`[]`\) são usados para arrays, os indexadores e atributos.  Eles também podem ser usados como ponteiros.  
  
## Comentários  
 Um tipo de matriz é um tipo de seguido por `[]`:  
  
 [!CODE [csRefOperators#43](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#43)]  
  
 Para acessar um elemento de um array, o índice do elemento desejado é delimitado por colchetes:  
  
 [!CODE [csRefOperators#44](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#44)]  
  
 Uma exceção é gerada se um índice do array estiver fora do intervalo.  
  
 O operador de indexação do array não pode ser sobrecarregado; no entanto, podem definir tipos indexadores, e propriedades que peguem um ou mais parâmetros.  Parâmetros do indexador são colocados entre colchetes, assim como os índices da matriz, mas os parâmetros de indexador podem ser declarados para ser de qualquer tipo, ao contrário dos índices da matriz, que deve ser integrante.  
  
 Por exemplo, o.NET Framework define uma `Hashtable` que associa as chaves e valores do tipo arbitrário tipo:  
  
 [!CODE [csRefOperators#45](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#45)]  
  
 Colchetes também são usados para especificar [Atributos](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md):  
  
 [!CODE [csRefOperators#46](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#46)]  
  
 Você pode usar colchetes para indexar um ponteiro:  
  
 [!CODE [csRefOperators#47](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#47)]  
  
 Nenhuma verificação será executada.  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)   
 [Matrizes](../../../csharp/programming-guide/arrays/index.md)   
 [Indexadores](../../../csharp/programming-guide/indexers/index.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)