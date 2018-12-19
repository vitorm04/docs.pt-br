---
title: Matrizes denteadas – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: f517a9a6d6e10f04df70729fb9e641c1f955f28a
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237851"
---
# <a name="jagged-arrays-c-programming-guide"></a>Matrizes denteadas (Guia de Programação em C#)

Uma matriz denteada é uma matriz cujos elementos são matrizes. Os elementos de uma matriz denteada podem ter diferentes dimensões e tamanhos. Às vezes, uma matriz denteada é chamada de uma "matriz de matrizes." Os exemplos a seguir mostram como declarar, inicializar e acessar matrizes denteadas.  
  
 A seguir, há uma declaração de uma matriz unidimensional que tem três elementos, cada um do qual é uma matriz de dimensão única de inteiros:  
  
 [!code-csharp[csProgGuideArrays#19](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_1.cs)]  
  
 Antes de usar `jaggedArray`, seus elementos devem ser inicializados. É possível inicializar os elementos dessa forma:  
  
 [!code-csharp[csProgGuideArrays#20](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_2.cs)]  
  
 Cada um dos elementos é uma matriz unidimensional de inteiros. O primeiro elemento é uma matriz de 5 inteiros, o segundo é uma matriz de 4 inteiros e o terceiro é uma matriz de 2 inteiros.  
  
 Também é possível usar os inicializadores para preencher os elementos matriz com valores, caso em que não é necessário o tamanho da matriz. Por exemplo:  
  
 [!code-csharp[csProgGuideArrays#21](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_3.cs)]  
  
 Também é possível inicializar a matriz mediante uma declaração como esta:  
  
 [!code-csharp[csProgGuideArrays#22](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_4.cs)]  
  
 É possível usar a seguinte forma abreviada. Observe que não é possível omitir o operador `new` da inicialização de elementos, porque não há nenhuma inicialização padrão para os elementos:  
  
 [!code-csharp[csProgGuideArrays#23](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_5.cs)]  
  
 Uma matriz denteada é uma matriz de matrizes e, portanto, seus elementos são tipos de referência e são inicializados para `null`.  
  
 É possível acessar elementos de matrizes individuais como estes exemplos:  
  
 [!code-csharp[csProgGuideArrays#24](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_6.cs)]  
  
 É possível misturar matrizes denteadas e multidimensionais. A seguir, há uma declaração e inicialização de uma matriz denteada unidimensional que contém três elementos de matriz bidimensional de tamanhos diferentes. Para obter mais informações sobre matrizes bidimensionais, consulte [Matrizes Multidimensionais](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).  
  
 [!code-csharp[csProgGuideArrays#25](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_7.cs)]  
  
 É possível acessar elementos individuais conforme mostrado neste exemplo, que exibe o valor do elemento `[1,0]` da primeira matriz (valor `5`):  
  
 [!code-csharp[csProgGuideArrays#26](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_8.cs)]  
  
 O método `Length` retorna inúmeros conjuntos contidos na matriz denteada. Por exemplo, supondo que você tenha declarado a matriz anterior, esta linha:  
  
 [!code-csharp[csProgGuideArrays#27](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_9.cs)]  
  
 retorna um valor de 3.  
  
## <a name="example"></a>Exemplo

 Este exemplo cria uma matriz cujos elementos são matrizes. Cada um dos elementos da matriz tem um tamanho diferente.  
  
 [!code-csharp[csProgGuideArrays#18](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_10.cs)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Array>  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Matrizes](../../../csharp/programming-guide/arrays/index.md)  
- [Matrizes unidimensionais](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
- [Matrizes multidimensionais](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
