---
title: Comparação de ponteiros – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
ms.openlocfilehash: 25bc1c7b701c36d2daf1918986eb6a8e56980990
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635144"
---
# <a name="pointer-comparison-c-programming-guide"></a>Comparação de ponteiros (Guia de Programação em C#)
É possível aplicar os seguintes operadores para comparar ponteiros de qualquer tipo:  
  
 **==   !=   \<   >   \<=   >=**  
  
 Os operadores de comparação comparam os endereços dos dois operandos como se fossem inteiros sem sinal.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuidePointers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#16)]  
  
 [!code-csharp[csProgGuidePointers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#17)]  
  
## <a name="sample-output"></a>Saída de Exemplo  
 `True`  
  
 `False`  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Operadores do C#](../../../csharp/language-reference/operators/index.md)
- [Manipulando ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
- [Tipos de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Tipos](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
