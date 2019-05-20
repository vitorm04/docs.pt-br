---
title: Operações aritméticas em ponteiros – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
ms.openlocfilehash: b08f9dbf8137e483bd38a4f396732191598532cf
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635230"
---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a>Operações aritméticas em ponteiros (Guia de Programação em C#)
Este tópico discute o uso de operadores aritméticos `+` e `-` para manipular ponteiros.  
  
> [!NOTE]
>  Você não pode executar operações aritméticas em ponteiros void.  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a>Adicionar e subtrair valores numéricos de/para ponteiros  
 Você pode adicionar um valor `n` do tipo [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md) ou [ulong](../../../csharp/language-reference/keywords/ulong.md) a um ponteiro. Se `p` for um ponteiro do tipo `pointer-type*`, o resultado `p+n` será o ponteiro resultante da adição de `n * sizeof(pointer-type)` ao endereço de `p`. Da mesma forma, `p-n` é o ponteiro resultante da subtração de `n * sizeof(pointer-type)` do endereço de `p`.  
  
## <a name="subtracting-pointers"></a>Subtração de ponteiros  
 Você também pode subtrair ponteiros do mesmo tipo. O resultado é sempre do tipo `long`. Por exemplo, se `p1` e `p2` são ponteiros do tipo `pointer-type*`, a expressão `p1-p2` resulta em:  
  
 `((long)p1 - (long)p2)/sizeof(pointer-type)`  
  
 Nenhuma exceção é gerada quando a operação aritmética estoura o domínio do ponteiro e o resultado depende da implementação.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuidePointers#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#14)]  
  
 [!code-csharp[csProgGuidePointers#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#15)]  
  
## <a name="c-language-specification"></a>Especificação da linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
- [Operadores do C#](../../../csharp/language-reference/operators/index.md)
- [Manipulando ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
- [Tipos de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Tipos](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
