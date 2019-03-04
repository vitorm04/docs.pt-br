---
title: Matrizes multidimensionais – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: df9063d0616b72ad15c9c48fa4459a6dc98b77c1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972606"
---
# <a name="multidimensional-arrays-c-programming-guide"></a>Matrizes multidimensionais (Guia de Programação em C#)

As matrizes podem ter mais de uma dimensão. Por exemplo, a declaração a seguir cria uma matriz bidimensional de quatro linhas e duas colunas.  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 A declaração a seguir cria uma matriz de três dimensões, 4, 2 e 3.  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a>Inicialização de Matriz

 É possível inicializar a matriz na declaração, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 Também é possível inicializar a matriz sem especificar a classificação.  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 Caso você escolha declarar uma variável de matriz sem inicialização, será necessário usar o operador `new` ao atribuir uma matriz a essa variável. O uso de `new` é mostrado no exemplo a seguir.  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 O exemplo a seguir atribui um valor a um elemento de matriz específico.  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 Da mesma forma, o exemplo a seguir obtém o valor de um elemento de matriz específico e o atribui à variável `elementValue`.  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 O exemplo de código a seguir inicializa os elementos da matriz com valores padrão (exceto em matrizes denteadas).  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Matrizes](../../../csharp/programming-guide/arrays/index.md)
- [Matrizes unidimensionais](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)
- [Matrizes denteadas](../../../csharp/programming-guide/arrays/jagged-arrays.md)
