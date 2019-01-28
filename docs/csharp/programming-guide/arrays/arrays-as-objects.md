---
title: Matrizes como objetos – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 0c4b5dcbd9e227e4edd5f549b687e3ded90ee9bc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740483"
---
# <a name="arrays-as-objects-c-programming-guide"></a>Matrizes como objetos (Guia de Programação em C#)

No C#, as matrizes são objetos e não apenas regiões endereçáveis de memória contígua, como no C e no C++. <xref:System.Array> é o tipo base abstrato de todos os tipos de matriz. É possível usar as propriedades e outros membros de classe do <xref:System.Array>. Um exemplo disso é o uso da propriedade <xref:System.Array.Length%2A> para obter o comprimento de uma matriz. O código a seguir atribui o comprimento da matriz `numbers`, que é `5`, a uma variável denominada `lengthOfNumbers`:  
  
 [!code-csharp[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]  
  
 A classe <xref:System.Array> fornece vários outros métodos e propriedades úteis para classificar, pesquisar e copiar matrizes.  
  
## <a name="example"></a>Exemplo

 Este exemplo usa a propriedade <xref:System.Array.Rank%2A> para exibir a quantidade de dimensões de uma matriz.  
  
 [!code-csharp[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Matrizes](../../../csharp/programming-guide/arrays/index.md)
- [Matrizes unidimensionais](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)
- [Matrizes multidimensionais](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
- [Matrizes denteadas](../../../csharp/programming-guide/arrays/jagged-arrays.md)
