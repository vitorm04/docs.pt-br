---
title: "Passando matrizes com o uso de ref e out (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], passing using ref and out
ms.assetid: 6a2b261e-a1cc-49a6-b4f0-6cacae385a1e
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f76f63aee0100c6af6bde73c8543b4e7136b1954
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="passing-arrays-using-ref-and-out-c-programming-guide"></a>Passando matrizes com o uso de ref e out (Guia de Programação em C#)
Como todos os parâmetros [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), um parâmetro `out` de um tipo de matriz deve ser atribuído antes que seja usado; ou seja, deve ser atribuído pelo computador chamado. Por exemplo:  
  
 [!code-csharp[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]  
  
 Como todos os parâmetros [ref](../../../csharp/language-reference/keywords/ref.md), um parâmetro `ref` de um tipo de matriz deve ser definitivamente atribuído pelo chamador. Portanto, não há necessidade de ser atribuído definitivamente pelo receptor. Um parâmetro `ref` de um tipo de matriz pode ser alterado como resultado da chamada. Por exemplo, o valor [nulo](../../../csharp/language-reference/keywords/null.md) pode ser atribuído à matriz ou ela pode ser inicializada em uma matriz diferente. Por exemplo:  
  
 [!code-csharp[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]  
  
 Os dois exemplos a seguir demonstram a diferença entre `out` e `ref` quando usados ao passar matrizes para métodos.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, a matriz `theArray` é declarada no chamador (o método `Main`) e inicializada no método `FillArray`. Em seguida, os elementos da matriz são retornados para o chamador e exibidos.  
  
 [!code-csharp[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, a matriz `theArray` é inicializada no chamador (o método `Main`) e passada para o método `FillArray` ao usar o parâmetro `ref`. Alguns elementos da matriz são atualizados no método `FillArray`. Em seguida, os elementos da matriz são retornados para o chamador e exibidos.  
  
 [!code-csharp[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [ref](../../../csharp/language-reference/keywords/ref.md)  
 [Modificador de parâmetro out](../../../csharp/language-reference/keywords/out-parameter-modifier.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Matrizes](../../../csharp/programming-guide/arrays/index.md)  
 [Matrizes unidimensionais](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Matrizes multidimensionais](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [Matrizes denteadas](../../../csharp/programming-guide/arrays/jagged-arrays.md)
