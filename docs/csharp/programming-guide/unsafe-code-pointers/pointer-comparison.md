---
title: Comparação de ponteiros – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
ms.openlocfilehash: 5185bd5e1686858452efcc7c89e2c1977e094386
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969200"
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
- [Expressões de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [Operadores do C#](../../../csharp/language-reference/operators/index.md)
- [Manipulando ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)
- [Tipos de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Tipos](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
