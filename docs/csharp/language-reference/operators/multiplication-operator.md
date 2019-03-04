---
title: '* Operador – referência do C#'
ms.custom: seodec18
ms.date: 02/26/2019
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: a5e120d26614f1e38cc2f2db02949552140b594e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977338"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="e7001-102">Operador \* (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="e7001-102">\* operator (C# Reference)</span></span>

<span data-ttu-id="e7001-103">O operador `*` é compatível em duas formas: um operador de indireção de ponteiro unário ou um operador de multiplicação binário.</span><span class="sxs-lookup"><span data-stu-id="e7001-103">The `*` operator is supported in two forms: a unary pointer indirection operator or a binary multiplication operator.</span></span>

## <a name="pointer-indirection-operator"></a><span data-ttu-id="e7001-104">Operador de indireção de ponteiro</span><span class="sxs-lookup"><span data-stu-id="e7001-104">Pointer indirection operator</span></span>

<span data-ttu-id="e7001-105">Use o operador `*` unário para obter a variável para a qual aponta o operando de um tipo de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="e7001-105">Use the unary `*` operator to obtain the variable to which an operand of a pointer type points.</span></span> <span data-ttu-id="e7001-106">Veja mais informações em [Como obter o valor de uma variável de ponteiro](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-value-of-a-pointer-variable.md).</span><span class="sxs-lookup"><span data-stu-id="e7001-106">For more information, see [How to: obtain the value of a pointer variable](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-value-of-a-pointer-variable.md).</span></span>

<span data-ttu-id="e7001-107">O operador de indireção de ponteiro `*` requer o contexto [não seguro](../keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="e7001-107">The pointer indirection operator `*` requires [unsafe](../keywords/unsafe.md) context.</span></span>

## <a name="multiplication-operator"></a><span data-ttu-id="e7001-108">Operador de multiplicação</span><span class="sxs-lookup"><span data-stu-id="e7001-108">Multiplication operator</span></span>

<span data-ttu-id="e7001-109">Para tipos numéricos, o operador `*` calcula o produto dos operandos:</span><span class="sxs-lookup"><span data-stu-id="e7001-109">For numeric types, the `*` operator computes the product of its operands:</span></span>

[!code-csharp-interactive[multiplication](~/samples/snippets/csharp/language-reference/operators/MultiplicationExamples.cs#Multiply)]

## <a name="operator-overloadability"></a><span data-ttu-id="e7001-110">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="e7001-110">Operator overloadability</span></span>

<span data-ttu-id="e7001-111">Os tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) um operador `*` binário.</span><span class="sxs-lookup"><span data-stu-id="e7001-111">User-defined types can [overload](../keywords/operator.md) a binary `*` operator.</span></span> <span data-ttu-id="e7001-112">Quando um operador `*` binário é sobrecarregado, o [operador de atribuição de multiplicação](multiplication-assignment-operator.md) `*=` também é implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="e7001-112">When a binary `*` operator is overloaded, the [multiplication assignment operator](multiplication-assignment-operator.md) `*=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e7001-113">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e7001-113">C# language specification</span></span>

<span data-ttu-id="e7001-114">Veja mais informações, nas seções [Indireção de ponteiro](~/_csharplang/spec/unsafe-code.md#pointer-indirection) e [Operador de multiplicação](~/_csharplang/spec/expressions.md#multiplication-operator) da [ especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="e7001-114">For more information, see the [Pointer indirection](~/_csharplang/spec/unsafe-code.md#pointer-indirection) and [Multiplication operator](~/_csharplang/spec/expressions.md#multiplication-operator) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e7001-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7001-115">See also</span></span>

- [<span data-ttu-id="e7001-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="e7001-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e7001-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e7001-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e7001-118">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="e7001-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="e7001-119">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="e7001-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)