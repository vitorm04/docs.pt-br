---
title: Matrizes como objetos – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 8500cf508b77a0fa7e348ce0fe6b1f16fd2bab25
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977157"
---
# <a name="arrays-as-objects-c-programming-guide"></a>Matrizes como objetos (Guia de Programação em C#)

No C#, as matrizes são objetos e não apenas regiões endereçáveis de memória contígua, como no C e no C++. <xref:System.Array> é o tipo base abstrato de todos os tipos de matriz. É possível usar as propriedades e outros membros de classe do <xref:System.Array>. Um exemplo disso é o uso da propriedade <xref:System.Array.Length%2A> para obter o comprimento de uma matriz. O código a seguir atribui o comprimento da matriz `numbers`, que é `5`, a uma variável denominada `lengthOfNumbers`:  
  
 [!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]  
  
 A classe <xref:System.Array> fornece vários outros métodos e propriedades úteis para classificar, pesquisar e copiar matrizes.  
  
## <a name="example"></a>Exemplo

 Este exemplo usa a propriedade <xref:System.Array.Rank%2A> para exibir a quantidade de dimensões de uma matriz.  
  
 [!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Matrizes](../../../csharp/programming-guide/arrays/index.md)
- [Matrizes unidimensionais](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)
- [Matrizes multidimensionais](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
- [Matrizes denteadas](../../../csharp/programming-guide/arrays/jagged-arrays.md)
