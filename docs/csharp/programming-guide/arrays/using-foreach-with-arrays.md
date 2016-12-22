---
title: "Usando foreach com matrizes (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "matrizes [C#], foreach"
  - "instrução foreach [C#], usando com matrizes"
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Usando foreach com matrizes (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O C\# também oferece a instrução [foreach](../../../csharp/language-reference/keywords/foreach-in.md).  Essa instrução fornece uma maneira simples e limpa de iterar através dos elementos de uma matriz ou qualquer coleção enumerável.  A instrução `foreach` processa os elementos na ordem retornada pela matriz ou enumerador do tipo de coleção que normalmente vai do elemento 0 ao último.  Por exemplo, o código a seguir cria uma matriz chamada `numbers` e itera por ela com a instrução `foreach`:  
  
 [!code-cs[csProgGuideArrays#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_1.cs)]  
  
 Com matrizes multidimensionais, você pode usar o mesmo método para iterar pelos elementos, por exemplo:  
  
 [!code-cs[csProgGuideArrays#29](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_2.cs)]  
  
 No entanto, com matrizes multidimensionais, usar um loop aninhado [for](../../../csharp/language-reference/keywords/for.md) oferece mais controle sobre os elementos da matriz.  
  
## Consulte também  
 <xref:System.Array>   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Matrizes](../../../csharp/programming-guide/arrays/index.md)   
 [Matrizes unidimensionais](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)   
 [Matrizes multidimensionais](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)   
 [Matrizes denteadas](../../../csharp/programming-guide/arrays/jagged-arrays.md)