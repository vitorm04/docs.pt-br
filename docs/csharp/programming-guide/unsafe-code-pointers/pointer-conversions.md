---
title: Conversões de ponteiro (Guia de Programação em C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 36589d139c91e04d9e3d8b31281a91c26b85a5d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="pointer-conversions-c-programming-guide"></a>Conversões de ponteiro (Guia de Programação em C#)
A tabela a seguir mostra as conversões de ponteiro implícitas predefinidas. As conversões implícitas podem ocorrer em diversas situações, incluindo instruções de atribuição e invocações de método.  
  
## <a name="implicit-pointer-conversions"></a>Conversões de ponteiro implícitas  
  
|De|Para|  
|----------|--------|  
|Qualquer tipo de ponteiro|void*|  
|nulo|Qualquer tipo de ponteiro|  
  
 A conversão explícita de ponteiro é usada para realizar conversões para as quais não há conversão implícita, usando uma expressão de conversão. A tabela a seguir mostra essas conversões.  
  
## <a name="explicit-pointer-conversions"></a>Conversões de ponteiro explícitas  
  
|De|Para|  
|----------|--------|  
|Qualquer tipo de ponteiro|Qualquer outro tipo de ponteiro|  
|sbyte, byte, short, ushort, int, uint, long ou ulong|Qualquer tipo de ponteiro|  
|Qualquer tipo de ponteiro|sbyte, byte, short, ushort, int, uint, long ou ulong|  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, um ponteiro para `int` é convertido em um ponteiro para `byte`. Observe que o ponteiro aponta para o menor byte endereçado da variável. Quando você incrementar sucessivamente o resultado, até o tamanho de `int` (4 bytes), você poderá exibir os bytes restantes da variável.  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Expressões de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Tipos de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Tipos](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
