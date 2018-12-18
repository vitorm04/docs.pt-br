---
title: Operador ~ – Referência de C#
ms.custom: seodec18
ms.date: 11/05/2018
f1_keywords:
- ~_CSharpKeyword
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
ms.openlocfilehash: 57e5baee423c0b5d9292d0ad4cbf909646eb3a38
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235707"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="87f0d-102">Operador ~ (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="87f0d-102">~ Operator (C# Reference)</span></span>

<span data-ttu-id="87f0d-103">O operador de complemento bit a bit `~` é um operador unário que produz um complemento bit a bit de seu operando por meio da inversão de cada bit.</span><span class="sxs-lookup"><span data-stu-id="87f0d-103">The bitwise complement operator `~` is a unary operator that produces a bitwise complement of its operand by reversing each bit.</span></span> <span data-ttu-id="87f0d-104">Todos os tipos de inteiros dão suporte ao operador `~`.</span><span class="sxs-lookup"><span data-stu-id="87f0d-104">All integer types support the `~` operator.</span></span>

> [!NOTE]
> <span data-ttu-id="87f0d-105">O símbolo `~` também é usado para declarar finalizadores.</span><span class="sxs-lookup"><span data-stu-id="87f0d-105">The `~` symbol is also used to declare finalizers.</span></span> <span data-ttu-id="87f0d-106">Para mais informações, consulte [Finalizadores](../../programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="87f0d-106">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span></span>

<span data-ttu-id="87f0d-107">O exemplo a seguir demonstra o uso do operador `~`:</span><span class="sxs-lookup"><span data-stu-id="87f0d-107">The following example demonstrates the usage of the `~` operator:</span></span>

[!code-csharp-interactive[bitwise NOT](~/samples/snippets/csharp/language-reference/operators/BitwiseComplementExamples.cs#Example)]

> [!NOTE]
> <span data-ttu-id="87f0d-108">O exemplo anterior usa os literais binários [introduzidos no C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) e [aprimorados no C#7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span><span class="sxs-lookup"><span data-stu-id="87f0d-108">The preceding example uses the binary literals [introduced in C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) and [enhanced  in C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="87f0d-109">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="87f0d-109">Operator overloadability</span></span>

<span data-ttu-id="87f0d-110">Tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) o operador `~`.</span><span class="sxs-lookup"><span data-stu-id="87f0d-110">User-defined types can [overload](../keywords/operator.md) the `~` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="87f0d-111">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="87f0d-111">C# language specification</span></span>

<span data-ttu-id="87f0d-112">Para saber mais, confira a seção [Operador condicional complementar bit a bit](~/_csharplang/spec/expressions.md#bitwise-complement-operator) na [Especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="87f0d-112">For more information, see the [Bitwise complement operator](~/_csharplang/spec/expressions.md#bitwise-complement-operator) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="87f0d-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87f0d-113">See also</span></span>

- [<span data-ttu-id="87f0d-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="87f0d-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="87f0d-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="87f0d-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="87f0d-116">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="87f0d-116">C# Operators</span></span>](index.md)
- [<span data-ttu-id="87f0d-117">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="87f0d-117">Finalizers</span></span>](../../programming-guide/classes-and-structs/destructors.md)
- [<span data-ttu-id="87f0d-118">Operador &</span><span class="sxs-lookup"><span data-stu-id="87f0d-118">& operator</span></span>](and-operator.md)
- [<span data-ttu-id="87f0d-119">Operador |</span><span class="sxs-lookup"><span data-stu-id="87f0d-119">| operator</span></span>](or-operator.md)
- [<span data-ttu-id="87f0d-120">Operador ^</span><span class="sxs-lookup"><span data-stu-id="87f0d-120">^ operator</span></span>](xor-operator.md)
