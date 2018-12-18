---
title: Usar foreach com matrizes – Guia de Programação em C#
ms.custom: seodec18
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: a290cd709dd6491981658f467fa0163011290128
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238462"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>Usar foreach com matrizes (Guia de Programação em C#)

Essa instrução [foreach](../../language-reference/keywords/foreach-in.md) fornece uma maneira simples e limpa de iterar através dos elementos de uma matriz.

Em matrizes unidimensionais, a instrução `foreach` processa elementos em ordem crescente de índice, começando com o índice 0 e terminando com índice `Length - 1`:

[!code-csharp[csProgGuideArrays#28](./codesnippet/CSharp/using-foreach-with-arrays_1.cs)]

Em matrizes multidimensionais, os elementos são percorridos de modo a que os índices da dimensão mais à direita sejam aumentados primeiro e, em seguida, da próxima dimensão à esquerda, e assim por diante seguindo para a esquerda:

[!code-csharp[csProgGuideArrays#29](./codesnippet/CSharp/using-foreach-with-arrays_2.cs)]

No entanto, com matrizes multidimensionais, usar um loop aninhado [for](../../language-reference/keywords/for.md) oferece mais controle sobre a ordem na qual processar os elementos da matriz.

## <a name="see-also"></a>Consulte também

- <xref:System.Array>  
- [Guia de Programação em C#](../index.md)  
- [Matrizes](index.md)  
- [Matrizes unidimensionais](single-dimensional-arrays.md)  
- [Matrizes multidimensionais](multidimensional-arrays.md)  
- [Matrizes denteadas](jagged-arrays.md)
