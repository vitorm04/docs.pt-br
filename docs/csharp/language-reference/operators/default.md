---
title: expressões de valor padrão-referência C#
description: Usar as expressões de valor padrão para obter o valor padrão de um tipo
ms.date: 03/13/2020
f1_keywords:
- default_CSharpKeyword
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 92ad8e919567e1f9f57e6875d53c4055eb960829
ms.sourcegitcommit: e078b7540a8293ca1b604c9c0da1ff1506f0170b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2020
ms.locfileid: "91997650"
---
# <a name="default-value-expressions-c-reference"></a><span data-ttu-id="a2d4e-103">expressões de valor padrão (referência C#)</span><span class="sxs-lookup"><span data-stu-id="a2d4e-103">default value expressions (C# reference)</span></span>

<span data-ttu-id="a2d4e-104">Uma expressão de valor padrão produz o [valor padrão](../builtin-types/default-values.md) de um tipo.</span><span class="sxs-lookup"><span data-stu-id="a2d4e-104">A default value expression produces the [default value](../builtin-types/default-values.md) of a type.</span></span> <span data-ttu-id="a2d4e-105">Há dois tipos de expressões de valor padrão: a chamada de [operador padrão](#default-operator) e um [literal padrão](#default-literal).</span><span class="sxs-lookup"><span data-stu-id="a2d4e-105">There are two kinds of default value expressions: the [default operator](#default-operator) call and a [default literal](#default-literal).</span></span>

<span data-ttu-id="a2d4e-106">Você também usa a `default` palavra-chave como o rótulo de caso padrão dentro de uma [ `switch` instrução](../keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="a2d4e-106">You also use the `default` keyword as the default case label within a [`switch` statement](../keywords/switch.md).</span></span>

## <a name="default-operator"></a><span data-ttu-id="a2d4e-107">operador default</span><span class="sxs-lookup"><span data-stu-id="a2d4e-107">default operator</span></span>

<span data-ttu-id="a2d4e-108">O argumento do operador `default` deve ser o nome de um tipo ou um parâmetro de tipo, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="a2d4e-108">The argument to the `default` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[default of T](snippets/shared/DefaultOperator.cs#WithOperand)]

## <a name="default-literal"></a><span data-ttu-id="a2d4e-109">literal padrão</span><span class="sxs-lookup"><span data-stu-id="a2d4e-109">default literal</span></span>

<span data-ttu-id="a2d4e-110">A partir do C# 7,1, você pode usar o literal `default` para produzir o valor padrão de um tipo quando o compilador pode inferir o tipo de expressão.</span><span class="sxs-lookup"><span data-stu-id="a2d4e-110">Beginning with C# 7.1, you can use the `default` literal to produce the default value of a type when the compiler can infer the expression type.</span></span> <span data-ttu-id="a2d4e-111">A expressão literal `default` produz o mesmo valor que a expressão `default(T)`, em que `T` é o tipo inferido.</span><span class="sxs-lookup"><span data-stu-id="a2d4e-111">The `default` literal expression produces the same value as the `default(T)` expression where `T` is the inferred type.</span></span> <span data-ttu-id="a2d4e-112">Você pode usar o literal `default` em qualquer um dos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="a2d4e-112">You can use the `default` literal in any of the following cases:</span></span>

- <span data-ttu-id="a2d4e-113">Na atribuição ou inicialização de uma variável.</span><span class="sxs-lookup"><span data-stu-id="a2d4e-113">In the assignment or initialization of a variable.</span></span>
- <span data-ttu-id="a2d4e-114">Na declaração do valor padrão para um parâmetro de [método opcional](../../methods.md#optional-parameters-and-arguments).</span><span class="sxs-lookup"><span data-stu-id="a2d4e-114">In the declaration of the default value for an [optional method parameter](../../methods.md#optional-parameters-and-arguments).</span></span>
- <span data-ttu-id="a2d4e-115">Em uma chamada de método para fornecer um valor de argumento.</span><span class="sxs-lookup"><span data-stu-id="a2d4e-115">In a method call to provide an argument value.</span></span>
- <span data-ttu-id="a2d4e-116">Em uma [ `return` instrução](../keywords/return.md) ou como uma expressão em um [membro expression-apto para](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="a2d4e-116">In a [`return` statement](../keywords/return.md) or as an expression in an [expression-bodied member](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

<span data-ttu-id="a2d4e-117">O exemplo a seguir mostra o uso do literal `default`:</span><span class="sxs-lookup"><span data-stu-id="a2d4e-117">The following example shows the usage of the `default` literal:</span></span>

[!code-csharp-interactive[default literal](snippets/shared/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a><span data-ttu-id="a2d4e-118">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="a2d4e-118">C# language specification</span></span>

<span data-ttu-id="a2d4e-119">Para saber mais, confira a seção [Expressões de valor padrão](~/_csharplang/spec/expressions.md#default-value-expressions) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="a2d4e-119">For more information, see the [Default value expressions](~/_csharplang/spec/expressions.md#default-value-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="a2d4e-120">Para obter mais informações sobre o literal `default`, confira a [nota da proposta do recurso](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span><span class="sxs-lookup"><span data-stu-id="a2d4e-120">For more information about the `default` literal, see the [feature proposal note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a2d4e-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="a2d4e-121">See also</span></span>

- [<span data-ttu-id="a2d4e-122">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="a2d4e-122">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a2d4e-123">Operadores e expressões C#</span><span class="sxs-lookup"><span data-stu-id="a2d4e-123">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="a2d4e-124">Valores padrão de tipos C#</span><span class="sxs-lookup"><span data-stu-id="a2d4e-124">Default values of C# types</span></span>](../builtin-types/default-values.md)
- [<span data-ttu-id="a2d4e-125">Generics in .NET (Genéricos no .NET)</span><span class="sxs-lookup"><span data-stu-id="a2d4e-125">Generics in .NET</span></span>](../../../standard/generics/index.md)
