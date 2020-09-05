---
ms.openlocfilehash: 3f82a4daac3b5d8981532f0c82e9a76f13c68b6e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496761"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a><span data-ttu-id="f8f15-101">Desserialização de objetos em domínios de aplicativo podem falhar</span><span class="sxs-lookup"><span data-stu-id="f8f15-101">Deserialization of objects across appdomains can fail</span></span>

#### <a name="details"></a><span data-ttu-id="f8f15-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="f8f15-102">Details</span></span>

<span data-ttu-id="f8f15-103">Em alguns casos, quando um aplicativo usa dois ou mais domínios de aplicativo com bases de aplicativo diferentes, a tentativa de desserializar objetos no contexto da chamada lógica nos domínios de aplicativo aciona uma exceção.</span><span class="sxs-lookup"><span data-stu-id="f8f15-103">In some cases, when an app uses two or more app domains with different application bases, trying to deserialize objects in the logical call context across app domains throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f8f15-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="f8f15-104">Suggestion</span></span>

<span data-ttu-id="f8f15-105">Consulte [Mitigação: desserialização de objetos em domínios de aplicativos](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md).</span><span class="sxs-lookup"><span data-stu-id="f8f15-105">See [Mitigation: Deserialization of Objects Across App Domains](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span></span>

| <span data-ttu-id="f8f15-106">Nome</span><span class="sxs-lookup"><span data-stu-id="f8f15-106">Name</span></span>    | <span data-ttu-id="f8f15-107">Valor</span><span class="sxs-lookup"><span data-stu-id="f8f15-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f8f15-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="f8f15-108">Scope</span></span>   |<span data-ttu-id="f8f15-109">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="f8f15-109">Edge</span></span>|
|<span data-ttu-id="f8f15-110">Versão</span><span class="sxs-lookup"><span data-stu-id="f8f15-110">Version</span></span>|<span data-ttu-id="f8f15-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="f8f15-111">4.5.1</span></span>|
|<span data-ttu-id="f8f15-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="f8f15-112">Type</span></span>|<span data-ttu-id="f8f15-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="f8f15-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="f8f15-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="f8f15-114">Affected APIs</span></span>

<span data-ttu-id="f8f15-115">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="f8f15-115">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
