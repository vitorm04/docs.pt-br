---
title: '#elif – Referência de C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: d7ca980146369174a202c8096cdba154712a438e
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239376"
---
# <a name="elif-c-reference"></a><span data-ttu-id="b853a-102">#elif (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="b853a-102">#elif (C# Reference)</span></span>
<span data-ttu-id="b853a-103">O `#elif` permite criar uma diretiva condicional composta.</span><span class="sxs-lookup"><span data-stu-id="b853a-103">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="b853a-104">A expressão `#elif` será avaliada se nenhum dos [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) anteriores nem nenhuma diretiva `#elif`, opcional, anterior avaliar expressões para `true`.</span><span class="sxs-lookup"><span data-stu-id="b853a-104">The `#elif` expression will be evaluated if neither the preceding [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="b853a-105">Se uma expressão `#elif` for avaliada como `true`, o compilador avalia todo o código entre o `#elif` e a próxima diretiva condicional.</span><span class="sxs-lookup"><span data-stu-id="b853a-105">If a `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="b853a-106">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="b853a-106">For example:</span></span>  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 <span data-ttu-id="b853a-107">É possível usar os operadores `==` (igualdade), `!=` (desigualdade), `&&` (e) e `||` (ou), para avaliar vários símbolos.</span><span class="sxs-lookup"><span data-stu-id="b853a-107">You can use the operators `==` (equality), `!=` (inequality), `&&` (and), and `||` (or), to evaluate multiple symbols.</span></span> <span data-ttu-id="b853a-108">Também é possível agrupar os símbolos e operadores com parênteses.</span><span class="sxs-lookup"><span data-stu-id="b853a-108">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b853a-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b853a-109">Remarks</span></span>  
 <span data-ttu-id="b853a-110">`#elif` é equivalente a usar:</span><span class="sxs-lookup"><span data-stu-id="b853a-110">`#elif` is equivalent to using:</span></span>  
  
```csharp
#else  
#if  
```  
  
 <span data-ttu-id="b853a-111">Usar `#elif` é mais simples, porque cada `#if` requer um [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), enquanto um `#elif` pode ser usado sem um `#endif` de correspondência.</span><span class="sxs-lookup"><span data-stu-id="b853a-111">Using `#elif` is simpler, because each `#if` requires a [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), whereas a `#elif` can be used without a matching `#endif`.</span></span>  
  
 <span data-ttu-id="b853a-112">Consulte [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) para obter um exemplo de como usar `#elif`.</span><span class="sxs-lookup"><span data-stu-id="b853a-112">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#elif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b853a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b853a-113">See Also</span></span>

- [<span data-ttu-id="b853a-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="b853a-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="b853a-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="b853a-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b853a-116">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="b853a-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
