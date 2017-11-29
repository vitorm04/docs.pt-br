---
title: Operadores boolianos (F#)
description: "Saiba mais sobre os operadores booleanos que estão disponíveis no F # linguagem de programação."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f79370b8-4bc2-4704-b514-d392c80942bd
ms.openlocfilehash: 63588f2e371bf2c0f15de0b8a26a46be82f832c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="boolean-operators"></a><span data-ttu-id="b7851-104">Operadores boolianos</span><span class="sxs-lookup"><span data-stu-id="b7851-104">Boolean Operators</span></span>

<span data-ttu-id="b7851-105">Este tópico descreve o suporte para operadores boolianos na linguagem F #.</span><span class="sxs-lookup"><span data-stu-id="b7851-105">This topic describes the support for Boolean operators in the F# language.</span></span>


## <a name="summary-of-boolean-operators"></a><span data-ttu-id="b7851-106">Resumo de operadores boolianos</span><span class="sxs-lookup"><span data-stu-id="b7851-106">Summary of Boolean Operators</span></span>
<span data-ttu-id="b7851-107">A tabela a seguir resume os operadores booleanos que estão disponíveis na linguagem F #.</span><span class="sxs-lookup"><span data-stu-id="b7851-107">The following table summarizes the Boolean operators that are available in the F# language.</span></span> <span data-ttu-id="b7851-108">O único tipo com suporte desses operadores é o `bool` tipo.</span><span class="sxs-lookup"><span data-stu-id="b7851-108">The only type supported by these operators is the `bool` type.</span></span>

|<span data-ttu-id="b7851-109">Operador</span><span class="sxs-lookup"><span data-stu-id="b7851-109">Operator</span></span>|<span data-ttu-id="b7851-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7851-110">Description</span></span>|
|--------|-----------|
|`not`|<span data-ttu-id="b7851-111">Boleana</span><span class="sxs-lookup"><span data-stu-id="b7851-111">Boolean negation</span></span>|
|<code>&#124;&#124;</code>|<span data-ttu-id="b7851-112">Booliano OR</span><span class="sxs-lookup"><span data-stu-id="b7851-112">Boolean OR</span></span>|
|`&&`|<span data-ttu-id="b7851-113">Boolean e</span><span class="sxs-lookup"><span data-stu-id="b7851-113">Boolean AND</span></span>|

<span data-ttu-id="b7851-114">Executam o Boolean e e/ou operadores *avaliação de curto-circuito*, ou seja, elas avaliam a expressão à direita do operador somente quando é necessário determinar o resultado geral da expressão.</span><span class="sxs-lookup"><span data-stu-id="b7851-114">The Boolean AND and OR operators perform *short-circuit evaluation*, that is, they evaluate the expression on the right of the operator only when it is necessary to determine the overall result of the expression.</span></span> <span data-ttu-id="b7851-115">A segunda expressão do `&&` operador é avaliado apenas se a primeira expressão for avaliada como `true`; a segunda expressão do `||` operador é avaliado apenas se a primeira expressão for avaliada como `false`.</span><span class="sxs-lookup"><span data-stu-id="b7851-115">The second expression of the `&&` operator is evaluated only if the first expression evaluates to `true`; the second expression of the `||` operator is evaluated only if the first expression evaluates to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="b7851-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7851-116">See Also</span></span>
[<span data-ttu-id="b7851-117">Operadores Bit a Bit</span><span class="sxs-lookup"><span data-stu-id="b7851-117">Bitwise Operators</span></span>](bitwise-operators.md)

[<span data-ttu-id="b7851-118">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="b7851-118">Arithmetic Operators</span></span>](arithmetic-operators.md)

[<span data-ttu-id="b7851-119">Referência de Símbolos e Operadores</span><span class="sxs-lookup"><span data-stu-id="b7851-119">Symbol and Operator Reference</span></span>](index.md)
