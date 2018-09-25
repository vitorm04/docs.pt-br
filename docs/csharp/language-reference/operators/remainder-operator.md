---
title: Operador % (Referência de C#)
ms.date: 09/04/2018
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- remainder operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
ms.openlocfilehash: 9cd2f7ad3856feb34667686979c942ecb21887c2
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45645912"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="beb4e-102">Operador % (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="beb4e-102">% Operator (C# Reference)</span></span>

<span data-ttu-id="beb4e-103">O operador de resto `%` calcula o resto após dividir o primeiro operando pelo segundo.</span><span class="sxs-lookup"><span data-stu-id="beb4e-103">The remainder operator `%` computes the remainder after dividing its first operand by its second operand.</span></span> <span data-ttu-id="beb4e-104">Tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) o operador `%`.</span><span class="sxs-lookup"><span data-stu-id="beb4e-104">User-defined types can [overload](../keywords/operator.md) the `%` operator.</span></span> <span data-ttu-id="beb4e-105">Quando o `%` está sobrecarregado, o [operador de atribuição de resto](remainder-assignment-operator.md) `%=` também está implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="beb4e-105">When the `%` is overloaded, the [remainder assignment operator](remainder-assignment-operator.md) `%=` is also implicitly overloaded.</span></span>

<span data-ttu-id="beb4e-106">Todos os tipos numéricos são compatíveis com o operador de resto.</span><span class="sxs-lookup"><span data-stu-id="beb4e-106">All numeric types support the remainder operator.</span></span>

## <a name="integer-remainder"></a><span data-ttu-id="beb4e-107">Resto inteiro</span><span class="sxs-lookup"><span data-stu-id="beb4e-107">Integer remainder</span></span>
  
<span data-ttu-id="beb4e-108">Para os operandos inteiros, o resultado de `a % b` é o valor produzido por `a - (a / b) * b`.</span><span class="sxs-lookup"><span data-stu-id="beb4e-108">For the integer operands, the result of `a % b` is the value produced by `a - (a / b) * b`.</span></span> <span data-ttu-id="beb4e-109">O sinal do resto diferente de zero é o mesmo que o do primeiro operando, conforme mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="beb4e-109">The sign of the non-zero remainder is the same as that of the first operand, as the following example shows:</span></span>

[!code-csharp-interactive[integer remainder](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#1)]

## <a name="floating-point-remainder"></a><span data-ttu-id="beb4e-110">Resto de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="beb4e-110">Floating-point remainder</span></span>

<span data-ttu-id="beb4e-111">Para os operandos [float](../keywords/float.md) e [double](../keywords/double.md), o resultado de `x % y` para o `x` e `y` finitos é o valor `z` tal que</span><span class="sxs-lookup"><span data-stu-id="beb4e-111">For the [float](../keywords/float.md) and [double](../keywords/double.md) operands, the result of `x % y` for the finite `x` and `y` is the value `z` such that</span></span>

- <span data-ttu-id="beb4e-112">o sinal de `z`, se diferente de zero, é o mesmo que o sinal de `x`;</span><span class="sxs-lookup"><span data-stu-id="beb4e-112">the sign of `z`, if non-zero, is the same as the sign of `x`;</span></span>
- <span data-ttu-id="beb4e-113">o valor absoluto de `z` é o valor produzido por `|x| - n * |y|` em que `n` é o maior inteiro possível que é menor ou igual a `|x| / |y|` e `|x|` e `|y|` são os valores absolutos de `x` e `y`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="beb4e-113">the absolute value of `z` is the value produced by `|x| - n * |y|` where `n` is the largest possible integer that is less than or equal to `|x| / |y|` and `|x|` and `|y|` are the absolute values of `x` and `y`, respectively.</span></span>

<span data-ttu-id="beb4e-114">Para obter informações sobre o comportamento do operador `%` no caso de operandos não finitos, consulte a seção [Operador de resto](/dotnet/csharp/language-reference/language-specification/expressions#remainder-operator) da [Especificação da linguagem C#](/dotnet/csharp/language-reference/language-specification/index).</span><span class="sxs-lookup"><span data-stu-id="beb4e-114">For information about behavior of the `%` operator in case of non-finite operands, see the [Remainder operator](/dotnet/csharp/language-reference/language-specification/expressions#remainder-operator) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/index).</span></span>

> [!NOTE]
> <span data-ttu-id="beb4e-115">Esse método de calcular o resto é semelhante ao usado para operandos inteiros, mas é diferente do IEEE 754.</span><span class="sxs-lookup"><span data-stu-id="beb4e-115">This method of computing the remainder is analogous to that used for integer operands, but differs from the IEEE 754.</span></span> <span data-ttu-id="beb4e-116">Se precisar da operação de resto em conformidade com o IEEE 754, use o método <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="beb4e-116">If you need the remainder operation that complies with the IEEE 754, use the <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="beb4e-117">O exemplo a seguir demonstra o comportamento do operador de resto para os operandos `float` e `double`:</span><span class="sxs-lookup"><span data-stu-id="beb4e-117">The following example demonstrates the behavior of the remainder operator for `float` and `double` operands:</span></span>

[!code-csharp-interactive[float and double remainder](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#2)]

<span data-ttu-id="beb4e-118">Observe os erros de arredondamento que podem ser associados aos tipos de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="beb4e-118">Note the round-off errors that can be associated with the floating-point types.</span></span>

<span data-ttu-id="beb4e-119">Para os operandos [decimais](../keywords/decimal.md), o operador de resto `%` é equivalente ao [operador de resto](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) do tipo <xref:System.Decimal?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="beb4e-119">For the [decimal](../keywords/decimal.md) operands, the remainder operator `%` is equivalent to the [remainder operator](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) of the <xref:System.Decimal?displayProperty=nameWithType> type.</span></span>

## <a name="see-also"></a><span data-ttu-id="beb4e-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="beb4e-120">See also</span></span>

- [<span data-ttu-id="beb4e-121">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="beb4e-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="beb4e-122">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="beb4e-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="beb4e-123">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="beb4e-123">C# Operators</span></span>](index.md)
- <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType>
- <xref:System.Math.DivRem%2A?displayProperty=nameWithType>
