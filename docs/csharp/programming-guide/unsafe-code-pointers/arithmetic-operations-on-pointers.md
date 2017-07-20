---
title: "Operações aritméticas em ponteiros (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fc675600526dcaa6afd488fdee57acdc577cf71f
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

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
 [!code-cs[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]  
  
 [!code-cs[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Código Não Seguro e Ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [Expressões de Ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)   
 [Manipulando Ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)   
 [Tipos de Ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [Tipos](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
