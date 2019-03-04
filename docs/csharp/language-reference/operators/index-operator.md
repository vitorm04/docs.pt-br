---
title: Operador [] – referência do C#
ms.custom: seodec18
ms.date: 01/10/2019
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
ms.openlocfilehash: 9088393f61d300ee76e56e320bec17b4a79bfebb
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835584"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="f150b-102">Operador [] (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="f150b-102">[] operator (C# Reference)</span></span>

<span data-ttu-id="f150b-103">Os colchetes, `[]`, normalmente são usados para acesso de elemento de matriz, indexador ou ponteiro.</span><span class="sxs-lookup"><span data-stu-id="f150b-103">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

<span data-ttu-id="f150b-104">Para obter mais informações sobre o acesso de elemento de ponteiro, confira [Como acessar um elemento de matriz com um ponteiro](../../programming-guide/unsafe-code-pointers/how-to-access-an-array-element-with-a-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="f150b-104">For more information about pointer element access, see [How to: access an array element with a pointer](../../programming-guide/unsafe-code-pointers/how-to-access-an-array-element-with-a-pointer.md).</span></span>

<span data-ttu-id="f150b-105">Os colchetes também são usados para especificar [atributos](../../programming-guide/concepts/attributes/index.md):</span><span class="sxs-lookup"><span data-stu-id="f150b-105">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="array-access"></a><span data-ttu-id="f150b-106">Acesso de matriz</span><span class="sxs-lookup"><span data-stu-id="f150b-106">Array access</span></span>

<span data-ttu-id="f150b-107">O exemplo a seguir demonstra como acessar elementos de matriz:</span><span class="sxs-lookup"><span data-stu-id="f150b-107">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](~/samples/snippets/csharp/language-reference/operators/IndexOperatorExamples.cs#Arrays)]

<span data-ttu-id="f150b-108">Se um índice de matriz estiver fora dos limites da dimensão correspondente de uma matriz, uma <xref:System.IndexOutOfRangeException> será gerada.</span><span class="sxs-lookup"><span data-stu-id="f150b-108">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="f150b-109">Como mostra o exemplo anterior, você também pode usar colchetes na declaração de um tipo de matriz e na criação de instâncias da matriz.</span><span class="sxs-lookup"><span data-stu-id="f150b-109">As the preceding example shows, you also use square brackets in declaration of an array type and instantiation of array instances.</span></span>

<span data-ttu-id="f150b-110">Para obter mais informações sobre matrizes, confira [Matrizes](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="f150b-110">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

## <a name="indexer-access"></a><span data-ttu-id="f150b-111">Acesso de indexador</span><span class="sxs-lookup"><span data-stu-id="f150b-111">Indexer access</span></span>

<span data-ttu-id="f150b-112">O exemplo a seguir usa o tipo <xref:System.Collections.Generic.Dictionary%602> do .NET para demonstrar o acesso de indexador:</span><span class="sxs-lookup"><span data-stu-id="f150b-112">The following example uses .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](~/samples/snippets/csharp/language-reference/operators/IndexOperatorExamples.cs#Indexers)]

<span data-ttu-id="f150b-113">Os indexadores permitem indexar instâncias de um tipo definido pelo usuário de maneira semelhante à indexação de matriz.</span><span class="sxs-lookup"><span data-stu-id="f150b-113">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="f150b-114">Ao contrário dos índices da matriz, que precisam ser um inteiro, os argumentos do indexador podem ser declarados como qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="f150b-114">Unlike array indices, which must be integer, the indexer arguments can be declared to be of any type.</span></span>

<span data-ttu-id="f150b-115">Para obter mais informações sobre indexadores, confira [Indexadores](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="f150b-115">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="f150b-116">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="f150b-116">Operator overloadability</span></span>

<span data-ttu-id="f150b-117">O acesso de elemento `[]` não é considerado um operador que pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="f150b-117">Element access `[]` is not considered an overloadable operator.</span></span> <span data-ttu-id="f150b-118">Use [indexadores](../../programming-guide/indexers/index.md) para permitir a indexação com tipos definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="f150b-118">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f150b-119">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="f150b-119">C# language specification</span></span>

<span data-ttu-id="f150b-120">Para obter mais informações, confira as seções [Acesso de elemento](~/_csharplang/spec/expressions.md#element-access) e [Acesso de elemento de ponteiro](~/_csharplang/spec/unsafe-code.md#pointer-element-access) da [Especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="f150b-120">For more information, see the [Element access](~/_csharplang/spec/expressions.md#element-access) and [Pointer element access](~/_csharplang/spec/unsafe-code.md#pointer-element-access) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f150b-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f150b-121">See also</span></span>

- [<span data-ttu-id="f150b-122">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="f150b-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f150b-123">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="f150b-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f150b-124">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="f150b-124">C# Operators</span></span>](index.md)
- [<span data-ttu-id="f150b-125">Matrizes</span><span class="sxs-lookup"><span data-stu-id="f150b-125">Arrays</span></span>](../../programming-guide/arrays/index.md)
- [<span data-ttu-id="f150b-126">Indexadores</span><span class="sxs-lookup"><span data-stu-id="f150b-126">Indexers</span></span>](../../programming-guide/indexers/index.md)
- [<span data-ttu-id="f150b-127">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="f150b-127">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="f150b-128">Atributos</span><span class="sxs-lookup"><span data-stu-id="f150b-128">Attributes</span></span>](../../programming-guide/concepts/attributes/index.md)
- <span data-ttu-id="f150b-129">[Operadores ?. e ?[]](null-conditional-operators.md)</span><span class="sxs-lookup"><span data-stu-id="f150b-129">[?. and ?[] operators](null-conditional-operators.md)</span></span>