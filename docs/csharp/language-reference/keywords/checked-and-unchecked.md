---
title: Contexto verificado e não verificado (Referência de C#)
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: f8e292a67fab49b5fc3616e438d063eca2617274
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/18/2018
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="d4f9d-102">Contexto verificado e não verificado (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="d4f9d-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="d4f9d-103">Instruções C# podem ser executadas em contexto marcado ou desmarcado.</span><span class="sxs-lookup"><span data-stu-id="d4f9d-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="d4f9d-104">Em um contexto marcado, o estouro aritmético gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="d4f9d-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="d4f9d-105">Em um contexto não verificado, o estouro aritmético é ignorado, e o resultado é truncado descartando todos os bits de ordem superior que não se encaixam no tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="d4f9d-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
-   <span data-ttu-id="d4f9d-106">[verificado](checked.md) Especificar o contexto verificado.</span><span class="sxs-lookup"><span data-stu-id="d4f9d-106">[checked](checked.md) Specify checked context.</span></span>  
  
-   <span data-ttu-id="d4f9d-107">[não verificado](unchecked.md) Especificar o contexto não verificado.</span><span class="sxs-lookup"><span data-stu-id="d4f9d-107">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="d4f9d-108">As seguintes operações são afetadas pela verificação de estouro:</span><span class="sxs-lookup"><span data-stu-id="d4f9d-108">The following operations are affected by the overflow checking:</span></span>  
  
-   <span data-ttu-id="d4f9d-109">Expressões que usam os seguintes operadores predefinidos em tipos integrais:</span><span class="sxs-lookup"><span data-stu-id="d4f9d-109">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="d4f9d-110">`++`, `--`, unário `-`, `+`, `-`, `*`, `/`</span><span class="sxs-lookup"><span data-stu-id="d4f9d-110">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
-   <span data-ttu-id="d4f9d-111">Conversões numéricas explícitas entre tipos integrais ou de `float` ou `double` para um tipo integral.</span><span class="sxs-lookup"><span data-stu-id="d4f9d-111">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="d4f9d-112">Se nem `checked` ou `unchecked` for especificado, o contexto padrão de expressões de não constante (expressões que são avaliadas no tempo de execução) é definido pelo valor da opção do compilador [-checked](../compiler-options/checked-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="d4f9d-112">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [-checked](../compiler-options/checked-compiler-option.md) compiler option.</span></span> <span data-ttu-id="d4f9d-113">Por padrão, o valor dessa opção é removido e as operações aritméticas são executadas em um contexto não verificado.</span><span class="sxs-lookup"><span data-stu-id="d4f9d-113">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>
 
 <span data-ttu-id="d4f9d-114">Para expressões de constante (expressões que podem ser totalmente avaliadas no tempo de compilação), o contexto padrão sempre é verificado.</span><span class="sxs-lookup"><span data-stu-id="d4f9d-114">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="d4f9d-115">A menos que uma expressão de constante seja explicitamente colocada em um contexto não verificado, estouros que ocorrem durante a avaliação do tempo de compilação da expressão causam erros de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="d4f9d-115">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d4f9d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d4f9d-116">See Also</span></span>  
 [<span data-ttu-id="d4f9d-117">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="d4f9d-117">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="d4f9d-118">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d4f9d-118">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="d4f9d-119">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="d4f9d-119">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="d4f9d-120">Palavras-chave de instrução</span><span class="sxs-lookup"><span data-stu-id="d4f9d-120">Statement Keywords</span></span>](statement-keywords.md)
