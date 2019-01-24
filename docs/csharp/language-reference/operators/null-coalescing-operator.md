---
title: ?? Operador – referência do C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: b96fe4790aac7ff5ff5394cbaaeaddc1e334e96c
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333207"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="64bcd-103">??</span><span class="sxs-lookup"><span data-stu-id="64bcd-103">??</span></span> <span data-ttu-id="64bcd-104">operator (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="64bcd-104">operator (C# Reference)</span></span>

<span data-ttu-id="64bcd-105">O operador `??` é chamado operador de coalescência nula.</span><span class="sxs-lookup"><span data-stu-id="64bcd-105">The `??` operator is called the null-coalescing operator.</span></span>  <span data-ttu-id="64bcd-106">Ele retornará o operando esquerdo se o operando não for nulo; caso contrário, ele retornará o operando direito.</span><span class="sxs-lookup"><span data-stu-id="64bcd-106">It returns the left-hand operand if the operand is not null; otherwise it returns the right hand operand.</span></span>

## <a name="remarks"></a><span data-ttu-id="64bcd-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="64bcd-107">Remarks</span></span>

<span data-ttu-id="64bcd-108">Um tipo anulável pode representar um valor de domínio do tipo ou o valor pode ser indefinido (nesse caso, o valor será nulo).</span><span class="sxs-lookup"><span data-stu-id="64bcd-108">A nullable type can represent a value from the type’s domain, or the value can be undefined (in which case the value is null).</span></span> <span data-ttu-id="64bcd-109">Você pode usar a expressividade sintática do operador `??` para retornar um valor adequado (o operando direito) quando o operando esquerdo tiver um tipo que permite valor nulo cujo valor seja nulo.</span><span class="sxs-lookup"><span data-stu-id="64bcd-109">You can use the `??` operator’s syntactic expressiveness to return an appropriate value (the right hand operand) when the left operand has a nullable type whose value is null.</span></span> <span data-ttu-id="64bcd-110">Se você tentar atribuir um tipo de valor anulável a um tipo de valor não anulável sem usar o operador `??`, um erro de tempo de compilação será gerado.</span><span class="sxs-lookup"><span data-stu-id="64bcd-110">If you try to assign a nullable value type to a non-nullable value type without using the `??` operator, you will generate a compile-time error.</span></span> <span data-ttu-id="64bcd-111">Se você usar uma conversão e o tipo de valor anulável estiver atualmente indefinido, uma exceção `InvalidOperationException` será acionada.</span><span class="sxs-lookup"><span data-stu-id="64bcd-111">If you use a cast, and the nullable value type is currently undefined, an `InvalidOperationException` exception will be thrown.</span></span>

<span data-ttu-id="64bcd-112">Para obter mais informações, consulte [Tipos que permitem valor nulo](../../programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="64bcd-112">For more information, see [Nullable Types](../../programming-guide/nullable-types/index.md).</span></span>

<span data-ttu-id="64bcd-113">O resultado de um operador</span><span class="sxs-lookup"><span data-stu-id="64bcd-113">The result of a ??</span></span> <span data-ttu-id="64bcd-114">?? não será considerado constante, mesmo se os dois argumentos forem constantes.</span><span class="sxs-lookup"><span data-stu-id="64bcd-114">operator is not considered to be a constant even if both its arguments are constants.</span></span>

## <a name="example"></a><span data-ttu-id="64bcd-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="64bcd-115">Example</span></span>

[!code-csharp[csRefOperators#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#53)]

## <a name="c-language-specification"></a><span data-ttu-id="64bcd-116">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="64bcd-116">C# language specification</span></span>

<span data-ttu-id="64bcd-117">Para obter mais informações, veja [O operador coalescente nulo](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) na [Especificação da Linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="64bcd-117">For more information, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="64bcd-118">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="64bcd-118">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="64bcd-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64bcd-119">See also</span></span>

- [<span data-ttu-id="64bcd-120">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="64bcd-120">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="64bcd-121">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="64bcd-121">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="64bcd-122">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="64bcd-122">C# operators</span></span>](index.md)
- [<span data-ttu-id="64bcd-123">Tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="64bcd-123">Nullable Types</span></span>](../../programming-guide/nullable-types/index.md)
- [<span data-ttu-id="64bcd-124">O que exatamente “levantado” significa?</span><span class="sxs-lookup"><span data-stu-id="64bcd-124">What Exactly Does 'Lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)