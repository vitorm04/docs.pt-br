---
description: 'Saiba mais sobre o tipo booliano interno em C #'
title: tipo bool-referência C#
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
- "true"
- "false"
- true_CSharpKeyword
- false_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 23e5bc34f1751b0a706c20dae340920239fcda9d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89126457"
---
# <a name="bool-c-reference"></a><span data-ttu-id="e9738-103">bool (referência C#)</span><span class="sxs-lookup"><span data-stu-id="e9738-103">bool (C# reference)</span></span>

<span data-ttu-id="e9738-104">A `bool` palavra-chave Type é um alias para o <xref:System.Boolean?displayProperty=nameWithType> tipo de estrutura .NET que representa um valor booliano, que pode ser `true` ou `false` .</span><span class="sxs-lookup"><span data-stu-id="e9738-104">The `bool` type keyword is an alias for the .NET <xref:System.Boolean?displayProperty=nameWithType> structure type that represents a Boolean value, which can be either `true` or `false`.</span></span>

<span data-ttu-id="e9738-105">Para executar operações lógicas com valores do `bool` tipo, use operadores [lógicos boolianos](../operators/boolean-logical-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="e9738-105">To perform logical operations with values of the `bool` type, use [Boolean logical](../operators/boolean-logical-operators.md) operators.</span></span> <span data-ttu-id="e9738-106">O `bool` tipo é o tipo de resultado dos operadores de [comparação](../operators/comparison-operators.md) e de [igualdade](../operators/equality-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="e9738-106">The `bool` type is the result type of [comparison](../operators/comparison-operators.md) and [equality](../operators/equality-operators.md) operators.</span></span> <span data-ttu-id="e9738-107">Uma `bool` expressão pode ser uma expressão condicional de controle nas [if](../keywords/if-else.md)instruções if [do](../keywords/do.md), do, [while](../keywords/while.md)e [for](../keywords/for.md) e no [operador `?:` condicional ](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="e9738-107">A `bool` expression can be a controlling conditional expression in the [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md), and [for](../keywords/for.md) statements and in the [conditional operator `?:`](../operators/conditional-operator.md).</span></span>

<span data-ttu-id="e9738-108">O valor padrão do `bool` tipo é `false` .</span><span class="sxs-lookup"><span data-stu-id="e9738-108">The default value of the `bool` type is `false`.</span></span>

## <a name="literals"></a><span data-ttu-id="e9738-109">Literais</span><span class="sxs-lookup"><span data-stu-id="e9738-109">Literals</span></span>

<span data-ttu-id="e9738-110">Você pode usar os `true` `false` literais e para inicializar uma `bool` variável ou para passar um `bool` valor:</span><span class="sxs-lookup"><span data-stu-id="e9738-110">You can use the `true` and `false` literals to initialize a `bool` variable or to pass a `bool` value:</span></span>

[!code-csharp-interactive[bool literals](snippets/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a><span data-ttu-id="e9738-111">Lógica booleana de três valores</span><span class="sxs-lookup"><span data-stu-id="e9738-111">Three-valued Boolean logic</span></span>

<span data-ttu-id="e9738-112">Use o `bool?` tipo anulável, se você precisar dar suporte à lógica de três valores, por exemplo, quando trabalhar com bancos de dados que dão suporte a um tipo booliano de três valores.</span><span class="sxs-lookup"><span data-stu-id="e9738-112">Use the nullable `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="e9738-113">Para os operandos `bool?`, os operadores `&` e `|` predefinidos oferecem suporte à lógica de três valores.</span><span class="sxs-lookup"><span data-stu-id="e9738-113">For the `bool?` operands, the predefined `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="e9738-114">Para obter mais informações, confira a seção [Operadores lógicos booleanos anuláveis](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) do artigo [Operadores lógicos boolianos](../operators/boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="e9738-114">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="e9738-115">Para obter mais informações sobre tipos de valor anulável, consulte [tipos de valor anulável](nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="e9738-115">For more information about nullable value types, see [Nullable value types](nullable-value-types.md).</span></span>

## <a name="conversions"></a><span data-ttu-id="e9738-116">Conversões</span><span class="sxs-lookup"><span data-stu-id="e9738-116">Conversions</span></span>

<span data-ttu-id="e9738-117">O C# fornece apenas duas conversões que envolvem o `bool` tipo.</span><span class="sxs-lookup"><span data-stu-id="e9738-117">C# provides only two conversions that involve the `bool` type.</span></span> <span data-ttu-id="e9738-118">Essas são uma conversão implícita para o tipo anulável correspondente `bool?` e uma conversão explícita do `bool?` tipo.</span><span class="sxs-lookup"><span data-stu-id="e9738-118">Those are an implicit conversion to the corresponding nullable `bool?` type and an explicit conversion from the `bool?` type.</span></span> <span data-ttu-id="e9738-119">No entanto, o .NET fornece métodos adicionais que você pode usar para converter de ou para o `bool` tipo.</span><span class="sxs-lookup"><span data-stu-id="e9738-119">However, .NET provides additional methods that you can use to convert to or from the `bool` type.</span></span> <span data-ttu-id="e9738-120">Para obter mais informações, consulte a seção [convertendo de valores booleanos](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) da <xref:System.Boolean?displayProperty=nameWithType> página de referência da API.</span><span class="sxs-lookup"><span data-stu-id="e9738-120">For more information, see the [Converting to and from Boolean values](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) section of the <xref:System.Boolean?displayProperty=nameWithType> API reference page.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e9738-121">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e9738-121">C# language specification</span></span>

<span data-ttu-id="e9738-122">Para obter mais informações, consulte [a seção tipo bool](~/_csharplang/spec/types.md#the-bool-type) da [especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="e9738-122">For more information, see [The bool type](~/_csharplang/spec/types.md#the-bool-type) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e9738-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="e9738-123">See also</span></span>

- [<span data-ttu-id="e9738-124">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="e9738-124">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e9738-125">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="e9738-125">Value types</span></span>](value-types.md)
- [<span data-ttu-id="e9738-126">operadores true e false</span><span class="sxs-lookup"><span data-stu-id="e9738-126">true and false operators</span></span>](../operators/true-false-operators.md)
