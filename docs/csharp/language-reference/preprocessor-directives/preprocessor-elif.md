---
title: '#elif – Referência de C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: b04db4bd23a459043efec59b8ebf9d322defbcf7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608592"
---
# <a name="elif-c-reference"></a><span data-ttu-id="f1ffa-102">#elif (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="f1ffa-102">#elif (C# Reference)</span></span>
<span data-ttu-id="f1ffa-103">O `#elif` permite criar uma diretiva condicional composta.</span><span class="sxs-lookup"><span data-stu-id="f1ffa-103">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="f1ffa-104">A expressão `#elif` será avaliada se nenhum dos [#if](./preprocessor-if.md) anteriores nem nenhuma diretiva `#elif`, opcional, anterior avaliar expressões para `true`.</span><span class="sxs-lookup"><span data-stu-id="f1ffa-104">The `#elif` expression will be evaluated if neither the preceding [#if](./preprocessor-if.md) nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="f1ffa-105">Se uma expressão `#elif` for avaliada como `true`, o compilador avalia todo o código entre o `#elif` e a próxima diretiva condicional.</span><span class="sxs-lookup"><span data-stu-id="f1ffa-105">If a `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="f1ffa-106">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="f1ffa-106">For example:</span></span>  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 <span data-ttu-id="f1ffa-107">É possível usar os operadores `==` (igualdade), `!=` (desigualdade), `&&` (e) e `||` (ou), para avaliar vários símbolos.</span><span class="sxs-lookup"><span data-stu-id="f1ffa-107">You can use the operators `==` (equality), `!=` (inequality), `&&` (and), and `||` (or), to evaluate multiple symbols.</span></span> <span data-ttu-id="f1ffa-108">Também é possível agrupar os símbolos e operadores com parênteses.</span><span class="sxs-lookup"><span data-stu-id="f1ffa-108">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1ffa-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="f1ffa-109">Remarks</span></span>  
 <span data-ttu-id="f1ffa-110">`#elif` é equivalente a usar:</span><span class="sxs-lookup"><span data-stu-id="f1ffa-110">`#elif` is equivalent to using:</span></span>  
  
```csharp
#else  
#if  
```  
  
 <span data-ttu-id="f1ffa-111">Usar `#elif` é mais simples, porque cada `#if` requer um [#endif](./preprocessor-endif.md), enquanto um `#elif` pode ser usado sem um `#endif` de correspondência.</span><span class="sxs-lookup"><span data-stu-id="f1ffa-111">Using `#elif` is simpler, because each `#if` requires a [#endif](./preprocessor-endif.md), whereas a `#elif` can be used without a matching `#endif`.</span></span>  
  
 <span data-ttu-id="f1ffa-112">Consulte [#if](./preprocessor-if.md) para obter um exemplo de como usar `#elif`.</span><span class="sxs-lookup"><span data-stu-id="f1ffa-112">See [#if](./preprocessor-if.md) for an example of how to use `#elif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1ffa-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1ffa-113">See also</span></span>

- [<span data-ttu-id="f1ffa-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="f1ffa-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f1ffa-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="f1ffa-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f1ffa-116">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="f1ffa-116">C# Preprocessor Directives</span></span>](./index.md)
