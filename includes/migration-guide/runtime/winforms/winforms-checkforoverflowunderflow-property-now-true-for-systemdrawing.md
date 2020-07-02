---
ms.openlocfilehash: 4cd06fd02fadbaa9f74e40f850e688ee883454ed
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619887"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a><span data-ttu-id="178f3-101">A propriedade CheckForOverflowUnderflow do WinForm agora é true para System.Drawing</span><span class="sxs-lookup"><span data-stu-id="178f3-101">WinForm's CheckForOverflowUnderflow property is now true for System.Drawing</span></span>

#### <a name="details"></a><span data-ttu-id="178f3-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="178f3-102">Details</span></span>

<span data-ttu-id="178f3-103">A propriedade CheckForOverflowUnderflow do o assembly System.Drawing.dll está definida como true.</span><span class="sxs-lookup"><span data-stu-id="178f3-103">The CheckForOverflowUnderflow property for the System.Drawing.dll assembly is set to true.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="178f3-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="178f3-104">Suggestion</span></span>

<span data-ttu-id="178f3-105">Anteriormente, quando os estouros ocorriam, o resultado teria sido truncado silenciosamente.</span><span class="sxs-lookup"><span data-stu-id="178f3-105">Previously when overflows occurred, the result would be silently truncated.</span></span> <span data-ttu-id="178f3-106">Agora, uma exceção <xref:System.OverflowException?displayProperty=fullName> é gerada.</span><span class="sxs-lookup"><span data-stu-id="178f3-106">Now an <xref:System.OverflowException?displayProperty=fullName> exception is thrown.</span></span>

| <span data-ttu-id="178f3-107">Name</span><span class="sxs-lookup"><span data-stu-id="178f3-107">Name</span></span>    | <span data-ttu-id="178f3-108">Valor</span><span class="sxs-lookup"><span data-stu-id="178f3-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="178f3-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="178f3-109">Scope</span></span>   |<span data-ttu-id="178f3-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="178f3-110">Edge</span></span>|
|<span data-ttu-id="178f3-111">Versão</span><span class="sxs-lookup"><span data-stu-id="178f3-111">Version</span></span>|<span data-ttu-id="178f3-112">4.5</span><span class="sxs-lookup"><span data-stu-id="178f3-112">4.5</span></span>|
|<span data-ttu-id="178f3-113">Type</span><span class="sxs-lookup"><span data-stu-id="178f3-113">Type</span></span>|<span data-ttu-id="178f3-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="178f3-114">Runtime</span></span>|
