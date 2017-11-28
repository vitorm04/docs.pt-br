---
title: "Usando foreach com matrizes (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 797cb9a63a5e1009b170b2afda8634bd21a50035
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>Usando foreach com matrizes (Guia de Programação em C#)
O C# também oferece a instrução [foreach](../../../csharp/language-reference/keywords/foreach-in.md). Essa instrução fornece uma maneira simples e limpa de iterar através dos elementos de uma matriz ou qualquer coleção enumerável. A instrução `foreach` processa os elementos na ordem retornada pela matriz ou enumerador do tipo de coleção que normalmente vai do elemento 0 ao último. Por exemplo, o código a seguir cria uma matriz chamada `numbers` e itera por ela com a instrução `foreach`:  
  
 [!code-csharp[csProgGuideArrays#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_1.cs)]  
  
 Com matrizes multidimensionais, você pode usar o mesmo método para iterar pelos elementos, por exemplo:  
  
 [!code-csharp[csProgGuideArrays#29](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_2.cs)]  
  
 No entanto, com matrizes multidimensionais, usar um loop aninhado [for](../../../csharp/language-reference/keywords/for.md) oferece mais controle sobre os elementos da matriz.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Array>  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Matrizes](../../../csharp/programming-guide/arrays/index.md)  
 [Matrizes unidimensionais](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Matrizes multidimensionais](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [Matrizes denteadas](../../../csharp/programming-guide/arrays/jagged-arrays.md)
