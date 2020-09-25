---
description: '#elif – Referência de C#'
title: '#elif – Referência de C#'
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: 383c143792a39bb3abcd255804360ad5e2f8ef74
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168693"
---
# <a name="elif-c-reference"></a><span data-ttu-id="4dd71-103">#elif (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="4dd71-103">#elif (C# Reference)</span></span>

<span data-ttu-id="4dd71-104">O `#elif` permite criar uma diretiva condicional composta.</span><span class="sxs-lookup"><span data-stu-id="4dd71-104">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="4dd71-105">A expressão `#elif` será avaliada se nenhum dos [#if](./preprocessor-if.md) anteriores nem nenhuma diretiva `#elif`, opcional, anterior avaliar expressões para `true`.</span><span class="sxs-lookup"><span data-stu-id="4dd71-105">The `#elif` expression will be evaluated if neither the preceding [#if](./preprocessor-if.md) nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="4dd71-106">Se uma expressão `#elif` for avaliada como `true`, o compilador avalia todo o código entre o `#elif` e a próxima diretiva condicional.</span><span class="sxs-lookup"><span data-stu-id="4dd71-106">If a `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="4dd71-107">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4dd71-107">For example:</span></span>  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 <span data-ttu-id="4dd71-108">É possível usar os operadores `==` (igualdade), `!=` (desigualdade), `&&` (e) e `||` (ou), para avaliar vários símbolos.</span><span class="sxs-lookup"><span data-stu-id="4dd71-108">You can use the operators `==` (equality), `!=` (inequality), `&&` (and), and `||` (or), to evaluate multiple symbols.</span></span> <span data-ttu-id="4dd71-109">Também é possível agrupar os símbolos e operadores com parênteses.</span><span class="sxs-lookup"><span data-stu-id="4dd71-109">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4dd71-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="4dd71-110">Remarks</span></span>  

 <span data-ttu-id="4dd71-111">`#elif` é equivalente a usar:</span><span class="sxs-lookup"><span data-stu-id="4dd71-111">`#elif` is equivalent to using:</span></span>  
  
```csharp
#else  
#if  
```  
  
 <span data-ttu-id="4dd71-112">Usar `#elif` é mais simples, porque cada `#if` requer um [#endif](./preprocessor-endif.md), enquanto um `#elif` pode ser usado sem um `#endif` de correspondência.</span><span class="sxs-lookup"><span data-stu-id="4dd71-112">Using `#elif` is simpler, because each `#if` requires a [#endif](./preprocessor-endif.md), whereas a `#elif` can be used without a matching `#endif`.</span></span>  
  
 <span data-ttu-id="4dd71-113">Consulte [#if](./preprocessor-if.md) para obter um exemplo de como usar `#elif`.</span><span class="sxs-lookup"><span data-stu-id="4dd71-113">See [#if](./preprocessor-if.md) for an example of how to use `#elif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dd71-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="4dd71-114">See also</span></span>

- [<span data-ttu-id="4dd71-115">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="4dd71-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4dd71-116">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="4dd71-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4dd71-117">Diretivas de pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="4dd71-117">C# Preprocessor Directives</span></span>](./index.md)
