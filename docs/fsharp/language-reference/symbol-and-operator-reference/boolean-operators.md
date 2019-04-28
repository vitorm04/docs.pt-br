---
title: Operadores boolianos
description: Saiba mais sobre os operadores boolianos que estão disponíveis no F# linguagem de programação.
ms.date: 05/16/2016
ms.openlocfilehash: 5353b6ec6a0bd610f3446761a1d28f01f0403302
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925808"
---
# <a name="boolean-operators"></a><span data-ttu-id="19d90-103">Operadores boolianos</span><span class="sxs-lookup"><span data-stu-id="19d90-103">Boolean Operators</span></span>

<span data-ttu-id="19d90-104">Este tópico descreve o suporte para operadores boolianos no F# idioma.</span><span class="sxs-lookup"><span data-stu-id="19d90-104">This topic describes the support for Boolean operators in the F# language.</span></span>

## <a name="summary-of-boolean-operators"></a><span data-ttu-id="19d90-105">Resumo de operadores boolianos</span><span class="sxs-lookup"><span data-stu-id="19d90-105">Summary of Boolean Operators</span></span>

<span data-ttu-id="19d90-106">A tabela a seguir resume os operadores boolianos que estão disponíveis no F# idioma.</span><span class="sxs-lookup"><span data-stu-id="19d90-106">The following table summarizes the Boolean operators that are available in the F# language.</span></span> <span data-ttu-id="19d90-107">O único tipo com suporte desses operadores é o `bool` tipo.</span><span class="sxs-lookup"><span data-stu-id="19d90-107">The only type supported by these operators is the `bool` type.</span></span>

|<span data-ttu-id="19d90-108">Operador</span><span class="sxs-lookup"><span data-stu-id="19d90-108">Operator</span></span>|<span data-ttu-id="19d90-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="19d90-109">Description</span></span>|
|--------|-----------|
|`not`|<span data-ttu-id="19d90-110">Boleana</span><span class="sxs-lookup"><span data-stu-id="19d90-110">Boolean negation</span></span>|
|<code>&#124;&#124;</code>|<span data-ttu-id="19d90-111">Booliano OR</span><span class="sxs-lookup"><span data-stu-id="19d90-111">Boolean OR</span></span>|
|`&&`|<span data-ttu-id="19d90-112">Booliano AND</span><span class="sxs-lookup"><span data-stu-id="19d90-112">Boolean AND</span></span>|

<span data-ttu-id="19d90-113">Executam o booliano e e/ou operadores *avaliação curto-circuito*, ou seja, eles avaliar a expressão à direita do operador somente quando for necessário determinar o resultado geral da expressão.</span><span class="sxs-lookup"><span data-stu-id="19d90-113">The Boolean AND and OR operators perform *short-circuit evaluation*, that is, they evaluate the expression on the right of the operator only when it is necessary to determine the overall result of the expression.</span></span> <span data-ttu-id="19d90-114">A segunda expressão do `&&` operador é avaliado somente se a primeira expressão é avaliada como `true`; a segunda expressão do `||` operador é avaliado somente se a primeira expressão é avaliada como `false`.</span><span class="sxs-lookup"><span data-stu-id="19d90-114">The second expression of the `&&` operator is evaluated only if the first expression evaluates to `true`; the second expression of the `||` operator is evaluated only if the first expression evaluates to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="19d90-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19d90-115">See also</span></span>

- [<span data-ttu-id="19d90-116">Operadores Bit a Bit</span><span class="sxs-lookup"><span data-stu-id="19d90-116">Bitwise Operators</span></span>](bitwise-operators.md)
- [<span data-ttu-id="19d90-117">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="19d90-117">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="19d90-118">Referência de Símbolos e Operadores</span><span class="sxs-lookup"><span data-stu-id="19d90-118">Symbol and Operator Reference</span></span>](index.md)