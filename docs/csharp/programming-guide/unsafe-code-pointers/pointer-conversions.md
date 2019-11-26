---
title: Conversões de ponteiro – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: b0a517eacc505376c9502e9d095c7aac0cd54555
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73417527"
---
# <a name="pointer-conversions-c-programming-guide"></a>Conversões de ponteiro (Guia de Programação em C#)
A tabela a seguir mostra as conversões de ponteiro implícitas predefinidas. As conversões implícitas podem ocorrer em diversas situações, incluindo instruções de atribuição e invocações de método.  
  
## <a name="implicit-pointer-conversions"></a>Conversões de ponteiro implícitas  
  
|De|{1&gt;Para&lt;1}|  
|----------|--------|  
|Qualquer tipo de ponteiro|void*|  
|{1&gt;nulo&lt;1}|Qualquer tipo de ponteiro|  
  
 A conversão explícita de ponteiro é usada para realizar conversões para as quais não há conversão implícita, usando uma expressão de conversão. A tabela a seguir mostra essas conversões.  
  
## <a name="explicit-pointer-conversions"></a>Conversões de ponteiro explícitas  
  
|De|{1&gt;Para&lt;1}|  
|----------|--------|  
|Qualquer tipo de ponteiro|Qualquer outro tipo de ponteiro|  
|sbyte, byte, short, ushort, int, uint, long ou ulong|Qualquer tipo de ponteiro|  
|Qualquer tipo de ponteiro|sbyte, byte, short, ushort, int, uint, long ou ulong|  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, um ponteiro para `int` é convertido em um ponteiro para `byte`. Observe que o ponteiro aponta para o menor byte endereçado da variável. Quando você incrementar sucessivamente o resultado, até o tamanho de `int` (4 bytes), você poderá exibir os bytes restantes da variável.  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../index.md)
- [Tipos de ponteiro](./pointer-types.md)
- [Tipos](/dotnet/csharp/language-reference/keywords)
- [unsafe](../../language-reference/keywords/unsafe.md)
- [Instrução fixed](../../language-reference/keywords/fixed-statement.md)
- [stackalloc](../../language-reference/operators/stackalloc.md)
