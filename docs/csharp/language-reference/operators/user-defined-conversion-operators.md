---
title: Operadores de conversão definidos pelo usuário – Referência de C#
description: Saiba como definir conversões de tipo implícitas e explícitas personalizadas em C#.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: 8788883a6c60032de2ffab658fcf2721654fc6f7
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566669"
---
# <a name="user-defined-conversion-operators-c-reference"></a><span data-ttu-id="d9694-103">Operadores de conversão definidos pelo usuário (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="d9694-103">User-defined conversion operators (C# reference)</span></span>

<span data-ttu-id="d9694-104">Um tipo definido pelo usuário pode definir uma conversão implícita ou explícita personalizada de outro tipo ou para outro.</span><span class="sxs-lookup"><span data-stu-id="d9694-104">A user-defined type can define a custom implicit or explicit conversion from or to another type.</span></span>

<span data-ttu-id="d9694-105">Conversões implícitas não requerem que uma sintaxe especial seja invocada e podem ocorrer em uma variedade de situações, por exemplo, em atribuições e invocações de método.</span><span class="sxs-lookup"><span data-stu-id="d9694-105">Implicit conversions don't require special syntax to be invoked and can occur in a variety of situations, for example, in assignments and methods invocations.</span></span> <span data-ttu-id="d9694-106">Conversões implícitas em C# predefinidas sempre têm êxito e nunca geram uma exceção ou perdem informações.</span><span class="sxs-lookup"><span data-stu-id="d9694-106">Predefined C# implicit conversions always succeed and never throw an exception or lose information.</span></span> <span data-ttu-id="d9694-107">Conversões implícitas definidas pelo usuário devem se comportam dessa forma também.</span><span class="sxs-lookup"><span data-stu-id="d9694-107">User-defined implicit conversions should behave in that way as well.</span></span> <span data-ttu-id="d9694-108">Se uma conversão personalizada puder gerar uma exceção ou perder informações, defina-a como uma conversão explícita.</span><span class="sxs-lookup"><span data-stu-id="d9694-108">If a custom conversion can throw an exception or lose information, define it as an explicit conversion.</span></span>

<span data-ttu-id="d9694-109">Conversões definidas pelo usuário não são consideradas pelos operadores [is](type-testing-and-cast.md#is-operator) e [as](type-testing-and-cast.md#as-operator).</span><span class="sxs-lookup"><span data-stu-id="d9694-109">User-defined conversions are not considered by the [is](type-testing-and-cast.md#is-operator) and [as](type-testing-and-cast.md#as-operator) operators.</span></span> <span data-ttu-id="d9694-110">Use o [operador cast ()](type-testing-and-cast.md#cast-operator-) para invocar uma conversão explícita definida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="d9694-110">Use the [cast operator ()](type-testing-and-cast.md#cast-operator-) to invoke a user-defined explicit conversion.</span></span>

<span data-ttu-id="d9694-111">Use `operator` e as palavras-chave `implicit` ou `explicit` para definir uma conversão implícita ou explícita, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="d9694-111">Use the `operator` and `implicit` or `explicit` keywords to define an implicit or explicit conversion, respectively.</span></span> <span data-ttu-id="d9694-112">O tipo que define uma conversão deve ser um tipo de origem ou e destino dessa conversão.</span><span class="sxs-lookup"><span data-stu-id="d9694-112">The type that defines a conversion must be either a source type or a target type of that conversion.</span></span> <span data-ttu-id="d9694-113">Uma conversão entre os dois tipos definidos pelo usuário pode ser definida em qualquer um dos dois tipos.</span><span class="sxs-lookup"><span data-stu-id="d9694-113">A conversion between two user-defined types can be defined in either of the two types.</span></span>

<span data-ttu-id="d9694-114">O exemplo a seguir demonstra como definir uma conversão implícita e explícita:</span><span class="sxs-lookup"><span data-stu-id="d9694-114">The following example demonstrates how to define an implicit and explicit conversion:</span></span>

[!code-csharp[implicit an explicit conversions](~/samples/csharp/language-reference/operators/UserDefinedConversions.cs)]

<span data-ttu-id="d9694-115">Use também a palavra-chave `operator` para sobrecarregar um operador C# predefinido.</span><span class="sxs-lookup"><span data-stu-id="d9694-115">You also use the `operator` keyword to overload a predefined C# operator.</span></span> <span data-ttu-id="d9694-116">Para obter mais informações, consulte [Sobrecarga de operador](operator-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="d9694-116">For more information, see [Operator overloading](operator-overloading.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d9694-117">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="d9694-117">C# language specification</span></span>

<span data-ttu-id="d9694-118">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="d9694-118">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="d9694-119">Operadores de conversão</span><span class="sxs-lookup"><span data-stu-id="d9694-119">Conversion operators</span></span>](~/_csharplang/spec/classes.md#conversion-operators)
- [<span data-ttu-id="d9694-120">Conversões Definidas pelo Usuário</span><span class="sxs-lookup"><span data-stu-id="d9694-120">User-defined conversions</span></span>](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [<span data-ttu-id="d9694-121">Conversões implícitas</span><span class="sxs-lookup"><span data-stu-id="d9694-121">Implicit conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-conversions)
- [<span data-ttu-id="d9694-122">Conversões explícitas</span><span class="sxs-lookup"><span data-stu-id="d9694-122">Explicit conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a><span data-ttu-id="d9694-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9694-123">See also</span></span>

- [<span data-ttu-id="d9694-124">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="d9694-124">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d9694-125">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="d9694-125">C# operators</span></span>](index.md)
- [<span data-ttu-id="d9694-126">Sobrecarga de operador</span><span class="sxs-lookup"><span data-stu-id="d9694-126">Operator overloading</span></span>](operator-overloading.md)
- [<span data-ttu-id="d9694-127">Operadores cast e teste de tipo</span><span class="sxs-lookup"><span data-stu-id="d9694-127">Type-testing and cast operators</span></span>](type-testing-and-cast.md)
- [<span data-ttu-id="d9694-128">Conversão e conversão de tipo</span><span class="sxs-lookup"><span data-stu-id="d9694-128">Casting and type conversion</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="d9694-129">Conversões explícitas encadeadas definidas pelo usuário em C#</span><span class="sxs-lookup"><span data-stu-id="d9694-129">Chained user-defined explicit conversions in C#</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
