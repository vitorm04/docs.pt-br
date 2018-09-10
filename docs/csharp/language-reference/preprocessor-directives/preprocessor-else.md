---
title: '#else (Referência de C#)'
ms.date: 07/20/2015
f1_keywords:
- '#else'
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
ms.openlocfilehash: 000cbaac4458a104214e3197442a21dcb4740a37
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530218"
---
# <a name="else-c-reference"></a><span data-ttu-id="780dd-102">#else (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="780dd-102">#else (C# Reference)</span></span>
<span data-ttu-id="780dd-103">`#else` permite que você crie uma diretiva condicional composta, para que, caso nenhuma das expressões nas diretivas anteriores [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ou [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) (opcional) seja avaliada como `true`, o compilador avalie todo o código entre `#else` e o próximo `#endif`.</span><span class="sxs-lookup"><span data-stu-id="780dd-103">`#else` lets you create a compound conditional directive, so that, if none of the expressions in the preceding [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) or (optional) [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) directives evaluate to `true`, the compiler will evaluate all code between `#else` and the subsequent `#endif`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="780dd-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="780dd-104">Remarks</span></span>  
 <span data-ttu-id="780dd-105">[#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) deve ser a próxima diretiva de pré-processador após `#else`.</span><span class="sxs-lookup"><span data-stu-id="780dd-105">[#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) must be the next preprocessor directive after `#else`.</span></span> <span data-ttu-id="780dd-106">Consulte [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) para obter um exemplo de como usar `#else`.</span><span class="sxs-lookup"><span data-stu-id="780dd-106">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#else`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="780dd-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="780dd-107">See Also</span></span>

- [<span data-ttu-id="780dd-108">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="780dd-108">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="780dd-109">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="780dd-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="780dd-110">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="780dd-110">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
