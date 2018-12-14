---
title: Operador -- (Referência de C#)
ms.date: 11/26/2018
f1_keywords:
- --_CSharpKeyword
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
ms.openlocfilehash: 0858321d6fe192a55bc548f169c558542238a981
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153326"
---
# <a name="---operator-c-reference"></a><span data-ttu-id="41178-102">Operador -- (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="41178-102">-- Operator (C# Reference)</span></span>

<span data-ttu-id="41178-103">O operador de decremento unário `--` decrementa o operando em 1.</span><span class="sxs-lookup"><span data-stu-id="41178-103">The unary decrement operator `--` decrements its operand by 1.</span></span> <span data-ttu-id="41178-104">Há duas formas de suporte: o operador de decremento pós-fixado, `x--`, e o operador de decremento de prefixo, `--x`.</span><span class="sxs-lookup"><span data-stu-id="41178-104">It's supported in two forms: the postfix decrement operator, `x--`, and the prefix decrement operator, `--x`.</span></span>

## <a name="postfix-decrement-operator"></a><span data-ttu-id="41178-105">Operador de decremento pós-fixado</span><span class="sxs-lookup"><span data-stu-id="41178-105">Postfix decrement operator</span></span>

<span data-ttu-id="41178-106">O resultado de `x--` é o valor de `x` *antes* da operação, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="41178-106">The result of `x--` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix decrement](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PostfixDecrement)]

## <a name="prefix-decrement-operator"></a><span data-ttu-id="41178-107">Operador de decremento de prefixo</span><span class="sxs-lookup"><span data-stu-id="41178-107">Prefix decrement operator</span></span>

<span data-ttu-id="41178-108">O resultado de `--x` é o valor de `x` *após* a operação, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="41178-108">The result of `--x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix decrement](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PrefixDecrement)]

## <a name="remarks"></a><span data-ttu-id="41178-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="41178-109">Remarks</span></span>

<span data-ttu-id="41178-110">O operador de decremento é predefinido para todos os [tipos integrais](../keywords/integral-types-table.md) (incluindo o tipo [char](../keywords/char.md)), [tipos de ponto flutuante](../keywords/floating-point-types-table.md) e qualquer tipo [enum](../keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="41178-110">The decrement operator is predefined for all [integral types](../keywords/integral-types-table.md) (including the [char](../keywords/char.md) type), [floating-point types](../keywords/floating-point-types-table.md), and any [enum](../keywords/enum.md) type.</span></span>

<span data-ttu-id="41178-111">O operando do operador de decremento deve ser uma variável, um acesso à [propriedade](../../programming-guide/classes-and-structs/properties.md) ou um acesso ao [indexador](../../../csharp/programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="41178-111">An operand of the decrement operator must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../../csharp/programming-guide/indexers/index.md) access.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="41178-112">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="41178-112">Operator overloadability</span></span>

<span data-ttu-id="41178-113">Tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) o operador `--`.</span><span class="sxs-lookup"><span data-stu-id="41178-113">User-defined types can [overload](../keywords/operator.md) the `--` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="41178-114">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="41178-114">C# language specification</span></span>

<span data-ttu-id="41178-115">Para obter mais informações, confira as seções [operadores de incremento e de decremento pré-fixados](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators) e [operadores de incremento e decremento de prefixo](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators) da [Especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="41178-115">For more information, see the [Postfix increment and decrement operators](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators) and [Prefix increment and decrement operators](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="41178-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41178-116">See also</span></span>

- [<span data-ttu-id="41178-117">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="41178-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="41178-118">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="41178-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="41178-119">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="41178-119">C# Operators</span></span>](index.md)
- [<span data-ttu-id="41178-120">Operador ++</span><span class="sxs-lookup"><span data-stu-id="41178-120">++ Operator</span></span>](increment-operator.md)
- [<span data-ttu-id="41178-121">Como incrementar e diminuir ponteiros</span><span class="sxs-lookup"><span data-stu-id="41178-121">How to: increment and decrement pointers</span></span>](../../programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
