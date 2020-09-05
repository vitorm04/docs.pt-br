---
ms.openlocfilehash: af8de731ee93d0bfb01042d894f5730570dcdd78
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496307"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a><span data-ttu-id="fbd32-101">Valores nulos de união não são visíveis no depurador até uma etapa posterior</span><span class="sxs-lookup"><span data-stu-id="fbd32-101">Null coalescer values are not visible in debugger until one step later</span></span>

#### <a name="details"></a><span data-ttu-id="fbd32-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="fbd32-102">Details</span></span>

<span data-ttu-id="fbd32-103">Um bug no .NET Framework 4.5 faz com que os valores definidos por meio de uma operação de união nula não fiquem visíveis no depurador imediatamente após a operação de atribuição ser executada na versão de 64 bits do Framework.</span><span class="sxs-lookup"><span data-stu-id="fbd32-103">A bug in the .NET Framework 4.5 causes values set via a null coalescing operation to not be visible in the debugger immediately after the assignment operation is executed when running on the 64-bit version of the Framework.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fbd32-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="fbd32-104">Suggestion</span></span>

<span data-ttu-id="fbd32-105">Colocar um tempo adicional no depurador fará com que o valor do local/campo seja atualizado corretamente.</span><span class="sxs-lookup"><span data-stu-id="fbd32-105">Stepping one additional time in the debugger will cause the local/field's value to be correctly updated.</span></span> <span data-ttu-id="fbd32-106">Além disso, esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fbd32-106">Also, this issue has been fixed in the .NET Framework 4.6; upgrading to that version of the Framework should solve the issue.</span></span>

| <span data-ttu-id="fbd32-107">Nome</span><span class="sxs-lookup"><span data-stu-id="fbd32-107">Name</span></span>    | <span data-ttu-id="fbd32-108">Valor</span><span class="sxs-lookup"><span data-stu-id="fbd32-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fbd32-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="fbd32-109">Scope</span></span>   |<span data-ttu-id="fbd32-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="fbd32-110">Edge</span></span>|
|<span data-ttu-id="fbd32-111">Versão</span><span class="sxs-lookup"><span data-stu-id="fbd32-111">Version</span></span>|<span data-ttu-id="fbd32-112">4.5</span><span class="sxs-lookup"><span data-stu-id="fbd32-112">4.5</span></span>|
|<span data-ttu-id="fbd32-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="fbd32-113">Type</span></span>|<span data-ttu-id="fbd32-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="fbd32-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="fbd32-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="fbd32-115">Affected APIs</span></span>

<span data-ttu-id="fbd32-116">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="fbd32-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
