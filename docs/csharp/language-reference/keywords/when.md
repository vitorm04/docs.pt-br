---
title: "when (Referência de C#)"
ms.date: 2017-03-07
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- when_CSharpKeyword
- when
dev_langs:
- CSharp
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
caps.latest.revision: 30
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 9ad2eff6eb527f00ce23f463e811aa748def62d0
ms.openlocfilehash: c391c6de51d41577d61278f43d58fade5b7c139f
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
 # <a name="when-c-reference"></a><span data-ttu-id="749fa-102">when (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="749fa-102">when (C# Reference)</span></span>

<span data-ttu-id="749fa-103">Você pode usar a palavra-chave contextual `when` para especificar uma condição de filtro em dois contextos:</span><span class="sxs-lookup"><span data-stu-id="749fa-103">You can use the `when` contextual keyword to specify a filter condition in two contexts:</span></span>

- <span data-ttu-id="749fa-104">Na instrução `catch` de um bloco [try/catch](try-catch.md) ou [try/catch/finally](try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="749fa-104">In the `catch` statement of a [try/catch](try-catch.md) or [try/catch/finally](try-catch-finally.md) block.</span></span>
- <span data-ttu-id="749fa-105">No rótulo `case` de uma instrução [switch](switch.md).</span><span class="sxs-lookup"><span data-stu-id="749fa-105">In the `case` label of a [switch](switch.md) statement.</span></span>

## <a name="when-in-a-catch-statement"></a><span data-ttu-id="749fa-106">`when` em uma instrução `catch`</span><span class="sxs-lookup"><span data-stu-id="749fa-106">`when` in a `catch` statement</span></span>

<span data-ttu-id="749fa-107">Começando com o C# 6, `When` pode ser usado em uma instrução `catch` para especificar uma condição que deve ser verdadeira para o manipulador para uma exceção específica a ser executada.</span><span class="sxs-lookup"><span data-stu-id="749fa-107">Starting with C# 6, `When` can be used in a `catch` statement to specify a condition that must be true for the handler for a specific exception to execute.</span></span> <span data-ttu-id="749fa-108">A sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="749fa-108">Its syntax is:</span></span>

```csharp
catch ExceptionType [e] when (expr)
```
<span data-ttu-id="749fa-109">em que *expr* é uma expressão que é avaliada como um valor booliano.</span><span class="sxs-lookup"><span data-stu-id="749fa-109">where *expr* is an expression that evaluates to a Boolean value.</span></span> <span data-ttu-id="749fa-110">Se ele retornar `true`, o manipulador de exceção será executado, se `false`, não executará.</span><span class="sxs-lookup"><span data-stu-id="749fa-110">If it returns `true`, the exception handler executes; if `false`, it does not.</span></span> 

<span data-ttu-id="749fa-111">O exemplo a seguir usa a palavra-chave `when` para executar os manipuladores condicionalmente para um @System.Net.HttpRequestException dependendo do texto da mensagem de exceção.</span><span class="sxs-lookup"><span data-stu-id="749fa-111">The following example uses the `when` keyword to conditionally execute handlers for an @System.Net.HttpRequestException depending on the text of the exception message.</span></span>

 <span data-ttu-id="749fa-112">[!code-cs[when-with-catch](../../../../samples/snippets/csharp/language-reference/keywords/when/catch.cs)]</span><span class="sxs-lookup"><span data-stu-id="749fa-112">[!code-cs[when-with-catch](../../../../samples/snippets/csharp/language-reference/keywords/when/catch.cs)]</span></span>  
  
## <a name="when-in-a-switch-statement"></a><span data-ttu-id="749fa-113">`when` em uma instrução `switch`</span><span class="sxs-lookup"><span data-stu-id="749fa-113">`when` in a `switch` statement</span></span>

<span data-ttu-id="749fa-114">Iniciando com 7, os rótulos `case` não precisam mais ser mutuamente exclusivos e a ordem na qual os rótulos `case` são exibidos em uma instrução `switch` pode determinar qual bloco switch é executado.</span><span class="sxs-lookup"><span data-stu-id="749fa-114">Starting with 7, `case` labels no longer need be mutually exclusive, and the order in which `case` labels appear in a `switch` statement can determine which switch block executes.</span></span> <span data-ttu-id="749fa-115">A palavra-chave `when` pode ser usada para especificar uma condição de filtro que faz com que seu rótulo case associado seja verdadeiro somente se a condição de filtro também for verdadeira.</span><span class="sxs-lookup"><span data-stu-id="749fa-115">The `when` keyword can be used to specify a filter condition that causes its associated case label to be true only if the filter condition is also true.</span></span> <span data-ttu-id="749fa-116">A sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="749fa-116">Its syntax is:</span></span>

```csharp
case (expr) when (when-condition):
```
<span data-ttu-id="749fa-117">em que *expr* é um padrão de constante ou padrão de tipo que é comparado com a expressão de correspondência e *when-condition* é qualquer expressão booliana.</span><span class="sxs-lookup"><span data-stu-id="749fa-117">where *expr* is a constant pattern or type pattern that is compared to the match expression, and *when-condition* is any Boolean expression.</span></span> 

<span data-ttu-id="749fa-118">O exemplo a seguir usa a palavra-chave `when` para testar os objetos `Shape` que têm uma área de zero, bem como para testar uma variedade de objetos `Shape` que têm uma área maior que zero.</span><span class="sxs-lookup"><span data-stu-id="749fa-118">The following example uses the `when` keyword to test for `Shape` objects that have an area of zero, as well as to test for a variety of `Shape` objects that have an area greater than zero.</span></span> 

 <span data-ttu-id="749fa-119">[!code-cs[when-with-case#1](../../../../samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="749fa-119">[!code-cs[when-with-case#1](../../../../samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="749fa-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="749fa-120">See also</span></span> 
  [<span data-ttu-id="749fa-121">instrução switch</span><span class="sxs-lookup"><span data-stu-id="749fa-121">switch statement</span></span>](switch.md)  
  [<span data-ttu-id="749fa-122">instruções try/catch</span><span class="sxs-lookup"><span data-stu-id="749fa-122">try/catch statement</span></span>](try-catch.md)  
  [<span data-ttu-id="749fa-123">instrução try/catch/finally</span><span class="sxs-lookup"><span data-stu-id="749fa-123">try/catch/finally statement</span></span>](try-catch-finally.md) 


