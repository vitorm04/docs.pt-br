---
title: Matrizes – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: cf684d2ec7ae7282b1ab68817357773f0f96c9ae
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245646"
---
# <a name="arrays-c-programming-guide"></a>Matrizes (Guia de Programação em C#)

Você pode armazenar diversas variáveis do mesmo tipo em uma estrutura de dados de matriz. Você pode declarar uma matriz especificando o tipo de seus elementos.  
  
 `type[] arrayName;`  
  
 Os exemplos a seguir criam matrizes unidimensionais, multidimensionais e denteadas:  
  
 [!code-csharp[csProgGuideArrays#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/index_1.cs)]  
  
## <a name="array-overview"></a>Visão geral de matriz

 Uma matriz tem as seguintes propriedades:  
  
-   Uma matriz pode ser [Unidimensional](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [Multidimensional](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) ou [Denteada](../../../csharp/programming-guide/arrays/jagged-arrays.md).  
  
-   O número de dimensões e o tamanho de cada dimensão são estabelecidos quando a instância de matriz é criada. Esses valores não podem ser alterados durante o ciclo de vida da instância.  
  
-   Os valores padrão dos elementos de matriz numérica são definidos como zero, e os elementos de referência são definidos como null.  
  
-   Uma matriz denteada é uma matriz de matrizes e, portanto, seus elementos são tipos de referência e são inicializados para `null`.  
  
-   As matrizes são indexadas por zero: uma matriz com elementos `n` é indexada de `0` para `n-1`.  
  
-   Os elementos de matriz podem ser de qualquer tipo, inclusive um tipo de matriz.  
  
-   Os tipos de matriz são [tipos de referência](../../../csharp/language-reference/keywords/reference-types.md) derivados do tipo base abstrato <xref:System.Array>. Como esse tipo implementa <xref:System.Collections.IEnumerable> e <xref:System.Collections.Generic.IEnumerable%601>, você pode usar a iteração [foreach](../../../csharp/language-reference/keywords/foreach-in.md) em todas as matrizes em c#.  
  
## <a name="related-sections"></a>Seções relacionadas  
  
-   [Matrizes como objetos](../../../csharp/programming-guide/arrays/arrays-as-objects.md)  
  
-   [Usando foreach com matrizes](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
-   [Passando matrizes como argumentos](../../../csharp/programming-guide/arrays/passing-arrays-as-arguments.md)  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Coleções](../../../csharp/programming-guide/concepts/collections.md)
