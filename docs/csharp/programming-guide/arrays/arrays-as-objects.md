---
title: "Matrizes como objetos (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "matrizes [C#], como objetos"
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Matrizes como objetos (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

No C\#, matrizes são, na verdade, objetos e não apenas endereçáveis regiões de memória contígua, como em c e C\+\+.  <xref:System.Array>é o tipo base abstrato de todos os tipos de matriz.  Você pode usar as propriedades e outros membros da classe, que <xref:System.Array> tem.  Um exemplo disso estariam usando o <xref:System.Array.Length%2A> propriedade para obter o comprimento de uma matriz.  O código a seguir atribui o comprimento da `numbers` matriz, `5`, a uma variável chamada `lengthOfNumbers`:  
  
 [!code-cs[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]  
  
 O <xref:System.Array> classe fornece muitos outros métodos úteis e propriedades de classificação, pesquisa e copiando arrays.  
  
## Exemplo  
 Este exemplo usa a <xref:System.Array.Rank%2A> propriedade para exibir o número de dimensões de uma matriz.  
  
 [!code-cs[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Matrizes](../../../csharp/programming-guide/arrays/index.md)   
 [Matrizes unidimensionais](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)   
 [Matrizes multidimensionais](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)   
 [Matrizes denteadas](../../../csharp/programming-guide/arrays/jagged-arrays.md)