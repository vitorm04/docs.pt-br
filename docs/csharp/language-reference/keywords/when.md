---
title: when (Referência de C#)
ms.date: 03/07/2017
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
ms.openlocfilehash: a71cbdce256b1c1bd5d101d66f216fb229d70adf
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/29/2018
ms.locfileid: "47401125"
---
 # <a name="when-c-reference"></a><span data-ttu-id="7ec5a-102">when (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="7ec5a-102">when (C# Reference)</span></span>

<span data-ttu-id="7ec5a-103">Você pode usar a palavra-chave contextual `when` para especificar uma condição de filtro em dois contextos:</span><span class="sxs-lookup"><span data-stu-id="7ec5a-103">You can use the `when` contextual keyword to specify a filter condition in two contexts:</span></span>

- <span data-ttu-id="7ec5a-104">Na instrução `catch` de um bloco [try/catch](try-catch.md) ou [try/catch/finally](try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="7ec5a-104">In the `catch` statement of a [try/catch](try-catch.md) or [try/catch/finally](try-catch-finally.md) block.</span></span>
- <span data-ttu-id="7ec5a-105">No rótulo `case` de uma instrução [switch](switch.md).</span><span class="sxs-lookup"><span data-stu-id="7ec5a-105">In the `case` label of a [switch](switch.md) statement.</span></span>

## <a name="when-in-a-catch-statement"></a><span data-ttu-id="7ec5a-106">`when` em uma instrução `catch`</span><span class="sxs-lookup"><span data-stu-id="7ec5a-106">`when` in a `catch` statement</span></span>

<span data-ttu-id="7ec5a-107">Começando com o C# 6, `When` pode ser usado em uma instrução `catch` para especificar uma condição que deve ser verdadeira para o manipulador para uma exceção específica a ser executada.</span><span class="sxs-lookup"><span data-stu-id="7ec5a-107">Starting with C# 6, `When` can be used in a `catch` statement to specify a condition that must be true for the handler for a specific exception to execute.</span></span> <span data-ttu-id="7ec5a-108">A sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="7ec5a-108">Its syntax is:</span></span>

```csharp
catch ExceptionType [e] when (expr)
```
<span data-ttu-id="7ec5a-109">em que *expr* é uma expressão que é avaliada como um valor booliano.</span><span class="sxs-lookup"><span data-stu-id="7ec5a-109">where *expr* is an expression that evaluates to a Boolean value.</span></span> <span data-ttu-id="7ec5a-110">Se ele retornar `true`, o manipulador de exceção será executado, se `false`, não executará.</span><span class="sxs-lookup"><span data-stu-id="7ec5a-110">If it returns `true`, the exception handler executes; if `false`, it does not.</span></span> 

<span data-ttu-id="7ec5a-111">O exemplo a seguir usa a palavra-chave `when` para executar os manipuladores condicionalmente para um <xref:System.Net.Http.HttpRequestException> dependendo do texto da mensagem de exceção.</span><span class="sxs-lookup"><span data-stu-id="7ec5a-111">The following example uses the `when` keyword to conditionally execute handlers for an <xref:System.Net.Http.HttpRequestException> depending on the text of the exception message.</span></span>

 [!code-csharp[when-with-catch](../../../../samples/snippets/csharp/language-reference/keywords/when/catch.cs)]  
  
## <a name="when-in-a-switch-statement"></a><span data-ttu-id="7ec5a-112">`when` em uma instrução `switch`</span><span class="sxs-lookup"><span data-stu-id="7ec5a-112">`when` in a `switch` statement</span></span>

<span data-ttu-id="7ec5a-113">Iniciando com C# 7.0, os rótulos `case` não precisam mais ser mutuamente exclusivos e a ordem na qual os rótulos `case` são exibidos em uma instrução `switch` pode determinar qual bloco de opção é executado.</span><span class="sxs-lookup"><span data-stu-id="7ec5a-113">Starting with C# 7.0, `case` labels no longer need be mutually exclusive, and the order in which `case` labels appear in a `switch` statement can determine which switch block executes.</span></span> <span data-ttu-id="7ec5a-114">A palavra-chave `when` pode ser usada para especificar uma condição de filtro que faz com que seu rótulo case associado seja verdadeiro somente se a condição de filtro também for verdadeira.</span><span class="sxs-lookup"><span data-stu-id="7ec5a-114">The `when` keyword can be used to specify a filter condition that causes its associated case label to be true only if the filter condition is also true.</span></span> <span data-ttu-id="7ec5a-115">A sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="7ec5a-115">Its syntax is:</span></span>

```csharp
case (expr) when (when-condition):
```
<span data-ttu-id="7ec5a-116">em que *expr* é um padrão de constante ou padrão de tipo que é comparado com a expressão de correspondência e *when-condition* é qualquer expressão booliana.</span><span class="sxs-lookup"><span data-stu-id="7ec5a-116">where *expr* is a constant pattern or type pattern that is compared to the match expression, and *when-condition* is any Boolean expression.</span></span> 

<span data-ttu-id="7ec5a-117">O exemplo a seguir usa a palavra-chave `when` para testar os objetos `Shape` que têm uma área de zero, bem como para testar uma variedade de objetos `Shape` que têm uma área maior que zero.</span><span class="sxs-lookup"><span data-stu-id="7ec5a-117">The following example uses the `when` keyword to test for `Shape` objects that have an area of zero, as well as to test for a variety of `Shape` objects that have an area greater than zero.</span></span> 

 [!code-csharp[when-with-case#1](../../../../samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]  

## <a name="see-also"></a><span data-ttu-id="7ec5a-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ec5a-118">See also</span></span>

- [<span data-ttu-id="7ec5a-119">instrução switch</span><span class="sxs-lookup"><span data-stu-id="7ec5a-119">switch statement</span></span>](switch.md)  
- [<span data-ttu-id="7ec5a-120">instruções try/catch</span><span class="sxs-lookup"><span data-stu-id="7ec5a-120">try/catch statement</span></span>](try-catch.md)  
- [<span data-ttu-id="7ec5a-121">instrução try/catch/finally</span><span class="sxs-lookup"><span data-stu-id="7ec5a-121">try/catch/finally statement</span></span>](try-catch-finally.md) 
