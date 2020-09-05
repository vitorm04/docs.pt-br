---
ms.openlocfilehash: 68b0c4bb032b9744ef585eaef3d68e31afebee24
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497641"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a><span data-ttu-id="db89b-101">A propriedade CheckForOverflowUnderflow do WinForm agora é true para System.Drawing</span><span class="sxs-lookup"><span data-stu-id="db89b-101">WinForm's CheckForOverflowUnderflow property is now true for System.Drawing</span></span>

#### <a name="details"></a><span data-ttu-id="db89b-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="db89b-102">Details</span></span>

<span data-ttu-id="db89b-103">A propriedade CheckForOverflowUnderflow do o assembly System.Drawing.dll está definida como true.</span><span class="sxs-lookup"><span data-stu-id="db89b-103">The CheckForOverflowUnderflow property for the System.Drawing.dll assembly is set to true.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="db89b-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="db89b-104">Suggestion</span></span>

<span data-ttu-id="db89b-105">Anteriormente, quando os estouros ocorriam, o resultado teria sido truncado silenciosamente.</span><span class="sxs-lookup"><span data-stu-id="db89b-105">Previously when overflows occurred, the result would be silently truncated.</span></span> <span data-ttu-id="db89b-106">Agora, uma exceção <xref:System.OverflowException?displayProperty=fullName> é gerada.</span><span class="sxs-lookup"><span data-stu-id="db89b-106">Now an <xref:System.OverflowException?displayProperty=fullName> exception is thrown.</span></span>

| <span data-ttu-id="db89b-107">Nome</span><span class="sxs-lookup"><span data-stu-id="db89b-107">Name</span></span>    | <span data-ttu-id="db89b-108">Valor</span><span class="sxs-lookup"><span data-stu-id="db89b-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="db89b-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="db89b-109">Scope</span></span>   |<span data-ttu-id="db89b-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="db89b-110">Edge</span></span>|
|<span data-ttu-id="db89b-111">Versão</span><span class="sxs-lookup"><span data-stu-id="db89b-111">Version</span></span>|<span data-ttu-id="db89b-112">4.5</span><span class="sxs-lookup"><span data-stu-id="db89b-112">4.5</span></span>|
|<span data-ttu-id="db89b-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="db89b-113">Type</span></span>|<span data-ttu-id="db89b-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="db89b-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="db89b-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="db89b-115">Affected APIs</span></span>

<span data-ttu-id="db89b-116">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="db89b-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
