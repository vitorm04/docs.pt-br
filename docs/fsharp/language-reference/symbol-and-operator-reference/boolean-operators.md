---
title: Operadores boolianos (F#)
description: 'Saiba mais sobre os operadores boolianos que estão disponíveis na linguagem de programação F #.'
ms.date: 05/16/2016
ms.openlocfilehash: faa181090efa7c4064a30b42d83afa4888e98b82
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44364346"
---
# <a name="boolean-operators"></a><span data-ttu-id="776c5-103">Operadores boolianos</span><span class="sxs-lookup"><span data-stu-id="776c5-103">Boolean Operators</span></span>

<span data-ttu-id="776c5-104">Este tópico descreve o suporte para operadores boolianos na linguagem F #.</span><span class="sxs-lookup"><span data-stu-id="776c5-104">This topic describes the support for Boolean operators in the F# language.</span></span>

## <a name="summary-of-boolean-operators"></a><span data-ttu-id="776c5-105">Resumo de operadores boolianos</span><span class="sxs-lookup"><span data-stu-id="776c5-105">Summary of Boolean Operators</span></span>

<span data-ttu-id="776c5-106">A tabela a seguir resume os operadores boolianos que estão disponíveis na linguagem F #.</span><span class="sxs-lookup"><span data-stu-id="776c5-106">The following table summarizes the Boolean operators that are available in the F# language.</span></span> <span data-ttu-id="776c5-107">O único tipo com suporte desses operadores é o `bool` tipo.</span><span class="sxs-lookup"><span data-stu-id="776c5-107">The only type supported by these operators is the `bool` type.</span></span>

|<span data-ttu-id="776c5-108">Operador</span><span class="sxs-lookup"><span data-stu-id="776c5-108">Operator</span></span>|<span data-ttu-id="776c5-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="776c5-109">Description</span></span>|
|--------|-----------|
|`not`|<span data-ttu-id="776c5-110">Boleana</span><span class="sxs-lookup"><span data-stu-id="776c5-110">Boolean negation</span></span>|
|<code>&#124;&#124;</code>|<span data-ttu-id="776c5-111">Booliano OR</span><span class="sxs-lookup"><span data-stu-id="776c5-111">Boolean OR</span></span>|
|`&&`|<span data-ttu-id="776c5-112">Booliano AND</span><span class="sxs-lookup"><span data-stu-id="776c5-112">Boolean AND</span></span>|

<span data-ttu-id="776c5-113">Executam o booliano e e/ou operadores *avaliação curto-circuito*, ou seja, eles avaliar a expressão à direita do operador somente quando for necessário determinar o resultado geral da expressão.</span><span class="sxs-lookup"><span data-stu-id="776c5-113">The Boolean AND and OR operators perform *short-circuit evaluation*, that is, they evaluate the expression on the right of the operator only when it is necessary to determine the overall result of the expression.</span></span> <span data-ttu-id="776c5-114">A segunda expressão do `&&` operador é avaliado somente se a primeira expressão é avaliada como `true`; a segunda expressão do `||` operador é avaliado somente se a primeira expressão é avaliada como `false`.</span><span class="sxs-lookup"><span data-stu-id="776c5-114">The second expression of the `&&` operator is evaluated only if the first expression evaluates to `true`; the second expression of the `||` operator is evaluated only if the first expression evaluates to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="776c5-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="776c5-115">See also</span></span>

- [<span data-ttu-id="776c5-116">Operadores Bit a Bit</span><span class="sxs-lookup"><span data-stu-id="776c5-116">Bitwise Operators</span></span>](bitwise-operators.md)
- [<span data-ttu-id="776c5-117">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="776c5-117">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="776c5-118">Referência de Símbolos e Operadores</span><span class="sxs-lookup"><span data-stu-id="776c5-118">Symbol and Operator Reference</span></span>](index.md)
