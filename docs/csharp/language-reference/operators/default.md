---
title: Operador padrão – Referência do C#
description: Usar o operador padrão para produzir o valor padrão de um tipo
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 744bdf1ec683ef32bba508c260590c0ed4c6e987
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712709"
---
# <a name="default-operator-c-reference"></a><span data-ttu-id="806da-103">operador padrão (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="806da-103">default operator (C# reference)</span></span>

<span data-ttu-id="806da-104">O operador `default` produz o [valor padrão](../keywords/default-values-table.md) de um tipo.</span><span class="sxs-lookup"><span data-stu-id="806da-104">The `default` operator produces the [default value](../keywords/default-values-table.md) of a type.</span></span> <span data-ttu-id="806da-105">O argumento para o operador `default` deve ser o nome ou um parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="806da-105">The argument to the `default` operator must be the name of a type or a type parameter.</span></span>

<span data-ttu-id="806da-106">O exemplo a seguir mostra o uso do operador `default`:</span><span class="sxs-lookup"><span data-stu-id="806da-106">The following example shows the usage of the `default` operator:</span></span>

[!code-csharp-interactive[default of T](~/samples/csharp/language-reference/operators/DefaultOperator.cs#WithOperand)]

<span data-ttu-id="806da-107">Você também usa a palavra-chave `default` como o rótulo de caso padrão em uma [instrução`switch`](../keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="806da-107">You also use the `default` keyword as the default case label within a [`switch` statement](../keywords/switch.md).</span></span>

## <a name="default-literal"></a><span data-ttu-id="806da-108">literal padrão</span><span class="sxs-lookup"><span data-stu-id="806da-108">default literal</span></span>

<span data-ttu-id="806da-109">A partir do C# 7,1, você pode usar o literal `default` para produzir o valor padrão de um tipo quando o compilador pode inferir o tipo de expressão.</span><span class="sxs-lookup"><span data-stu-id="806da-109">Beginning with C# 7.1, you can use the `default` literal to produce the default value of a type when the compiler can infer the expression type.</span></span> <span data-ttu-id="806da-110">A expressão literal `default` produz o mesmo valor que a expressão `default(T)`, em que `T` é o tipo inferido.</span><span class="sxs-lookup"><span data-stu-id="806da-110">The `default` literal expression produces the same value as the `default(T)` expression where `T` is the inferred type.</span></span> <span data-ttu-id="806da-111">Você pode usar o literal `default` em qualquer um dos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="806da-111">You can use the `default` literal in any of the following cases:</span></span>

- <span data-ttu-id="806da-112">Na atribuição ou inicialização de uma variável.</span><span class="sxs-lookup"><span data-stu-id="806da-112">In the assignment or initialization of a variable.</span></span>
- <span data-ttu-id="806da-113">Na declaração do valor padrão para um parâmetro de [método opcional](../../methods.md#optional-parameters-and-arguments).</span><span class="sxs-lookup"><span data-stu-id="806da-113">In the declaration of the default value for an [optional method parameter](../../methods.md#optional-parameters-and-arguments).</span></span>
- <span data-ttu-id="806da-114">Em uma chamada de método para fornecer um valor de argumento.</span><span class="sxs-lookup"><span data-stu-id="806da-114">In a method call to provide an argument value.</span></span>
- <span data-ttu-id="806da-115">Em uma [instrução`return`](../keywords/return.md) ou como uma expressão em um [membro expression-apto para](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="806da-115">In a [`return` statement](../keywords/return.md) or as an expression in an [expression-bodied member](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

<span data-ttu-id="806da-116">O exemplo a seguir mostra o uso do literal `default`:</span><span class="sxs-lookup"><span data-stu-id="806da-116">The following example shows the usage of the `default` literal:</span></span>

[!code-csharp-interactive[default literal](~/samples/csharp/language-reference/operators/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a><span data-ttu-id="806da-117">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="806da-117">C# language specification</span></span>

<span data-ttu-id="806da-118">Para saber mais, confira a seção [Expressões de valor padrão](~/_csharplang/spec/expressions.md#default-value-expressions) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="806da-118">For more information, see the [Default value expressions](~/_csharplang/spec/expressions.md#default-value-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="806da-119">Para obter mais informações sobre o literal `default`, confira a [nota da proposta do recurso](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span><span class="sxs-lookup"><span data-stu-id="806da-119">For more information about the `default` literal, see the [feature proposal note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="806da-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="806da-120">See also</span></span>

- [<span data-ttu-id="806da-121">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="806da-121">C# reference</span></span>](../index.md)
- [<span data-ttu-id="806da-122">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="806da-122">C# operators</span></span>](index.md)
- [<span data-ttu-id="806da-123">Tabela de valores padrão</span><span class="sxs-lookup"><span data-stu-id="806da-123">Default values table</span></span>](../keywords/default-values-table.md)
- [<span data-ttu-id="806da-124">Genéricos no .NET</span><span class="sxs-lookup"><span data-stu-id="806da-124">Generics in .NET</span></span>](../../../standard/generics/index.md)
