---
description: '#elif – Referência de C#'
title: '#elif – Referência de C#'
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: 3aa9082b392b352091b9fde74a85f9dd155ad7b1
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132281"
---
# <a name="elif-c-reference"></a><span data-ttu-id="c56a5-103">#elif (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="c56a5-103">#elif (C# Reference)</span></span>
<span data-ttu-id="c56a5-104">O `#elif` permite criar uma diretiva condicional composta.</span><span class="sxs-lookup"><span data-stu-id="c56a5-104">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="c56a5-105">A expressão `#elif` será avaliada se nenhum dos [#if](./preprocessor-if.md) anteriores nem nenhuma diretiva `#elif`, opcional, anterior avaliar expressões para `true`.</span><span class="sxs-lookup"><span data-stu-id="c56a5-105">The `#elif` expression will be evaluated if neither the preceding [#if](./preprocessor-if.md) nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="c56a5-106">Se uma expressão `#elif` for avaliada como `true`, o compilador avalia todo o código entre o `#elif` e a próxima diretiva condicional.</span><span class="sxs-lookup"><span data-stu-id="c56a5-106">If a `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="c56a5-107">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c56a5-107">For example:</span></span>  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 <span data-ttu-id="c56a5-108">É possível usar os operadores `==` (igualdade), `!=` (desigualdade), `&&` (e) e `||` (ou), para avaliar vários símbolos.</span><span class="sxs-lookup"><span data-stu-id="c56a5-108">You can use the operators `==` (equality), `!=` (inequality), `&&` (and), and `||` (or), to evaluate multiple symbols.</span></span> <span data-ttu-id="c56a5-109">Também é possível agrupar os símbolos e operadores com parênteses.</span><span class="sxs-lookup"><span data-stu-id="c56a5-109">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c56a5-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="c56a5-110">Remarks</span></span>  
 <span data-ttu-id="c56a5-111">`#elif` é equivalente a usar:</span><span class="sxs-lookup"><span data-stu-id="c56a5-111">`#elif` is equivalent to using:</span></span>  
  
```csharp
#else  
#if  
```  
  
 <span data-ttu-id="c56a5-112">Usar `#elif` é mais simples, porque cada `#if` requer um [#endif](./preprocessor-endif.md), enquanto um `#elif` pode ser usado sem um `#endif` de correspondência.</span><span class="sxs-lookup"><span data-stu-id="c56a5-112">Using `#elif` is simpler, because each `#if` requires a [#endif](./preprocessor-endif.md), whereas a `#elif` can be used without a matching `#endif`.</span></span>  
  
 <span data-ttu-id="c56a5-113">Consulte [#if](./preprocessor-if.md) para obter um exemplo de como usar `#elif`.</span><span class="sxs-lookup"><span data-stu-id="c56a5-113">See [#if](./preprocessor-if.md) for an example of how to use `#elif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c56a5-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="c56a5-114">See also</span></span>

- [<span data-ttu-id="c56a5-115">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="c56a5-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c56a5-116">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="c56a5-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c56a5-117">Diretivas de pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="c56a5-117">C# Preprocessor Directives</span></span>](./index.md)
