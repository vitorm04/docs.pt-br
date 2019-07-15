---
ms.openlocfilehash: c1a2d76b4e596acc395da6cefed008078e57a336
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858544"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a><span data-ttu-id="b22f6-101">Valores nulos de união não são visíveis no depurador até uma etapa posterior</span><span class="sxs-lookup"><span data-stu-id="b22f6-101">Null coalescer values are not visible in debugger until one step later</span></span>

|   |   |
|---|---|
|<span data-ttu-id="b22f6-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="b22f6-102">Details</span></span>|<span data-ttu-id="b22f6-103">Um bug no .NET Framework 4.5 faz com que os valores definidos por meio de uma operação de união nula não fiquem visíveis no depurador imediatamente após a operação de atribuição ser executada na versão de 64 bits do Framework.</span><span class="sxs-lookup"><span data-stu-id="b22f6-103">A bug in the .NET Framework 4.5 causes values set via a null coalescing operation to not be visible in the debugger immediately after the assignment operation is executed when running on the 64-bit version of the Framework.</span></span>|
|<span data-ttu-id="b22f6-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="b22f6-104">Suggestion</span></span>|<span data-ttu-id="b22f6-105">Colocar um tempo adicional no depurador fará com que o valor do local/campo seja atualizado corretamente.</span><span class="sxs-lookup"><span data-stu-id="b22f6-105">Stepping one additional time in the debugger will cause the local/field's value to be correctly updated.</span></span> <span data-ttu-id="b22f6-106">Além disso, esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b22f6-106">Also, this issue has been fixed in the .NET Framework 4.6; upgrading to that version of the Framework should solve the issue.</span></span>|
|<span data-ttu-id="b22f6-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="b22f6-107">Scope</span></span>|<span data-ttu-id="b22f6-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="b22f6-108">Edge</span></span>|
|<span data-ttu-id="b22f6-109">Versão</span><span class="sxs-lookup"><span data-stu-id="b22f6-109">Version</span></span>|<span data-ttu-id="b22f6-110">4.5</span><span class="sxs-lookup"><span data-stu-id="b22f6-110">4.5</span></span>|
|<span data-ttu-id="b22f6-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="b22f6-111">Type</span></span>|<span data-ttu-id="b22f6-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="b22f6-112">Runtime</span></span>|

