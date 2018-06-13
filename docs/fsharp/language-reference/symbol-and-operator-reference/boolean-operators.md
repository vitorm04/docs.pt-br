---
title: Operadores boolianos (F#)
description: 'Saiba mais sobre os operadores booleanos que estão disponíveis no F # linguagem de programação.'
ms.date: 05/16/2016
ms.openlocfilehash: f8516ceb531907400f98dc4226d2985d3119e9e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563422"
---
# <a name="boolean-operators"></a><span data-ttu-id="0bd27-103">Operadores boolianos</span><span class="sxs-lookup"><span data-stu-id="0bd27-103">Boolean Operators</span></span>

<span data-ttu-id="0bd27-104">Este tópico descreve o suporte para operadores boolianos na linguagem F #.</span><span class="sxs-lookup"><span data-stu-id="0bd27-104">This topic describes the support for Boolean operators in the F# language.</span></span>


## <a name="summary-of-boolean-operators"></a><span data-ttu-id="0bd27-105">Resumo de operadores boolianos</span><span class="sxs-lookup"><span data-stu-id="0bd27-105">Summary of Boolean Operators</span></span>
<span data-ttu-id="0bd27-106">A tabela a seguir resume os operadores booleanos que estão disponíveis na linguagem F #.</span><span class="sxs-lookup"><span data-stu-id="0bd27-106">The following table summarizes the Boolean operators that are available in the F# language.</span></span> <span data-ttu-id="0bd27-107">O único tipo com suporte desses operadores é o `bool` tipo.</span><span class="sxs-lookup"><span data-stu-id="0bd27-107">The only type supported by these operators is the `bool` type.</span></span>

|<span data-ttu-id="0bd27-108">Operador</span><span class="sxs-lookup"><span data-stu-id="0bd27-108">Operator</span></span>|<span data-ttu-id="0bd27-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="0bd27-109">Description</span></span>|
|--------|-----------|
|`not`|<span data-ttu-id="0bd27-110">Boleana</span><span class="sxs-lookup"><span data-stu-id="0bd27-110">Boolean negation</span></span>|
|<code>&#124;&#124;</code>|<span data-ttu-id="0bd27-111">Booliano OR</span><span class="sxs-lookup"><span data-stu-id="0bd27-111">Boolean OR</span></span>|
|`&&`|<span data-ttu-id="0bd27-112">Boolean e</span><span class="sxs-lookup"><span data-stu-id="0bd27-112">Boolean AND</span></span>|

<span data-ttu-id="0bd27-113">Executam o Boolean e e/ou operadores *avaliação de curto-circuito*, ou seja, elas avaliam a expressão à direita do operador somente quando é necessário determinar o resultado geral da expressão.</span><span class="sxs-lookup"><span data-stu-id="0bd27-113">The Boolean AND and OR operators perform *short-circuit evaluation*, that is, they evaluate the expression on the right of the operator only when it is necessary to determine the overall result of the expression.</span></span> <span data-ttu-id="0bd27-114">A segunda expressão do `&&` operador é avaliado apenas se a primeira expressão for avaliada como `true`; a segunda expressão do `||` operador é avaliado apenas se a primeira expressão for avaliada como `false`.</span><span class="sxs-lookup"><span data-stu-id="0bd27-114">The second expression of the `&&` operator is evaluated only if the first expression evaluates to `true`; the second expression of the `||` operator is evaluated only if the first expression evaluates to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="0bd27-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0bd27-115">See Also</span></span>
[<span data-ttu-id="0bd27-116">Operadores Bit a Bit</span><span class="sxs-lookup"><span data-stu-id="0bd27-116">Bitwise Operators</span></span>](bitwise-operators.md)

[<span data-ttu-id="0bd27-117">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="0bd27-117">Arithmetic Operators</span></span>](arithmetic-operators.md)

[<span data-ttu-id="0bd27-118">Referência de Símbolos e Operadores</span><span class="sxs-lookup"><span data-stu-id="0bd27-118">Symbol and Operator Reference</span></span>](index.md)
