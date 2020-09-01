---
description: Contexto verificado e não verificado – Referência de C#
title: Contexto verificado e não verificado – Referência de C#
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: a8d6a26e28062da682689bf64a9e38ea5fd158b2
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138261"
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="09cd3-103">Contexto verificado e não verificado (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="09cd3-103">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="09cd3-104">Instruções C# podem ser executadas em contexto marcado ou desmarcado.</span><span class="sxs-lookup"><span data-stu-id="09cd3-104">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="09cd3-105">Em um contexto marcado, o estouro aritmético gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="09cd3-105">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="09cd3-106">Em um contexto não verificado, o estouro aritmético é ignorado, e o resultado é truncado descartando todos os bits de ordem superior que não se encaixam no tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="09cd3-106">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
- <span data-ttu-id="09cd3-107">[verificado](checked.md) Especificar o contexto verificado.</span><span class="sxs-lookup"><span data-stu-id="09cd3-107">[checked](checked.md) Specify checked context.</span></span>  
  
- <span data-ttu-id="09cd3-108">[não verificado](unchecked.md) Especificar o contexto não verificado.</span><span class="sxs-lookup"><span data-stu-id="09cd3-108">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="09cd3-109">As seguintes operações são afetadas pela verificação de estouro:</span><span class="sxs-lookup"><span data-stu-id="09cd3-109">The following operations are affected by the overflow checking:</span></span>  
  
- <span data-ttu-id="09cd3-110">Expressões que usam os seguintes operadores predefinidos em tipos integrais:</span><span class="sxs-lookup"><span data-stu-id="09cd3-110">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="09cd3-111">`++`, `--`, unário `-`, `+`, `-`, `*`, `/`</span><span class="sxs-lookup"><span data-stu-id="09cd3-111">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
- <span data-ttu-id="09cd3-112">Conversões numéricas explícitas entre tipos integrais ou de `float` ou `double` para um tipo integral.</span><span class="sxs-lookup"><span data-stu-id="09cd3-112">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="09cd3-113">Se nem `checked` ou `unchecked` for especificado, o contexto padrão de expressões de não constante (expressões que são avaliadas no tempo de execução) é definido pelo valor da opção do compilador [-checked](../compiler-options/checked-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="09cd3-113">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [-checked](../compiler-options/checked-compiler-option.md) compiler option.</span></span> <span data-ttu-id="09cd3-114">Por padrão, o valor dessa opção é removido e as operações aritméticas são executadas em um contexto não verificado.</span><span class="sxs-lookup"><span data-stu-id="09cd3-114">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>

 <span data-ttu-id="09cd3-115">Para expressões de constante (expressões que podem ser totalmente avaliadas no tempo de compilação), o contexto padrão sempre é verificado.</span><span class="sxs-lookup"><span data-stu-id="09cd3-115">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="09cd3-116">A menos que uma expressão de constante seja explicitamente colocada em um contexto não verificado, estouros que ocorrem durante a avaliação do tempo de compilação da expressão causam erros de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="09cd3-116">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="09cd3-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="09cd3-117">See also</span></span>

- [<span data-ttu-id="09cd3-118">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="09cd3-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="09cd3-119">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="09cd3-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="09cd3-120">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="09cd3-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="09cd3-121">Palavras-chave de instrução</span><span class="sxs-lookup"><span data-stu-id="09cd3-121">Statement Keywords</span></span>](statement-keywords.md)
