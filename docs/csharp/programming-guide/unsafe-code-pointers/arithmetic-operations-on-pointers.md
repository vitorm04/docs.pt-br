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
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a><span data-ttu-id="6ebb5-102">Operações aritméticas em ponteiros (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="6ebb5-102">Arithmetic Operations on Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="6ebb5-103">Este tópico discute o uso de operadores aritméticos `+` e **-** para manipular ponteiros.</span><span class="sxs-lookup"><span data-stu-id="6ebb5-103">This topic discusses using the arithmetic operators `+` and **-** to manipulate pointers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ebb5-104">Você não pode executar operações aritméticas em ponteiros void.</span><span class="sxs-lookup"><span data-stu-id="6ebb5-104">You cannot perform any arithmetic operations on void pointers.</span></span>  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a><span data-ttu-id="6ebb5-105">Adicionando e subtraindo valores numéricos de/para ponteiros</span><span class="sxs-lookup"><span data-stu-id="6ebb5-105">Adding and Subtracting Numeric Values to or From Pointers</span></span>  
 <span data-ttu-id="6ebb5-106">Você pode adicionar um valor `n` do tipo [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md) ou [ulong](../../../csharp/language-reference/keywords/ulong.md) a um ponteiro `p` de qualquer tipo, exceto `void*`.</span><span class="sxs-lookup"><span data-stu-id="6ebb5-106">You can add a value `n` of type [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), or [ulong](../../../csharp/language-reference/keywords/ulong.md) to a pointer, `p`,of any type except `void*`.</span></span> <span data-ttu-id="6ebb5-107">O resultado `p+n` é o ponteiro resultante da adição de `n * sizeof(p) to the address of p`.</span><span class="sxs-lookup"><span data-stu-id="6ebb5-107">The result `p+n` is the pointer resulting from adding `n * sizeof(p) to the address of p`.</span></span> <span data-ttu-id="6ebb5-108">Da mesma forma, `p-n` é o ponteiro resultante da subtração de `n * sizeof(p)` do endereço de `p`.</span><span class="sxs-lookup"><span data-stu-id="6ebb5-108">Similarly, `p-n` is the pointer resulting from subtracting `n * sizeof(p)` from the address of `p`.</span></span>  
  
## <a name="subtracting-pointers"></a><span data-ttu-id="6ebb5-109">Subtração de ponteiros</span><span class="sxs-lookup"><span data-stu-id="6ebb5-109">Subtracting Pointers</span></span>  
 <span data-ttu-id="6ebb5-110">Você também pode subtrair ponteiros do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="6ebb5-110">You can also subtract pointers of the same type.</span></span> <span data-ttu-id="6ebb5-111">O resultado é sempre do tipo `long`.</span><span class="sxs-lookup"><span data-stu-id="6ebb5-111">The result is always of the type `long`.</span></span> <span data-ttu-id="6ebb5-112">Por exemplo, se `p1` e `p2` são ponteiros do tipo `pointer-type*`, a expressão `p1-p2` resulta em:</span><span class="sxs-lookup"><span data-stu-id="6ebb5-112">For example, if `p1` and `p2` are pointers of the type `pointer-type*`, then the expression `p1-p2` results in:</span></span>  
  
 `((long)p1 - (long)p2)/sizeof(pointer_type)`  
  
 <span data-ttu-id="6ebb5-113">Nenhuma exceção é gerada quando a operação aritmética estoura o domínio do ponteiro e o resultado depende da implementação.</span><span class="sxs-lookup"><span data-stu-id="6ebb5-113">No exceptions are generated when the arithmetic operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ebb5-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6ebb5-114">Example</span></span>  
 [!code-csharp[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="6ebb5-115">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="6ebb5-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6ebb5-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ebb5-116">See Also</span></span>

- [<span data-ttu-id="6ebb5-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="6ebb5-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="6ebb5-118">Código não seguro e ponteiros</span><span class="sxs-lookup"><span data-stu-id="6ebb5-118">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
- [<span data-ttu-id="6ebb5-119">Expressões de ponteiro</span><span class="sxs-lookup"><span data-stu-id="6ebb5-119">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="6ebb5-120">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="6ebb5-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="6ebb5-121">Manipulando ponteiros</span><span class="sxs-lookup"><span data-stu-id="6ebb5-121">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
- [<span data-ttu-id="6ebb5-122">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="6ebb5-122">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="6ebb5-123">Tipos</span><span class="sxs-lookup"><span data-stu-id="6ebb5-123">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="6ebb5-124">unsafe</span><span class="sxs-lookup"><span data-stu-id="6ebb5-124">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="6ebb5-125">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="6ebb5-125">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="6ebb5-126">stackalloc</span><span class="sxs-lookup"><span data-stu-id="6ebb5-126">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
