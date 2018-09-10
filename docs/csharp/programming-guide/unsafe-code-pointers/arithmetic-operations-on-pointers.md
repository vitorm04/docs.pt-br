---
title: Operações aritméticas em ponteiros (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
ms.openlocfilehash: 3694699466f7a200eecd5eef85f60fa19f9584a8
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43862297"
---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a>Operações aritméticas em ponteiros (Guia de Programação em C#)
Este tópico discute o uso de operadores aritméticos `+` e **-** para manipular ponteiros.  
  
> [!NOTE]
>  Você não pode executar operações aritméticas em ponteiros void.  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a>Adicionando e subtraindo valores numéricos de/para ponteiros  
 Você pode adicionar um valor `n` do tipo [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md) ou [ulong](../../../csharp/language-reference/keywords/ulong.md) a um ponteiro `p` de qualquer tipo, exceto `void*`. O resultado `p+n` é o ponteiro resultante da adição de `n * sizeof(p) to the address of p`. Da mesma forma, `p-n` é o ponteiro resultante da subtração de `n * sizeof(p)` do endereço de `p`.  
  
## <a name="subtracting-pointers"></a>Subtração de ponteiros  
 Você também pode subtrair ponteiros do mesmo tipo. O resultado é sempre do tipo `long`. Por exemplo, se `p1` e `p2` são ponteiros do tipo `pointer-type*`, a expressão `p1-p2` resulta em:  
  
 `((long)p1 - (long)p2)/sizeof(pointer_type)`  
  
 Nenhuma exceção é gerada quando a operação aritmética estoura o domínio do ponteiro e o resultado depende da implementação.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
- [Expressões de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [Operadores do C#](../../../csharp/language-reference/operators/index.md)  
- [Manipulando ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
- [Tipos de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [Tipos](../../../csharp/language-reference/keywords/types.md)  
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
- [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
