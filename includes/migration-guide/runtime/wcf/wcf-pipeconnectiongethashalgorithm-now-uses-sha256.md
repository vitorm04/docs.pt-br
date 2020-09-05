---
ms.openlocfilehash: d32725b0d3063d3320b73e02039ff567090da932
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497941"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="ed170-101">PipeConnection.GetHashAlgorithm do WCF agora usa o SHA256</span><span class="sxs-lookup"><span data-stu-id="ed170-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="ed170-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ed170-102">Details</span></span>

<span data-ttu-id="ed170-103">A partir do .NET Framework 4.7.1, o Windows Communication Foundation usa o hash SHA256 para gerar nomes aleatórios para pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="ed170-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="ed170-104">No .NET Framework 4.7 e nas versões anteriores, ele usa o hash SHA1.</span><span class="sxs-lookup"><span data-stu-id="ed170-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ed170-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="ed170-105">Suggestion</span></span>

<span data-ttu-id="ed170-106">Se houver problemas de compatibilidade com essa alteração no .NET Framework 4.7.1 ou uma versão posterior, é possível recusá-la adicionando a seguinte linha à seção <code>&lt;runtime&gt;</code> do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="ed170-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the <code>&lt;runtime&gt;</code> section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="ed170-107">Nome</span><span class="sxs-lookup"><span data-stu-id="ed170-107">Name</span></span>    | <span data-ttu-id="ed170-108">Valor</span><span class="sxs-lookup"><span data-stu-id="ed170-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ed170-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="ed170-109">Scope</span></span>   |<span data-ttu-id="ed170-110">Secundária</span><span class="sxs-lookup"><span data-stu-id="ed170-110">Minor</span></span>|
|<span data-ttu-id="ed170-111">Versão</span><span class="sxs-lookup"><span data-stu-id="ed170-111">Version</span></span>|<span data-ttu-id="ed170-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="ed170-112">4.7.1</span></span>|
|<span data-ttu-id="ed170-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="ed170-113">Type</span></span>|<span data-ttu-id="ed170-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="ed170-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="ed170-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ed170-115">Affected APIs</span></span>

<span data-ttu-id="ed170-116">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="ed170-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
