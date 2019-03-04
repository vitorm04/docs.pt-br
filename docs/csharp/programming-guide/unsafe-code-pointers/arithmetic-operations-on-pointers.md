---
title: Operações aritméticas em ponteiros – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
ms.openlocfilehash: bfa81bc926b4fe81455cecb88bc55f4dcd69268e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977832"
---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a><span data-ttu-id="924a6-102">Operações aritméticas em ponteiros (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="924a6-102">Arithmetic operations on pointers (C# Programming Guide)</span></span>
<span data-ttu-id="924a6-103">Este tópico discute o uso de operadores aritméticos `+` e `-` para manipular ponteiros.</span><span class="sxs-lookup"><span data-stu-id="924a6-103">This topic discusses using the arithmetic operators `+` and `-` to manipulate pointers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="924a6-104">Você não pode executar operações aritméticas em ponteiros void.</span><span class="sxs-lookup"><span data-stu-id="924a6-104">You cannot perform any arithmetic operations on void pointers.</span></span>  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a><span data-ttu-id="924a6-105">Adicionar e subtrair valores numéricos de/para ponteiros</span><span class="sxs-lookup"><span data-stu-id="924a6-105">Adding and subtracting numeric values to or from pointers</span></span>  
 <span data-ttu-id="924a6-106">Você pode adicionar um valor `n` do tipo [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md) ou [ulong](../../../csharp/language-reference/keywords/ulong.md) a um ponteiro.</span><span class="sxs-lookup"><span data-stu-id="924a6-106">You can add a value `n` of type [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), or [ulong](../../../csharp/language-reference/keywords/ulong.md) to a pointer.</span></span> <span data-ttu-id="924a6-107">Se `p` for um ponteiro do tipo `pointer-type*`, o resultado `p+n` será o ponteiro resultante da adição de `n * sizeof(pointer-type)` ao endereço de `p`.</span><span class="sxs-lookup"><span data-stu-id="924a6-107">If `p` is a pointer of the type `pointer-type*`, the result `p+n` is the pointer resulting from adding `n * sizeof(pointer-type)` to the address of `p`.</span></span> <span data-ttu-id="924a6-108">Da mesma forma, `p-n` é o ponteiro resultante da subtração de `n * sizeof(pointer-type)` do endereço de `p`.</span><span class="sxs-lookup"><span data-stu-id="924a6-108">Similarly, `p-n` is the pointer resulting from subtracting `n * sizeof(pointer-type)` from the address of `p`.</span></span>  
  
## <a name="subtracting-pointers"></a><span data-ttu-id="924a6-109">Subtração de ponteiros</span><span class="sxs-lookup"><span data-stu-id="924a6-109">Subtracting pointers</span></span>  
 <span data-ttu-id="924a6-110">Você também pode subtrair ponteiros do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="924a6-110">You can also subtract pointers of the same type.</span></span> <span data-ttu-id="924a6-111">O resultado é sempre do tipo `long`.</span><span class="sxs-lookup"><span data-stu-id="924a6-111">The result is always of the type `long`.</span></span> <span data-ttu-id="924a6-112">Por exemplo, se `p1` e `p2` são ponteiros do tipo `pointer-type*`, a expressão `p1-p2` resulta em:</span><span class="sxs-lookup"><span data-stu-id="924a6-112">For example, if `p1` and `p2` are pointers of the type `pointer-type*`, then the expression `p1-p2` results in:</span></span>  
  
 `((long)p1 - (long)p2)/sizeof(pointer-type)`  
  
 <span data-ttu-id="924a6-113">Nenhuma exceção é gerada quando a operação aritmética estoura o domínio do ponteiro e o resultado depende da implementação.</span><span class="sxs-lookup"><span data-stu-id="924a6-113">No exceptions are generated when the arithmetic operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="924a6-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="924a6-114">Example</span></span>  
 [!code-csharp[csProgGuidePointers#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#14)]  
  
 [!code-csharp[csProgGuidePointers#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#15)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="924a6-115">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="924a6-115">C# language specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="924a6-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="924a6-116">See also</span></span>

- [<span data-ttu-id="924a6-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="924a6-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="924a6-118">Código não seguro e ponteiros</span><span class="sxs-lookup"><span data-stu-id="924a6-118">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="924a6-119">Expressões de ponteiro</span><span class="sxs-lookup"><span data-stu-id="924a6-119">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="924a6-120">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="924a6-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
- [<span data-ttu-id="924a6-121">Manipulando ponteiros</span><span class="sxs-lookup"><span data-stu-id="924a6-121">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)
- [<span data-ttu-id="924a6-122">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="924a6-122">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="924a6-123">Tipos</span><span class="sxs-lookup"><span data-stu-id="924a6-123">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="924a6-124">unsafe</span><span class="sxs-lookup"><span data-stu-id="924a6-124">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="924a6-125">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="924a6-125">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="924a6-126">stackalloc</span><span class="sxs-lookup"><span data-stu-id="924a6-126">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
