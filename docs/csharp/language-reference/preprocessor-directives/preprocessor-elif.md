---
title: '#elif – Referência de C#'
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: c78818f40b76414d289af6c704ff019b63befe37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712566"
---
# <a name="elif-c-reference"></a><span data-ttu-id="b256b-102">#elif (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="b256b-102">#elif (C# Reference)</span></span>
<span data-ttu-id="b256b-103">O `#elif` permite criar uma diretiva condicional composta.</span><span class="sxs-lookup"><span data-stu-id="b256b-103">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="b256b-104">A expressão `#elif` será avaliada se nenhum dos [#if](./preprocessor-if.md) anteriores nem nenhuma diretiva `#elif`, opcional, anterior avaliar expressões para `true`.</span><span class="sxs-lookup"><span data-stu-id="b256b-104">The `#elif` expression will be evaluated if neither the preceding [#if](./preprocessor-if.md) nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="b256b-105">Se uma expressão `#elif` for avaliada como `true`, o compilador avalia todo o código entre o `#elif` e a próxima diretiva condicional.</span><span class="sxs-lookup"><span data-stu-id="b256b-105">If a `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="b256b-106">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="b256b-106">For example:</span></span>  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 <span data-ttu-id="b256b-107">É possível usar os operadores `==` (igualdade), `!=` (desigualdade), `&&` (e) e `||` (ou), para avaliar vários símbolos.</span><span class="sxs-lookup"><span data-stu-id="b256b-107">You can use the operators `==` (equality), `!=` (inequality), `&&` (and), and `||` (or), to evaluate multiple symbols.</span></span> <span data-ttu-id="b256b-108">Também é possível agrupar os símbolos e operadores com parênteses.</span><span class="sxs-lookup"><span data-stu-id="b256b-108">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b256b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b256b-109">Remarks</span></span>  
 <span data-ttu-id="b256b-110">`#elif` é equivalente a usar:</span><span class="sxs-lookup"><span data-stu-id="b256b-110">`#elif` is equivalent to using:</span></span>  
  
```csharp
#else  
#if  
```  
  
 <span data-ttu-id="b256b-111">Usar `#elif` é mais simples, porque cada `#if` requer um [#endif](./preprocessor-endif.md), enquanto um `#elif` pode ser usado sem um `#endif` de correspondência.</span><span class="sxs-lookup"><span data-stu-id="b256b-111">Using `#elif` is simpler, because each `#if` requires a [#endif](./preprocessor-endif.md), whereas a `#elif` can be used without a matching `#endif`.</span></span>  
  
 <span data-ttu-id="b256b-112">Consulte [#if](./preprocessor-if.md) para obter um exemplo de como usar `#elif`.</span><span class="sxs-lookup"><span data-stu-id="b256b-112">See [#if](./preprocessor-if.md) for an example of how to use `#elif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b256b-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="b256b-113">See also</span></span>

- [<span data-ttu-id="b256b-114">C# Referência</span><span class="sxs-lookup"><span data-stu-id="b256b-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b256b-115">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="b256b-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b256b-116">C# Diretivas de pré-processador</span><span class="sxs-lookup"><span data-stu-id="b256b-116">C# Preprocessor Directives</span></span>](./index.md)
