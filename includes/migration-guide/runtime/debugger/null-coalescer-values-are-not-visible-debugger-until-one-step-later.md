---
ms.openlocfilehash: 907c4aa5573c392a68afad0a4d937eadcd556440
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619793"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a><span data-ttu-id="7c461-101">Valores nulos de união não são visíveis no depurador até uma etapa posterior</span><span class="sxs-lookup"><span data-stu-id="7c461-101">Null coalescer values are not visible in debugger until one step later</span></span>

#### <a name="details"></a><span data-ttu-id="7c461-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="7c461-102">Details</span></span>

<span data-ttu-id="7c461-103">Um bug no .NET Framework 4.5 faz com que os valores definidos por meio de uma operação de união nula não fiquem visíveis no depurador imediatamente após a operação de atribuição ser executada na versão de 64 bits do Framework.</span><span class="sxs-lookup"><span data-stu-id="7c461-103">A bug in the .NET Framework 4.5 causes values set via a null coalescing operation to not be visible in the debugger immediately after the assignment operation is executed when running on the 64-bit version of the Framework.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7c461-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="7c461-104">Suggestion</span></span>

<span data-ttu-id="7c461-105">Colocar um tempo adicional no depurador fará com que o valor do local/campo seja atualizado corretamente.</span><span class="sxs-lookup"><span data-stu-id="7c461-105">Stepping one additional time in the debugger will cause the local/field's value to be correctly updated.</span></span> <span data-ttu-id="7c461-106">Além disso, esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7c461-106">Also, this issue has been fixed in the .NET Framework 4.6; upgrading to that version of the Framework should solve the issue.</span></span>

| <span data-ttu-id="7c461-107">Name</span><span class="sxs-lookup"><span data-stu-id="7c461-107">Name</span></span>    | <span data-ttu-id="7c461-108">Valor</span><span class="sxs-lookup"><span data-stu-id="7c461-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7c461-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="7c461-109">Scope</span></span>   |<span data-ttu-id="7c461-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="7c461-110">Edge</span></span>|
|<span data-ttu-id="7c461-111">Versão</span><span class="sxs-lookup"><span data-stu-id="7c461-111">Version</span></span>|<span data-ttu-id="7c461-112">4.5</span><span class="sxs-lookup"><span data-stu-id="7c461-112">4.5</span></span>|
|<span data-ttu-id="7c461-113">Type</span><span class="sxs-lookup"><span data-stu-id="7c461-113">Type</span></span>|<span data-ttu-id="7c461-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="7c461-114">Runtime</span></span>|
