---
title: Matrizes – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: 24c6d54c3fe92ada661e732adec582e87ab62417
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597524"
---
# <a name="arrays-c-programming-guide"></a>Matrizes (Guia de Programação em C#)

Você pode armazenar diversas variáveis do mesmo tipo em uma estrutura de dados de matriz. Você pode declarar uma matriz especificando o tipo de seus elementos.  
  
 `type[] arrayName;`  
  
 O exemplo a seguir cria matrizes unidimensionais, multidimensionais e denteadas:  
  
 [!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]  
  
## <a name="array-overview"></a>Visão geral de matriz

 Uma matriz tem as seguintes propriedades:  
  
- Uma matriz pode ser [Unidimensional](./single-dimensional-arrays.md), [Multidimensional](./multidimensional-arrays.md) ou [Denteada](./jagged-arrays.md).  
  
- O número de dimensões e o tamanho de cada dimensão são estabelecidos quando a instância de matriz é criada. Esses valores não podem ser alterados durante o ciclo de vida da instância.  
  
- Os valores padrão dos elementos de matriz numérica são definidos como zero, e os elementos de referência são definidos como null.  
  
- Uma matriz denteada é uma matriz de matrizes e, portanto, seus elementos são tipos de referência e são inicializados para `null`.  
  
- As matrizes são indexadas por zero: uma matriz com elementos `n` é indexada de `0` para `n-1`.  
  
- Os elementos de matriz podem ser de qualquer tipo, inclusive um tipo de matriz.  
  
- Os tipos de matriz são [tipos de referência](../../language-reference/keywords/reference-types.md) derivados do tipo base abstrato <xref:System.Array>. Como esse tipo implementa <xref:System.Collections.IEnumerable> e <xref:System.Collections.Generic.IEnumerable%601>, você pode usar a iteração [foreach](../../language-reference/keywords/foreach-in.md) em todas as matrizes em c#.  
  
## <a name="related-sections"></a>Seções relacionadas  
  
- [Matrizes como objetos](./arrays-as-objects.md)  
  
- [Usando foreach com matrizes](./using-foreach-with-arrays.md)  
  
- [Passando matrizes como argumentos](./passing-arrays-as-arguments.md)  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../index.md)
- [Coleções](../concepts/collections.md)
