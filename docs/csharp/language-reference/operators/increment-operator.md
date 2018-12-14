---
title: Operador ++ (Referência de C#)
ms.date: 11/26/2018
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
ms.openlocfilehash: b29f4f1ab00c0f8026f118cb72b090e3b728bfc5
ms.sourcegitcommit: 6ae7cdd0437a32884556dd4826ca90e957b7a4e3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/06/2018
ms.locfileid: "48030457"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="79155-102">Operador ++ (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="79155-102">++ Operator (C# Reference)</span></span>

<span data-ttu-id="79155-103">O operador de incremento unário `++` incrementa seu operando em 1.</span><span class="sxs-lookup"><span data-stu-id="79155-103">The unary increment operator `++` increments its operand by 1.</span></span> <span data-ttu-id="79155-104">Há duas formas de suporte: o operador de incremento pós-fixado, `x++`, e o operador de incremento de prefixo, `++x`.</span><span class="sxs-lookup"><span data-stu-id="79155-104">It's supported in two forms: the postfix increment operator, `x++`, and the prefix increment operator, `++x`.</span></span>

## <a name="postfix-increment-operator"></a><span data-ttu-id="79155-105">Operador de incremento pós-fixado</span><span class="sxs-lookup"><span data-stu-id="79155-105">Postfix increment operator</span></span>

<span data-ttu-id="79155-106">O resultado de `x++` é o valor de `x` *antes* da operação, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="79155-106">The result of `x++` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix increment](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PostfixIncrement)]

## <a name="prefix-increment-operator"></a><span data-ttu-id="79155-107">Operador de incremento de prefixo</span><span class="sxs-lookup"><span data-stu-id="79155-107">Prefix increment operator</span></span>

<span data-ttu-id="79155-108">O resultado de `++x` é o valor de `x` *após* a operação, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="79155-108">The result of `++x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix increment](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PrefixIncrement)]

## <a name="remarks"></a><span data-ttu-id="79155-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="79155-109">Remarks</span></span>

<span data-ttu-id="79155-110">O operador de incremento é predefinido para todos os [tipos integrais](../keywords/integral-types-table.md) (incluindo o tipo [char](../keywords/char.md)), [tipos de ponto flutuante](../keywords/floating-point-types-table.md) e qualquer tipo [enum](../keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="79155-110">The increment operator is predefined for all [integral types](../keywords/integral-types-table.md) (including the [char](../keywords/char.md) type), [floating-point types](../keywords/floating-point-types-table.md), and any [enum](../keywords/enum.md) type.</span></span>

<span data-ttu-id="79155-111">O operando do operador de incremento deve ser uma variável, um acesso à [propriedade](../../programming-guide/classes-and-structs/properties.md) ou um acesso ao [indexador](../../../csharp/programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="79155-111">An operand of the increment operator must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../../csharp/programming-guide/indexers/index.md) access.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="79155-112">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="79155-112">Operator overloadability</span></span>

<span data-ttu-id="79155-113">Tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) o operador `++`.</span><span class="sxs-lookup"><span data-stu-id="79155-113">User-defined types can [overload](../keywords/operator.md) the `++` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="79155-114">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="79155-114">C# language specification</span></span>

<span data-ttu-id="79155-115">Para saber mais, confira as seções [Operadores de incremento e de decremento pré-fixados](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators) e [Operadores de incremento e decremento de prefixo](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators) da [especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="79155-115">For more information, see the [Postfix increment and decrement operators](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators) and [Prefix increment and decrement operators](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="79155-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79155-116">See also</span></span>

- [<span data-ttu-id="79155-117">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="79155-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="79155-118">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="79155-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="79155-119">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="79155-119">C# Operators</span></span>](index.md)
- [<span data-ttu-id="79155-120">Operador --</span><span class="sxs-lookup"><span data-stu-id="79155-120">-- Operator</span></span>](decrement-operator.md)
- [<span data-ttu-id="79155-121">Como incrementar e diminuir ponteiros</span><span class="sxs-lookup"><span data-stu-id="79155-121">How to: increment and decrement pointers</span></span>](../../programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
