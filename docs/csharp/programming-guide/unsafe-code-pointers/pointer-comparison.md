---
title: Comparação de ponteiros – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
ms.openlocfilehash: a2cbbabdad1d79c82bb5b3ec02a391727e552c98
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718631"
---
# <a name="pointer-comparison-c-programming-guide"></a>Comparação de ponteiros (Guia de Programação em C#)
É possível aplicar os seguintes operadores para comparar ponteiros de qualquer tipo:  
  
 **==   !=   \<   >   \<=   >=**  
  
 Os operadores de comparação comparam os endereços dos dois operandos como se fossem inteiros sem sinal.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuidePointers#16](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#17](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_2.cs)]  
  
## <a name="sample-output"></a>Saída de Exemplo  
 `True`  
  
 `False`  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Expressões de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [Operadores do C#](../../../csharp/language-reference/operators/index.md)
- [Manipulando ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)
- [Tipos de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Tipos](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
