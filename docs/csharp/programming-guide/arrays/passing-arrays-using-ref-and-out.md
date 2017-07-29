---
title: "Passando matrizes com o uso de ref e out (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- arrays [C#], passing using ref and out
ms.assetid: 6a2b261e-a1cc-49a6-b4f0-6cacae385a1e
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 58fc359881295a9e6627ac1269ef17aa298009c7
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="passing-arrays-using-ref-and-out-c-programming-guide"></a>Passando matrizes com o uso de ref e out (Guia de Programação em C#)
Como todos os parâmetros [out](../../../csharp/language-reference/keywords/out.md), um parâmetro `out` de um tipo de matriz deve ser atribuído antes que seja usado; ou seja, deve ser atribuído pelo computador chamado. Por exemplo:  
  
 [!code-cs[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]  
  
 Como todos os parâmetros [ref](../../../csharp/language-reference/keywords/ref.md), um parâmetro `ref` de um tipo de matriz deve ser definitivamente atribuído pelo chamador. Portanto, não há necessidade de ser atribuído definitivamente pelo receptor. Um parâmetro `ref` de um tipo de matriz pode ser alterado como resultado da chamada. Por exemplo, o valor [nulo](../../../csharp/language-reference/keywords/null.md) pode ser atribuído à matriz ou ela pode ser inicializada em uma matriz diferente. Por exemplo:  
  
 [!code-cs[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]  
  
 Os dois exemplos a seguir demonstram a diferença entre `out` e `ref` quando usados ao passar matrizes para métodos.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, a matriz `theArray` é declarada no chamador (o método `Main`) e inicializada no método `FillArray`. Em seguida, os elementos da matriz são retornados para o chamador e exibidos.  
  
 [!code-cs[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, a matriz `theArray` é inicializada no chamador (o método `Main`) e passada para o método `FillArray` ao usar o parâmetro `ref`. Alguns elementos da matriz são atualizados no método `FillArray`. Em seguida, os elementos da matriz são retornados para o chamador e exibidos.  
  
 [!code-cs[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [ref](../../../csharp/language-reference/keywords/ref.md)   
 [Modificador de parâmetro out](../../../csharp/language-reference/keywords/out-parameter-modifier.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Matrizes](../../../csharp/programming-guide/arrays/index.md)   
 [Matrizes Unidimensionais](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)   
 [Matrizes Multidimensionais](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)   
 [Matrizes denteadas](../../../csharp/programming-guide/arrays/jagged-arrays.md)

