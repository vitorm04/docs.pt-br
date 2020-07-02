---
ms.openlocfilehash: b2fcacdb02c411c4dcb12051bf0c6759faccdea2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619867"
---
### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a><span data-ttu-id="038ec-101">O método Replace nas URLs do OData é desabilitado por padrão</span><span class="sxs-lookup"><span data-stu-id="038ec-101">The Replace method in OData URLs is disabled by default</span></span>

#### <a name="details"></a><span data-ttu-id="038ec-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="038ec-102">Details</span></span>

<span data-ttu-id="038ec-103">A partir do .NET Framework 4.5, o método Replace em URLs do OData é desabilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="038ec-103">Beginning in the .NET Framework 4.5, the Replace method in OData URLs is disabled by default.</span></span> <span data-ttu-id="038ec-104">Quando o Replace do OData está desabilitado (agora por padrão), qualquer solicitação de usuário, incluindo funções de substituição (que são incomuns), falha.</span><span class="sxs-lookup"><span data-stu-id="038ec-104">When OData Replace is disabled (now by default), any user requests including replace functions (which are uncommon) will fail.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="038ec-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="038ec-105">Suggestion</span></span>

<span data-ttu-id="038ec-106">Se o método de substituição for necessário (o que é incomum), ele poderá ser reabilitado por meio das configurações (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=fullName>).</span><span class="sxs-lookup"><span data-stu-id="038ec-106">If the replace method is required (which is uncommon), it can be re-enabled through a config settings (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=fullName>).</span></span> <span data-ttu-id="038ec-107">No entanto, um método de substituição habilitado pode dar abertura para vulnerabilidades de segurança, devendo ser usado somente depois de análise cuidadosa.</span><span class="sxs-lookup"><span data-stu-id="038ec-107">However, an enabled replace method can open security vulnerabilities and should only be used after careful review.</span></span>

| <span data-ttu-id="038ec-108">Name</span><span class="sxs-lookup"><span data-stu-id="038ec-108">Name</span></span>    | <span data-ttu-id="038ec-109">Valor</span><span class="sxs-lookup"><span data-stu-id="038ec-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="038ec-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="038ec-110">Scope</span></span>   |<span data-ttu-id="038ec-111">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="038ec-111">Edge</span></span>|
|<span data-ttu-id="038ec-112">Versão</span><span class="sxs-lookup"><span data-stu-id="038ec-112">Version</span></span>|<span data-ttu-id="038ec-113">4.5</span><span class="sxs-lookup"><span data-stu-id="038ec-113">4.5</span></span>|
|<span data-ttu-id="038ec-114">Type</span><span class="sxs-lookup"><span data-stu-id="038ec-114">Type</span></span>|<span data-ttu-id="038ec-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="038ec-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="038ec-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="038ec-116">Affected APIs</span></span>

-<xref:System.Data.Services.DataService%601?displayProperty=nameWithType></li></ul>|
