---
title: "Passando matrizes com o uso de ref e out (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "matrizes [C#], passando usando ref e out"
ms.assetid: 6a2b261e-a1cc-49a6-b4f0-6cacae385a1e
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Passando matrizes com o uso de ref e out (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Como todos os parâmetros [out](../../../csharp/language-reference/keywords/out.md), um parâmetro `out` de um tipo de matriz deve ser atribuído antes que seja usado; ou seja, deve ser atribuído pelo receptor.  Por exemplo:  
  
 [!code-cs[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]  
  
 Como todos os parâmetros [ref](../../../csharp/language-reference/keywords/ref.md), um parâmetro `ref` de um tipo de matriz deve ser definitivamente atribuído pelo chamador.  Portanto, não há necessidade de ser atribuído definitivamente pelo receptor.  Um parâmetro `ref` de um tipo de matriz pode ser alterado como resultado da chamada.  Por exemplo, o valor [nulo](../../../csharp/language-reference/keywords/null.md) pode ser atribuído à matriz ou pode ser inicializado em uma matriz diferente.  Por exemplo:  
  
 [!code-cs[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]  
  
 Os dois exemplos a seguir demonstram a diferença entre `out` e `ref` quando usados ao passar matrizes para métodos.  
  
## Exemplo  
 Neste exemplo, a matriz `theArray` é declarada no chamador \(o método `Main`\) e inicializada no método `FillArray`.  Em seguida, os elementos da matriz são retornados para o chamador e exibidos.  
  
 [!code-cs[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]  
  
## Exemplo  
 Neste exemplo, a matriz `theArray` é inicializada no chamador \(o método `Main`\) e passada para o método `FillArray` ao usar o parâmetro `ref`.  Alguns elementos da matriz são atualizados no método `FillArray`.  Em seguida, os elementos da matriz são retornados para o chamador e exibidos.  
  
 [!code-cs[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]  
  
## Consulte também  
 [ref](../../../csharp/language-reference/keywords/ref.md)   
 [Modificador de parâmetro out](../../../csharp/language-reference/keywords/out-parameter-modifier.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Matrizes](../../../csharp/programming-guide/arrays/index.md)   
 [Matrizes unidimensionais](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)   
 [Matrizes multidimensionais](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)   
 [Matrizes denteadas](../../../csharp/programming-guide/arrays/jagged-arrays.md)