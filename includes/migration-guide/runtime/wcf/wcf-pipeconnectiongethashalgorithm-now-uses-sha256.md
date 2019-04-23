---
ms.openlocfilehash: 318609c15d2e0b9a7ee59b38463735b33ef87974
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803136"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="9021a-101">PipeConnection.GetHashAlgorithm do WCF agora usa o SHA256</span><span class="sxs-lookup"><span data-stu-id="9021a-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="9021a-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="9021a-102">Details</span></span>|<span data-ttu-id="9021a-103">A partir do .NET Framework 4.7.1, o Windows Communication Foundation usa o hash SHA256 para gerar nomes aleatórios para pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="9021a-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="9021a-104">No .NET Framework 4.7 e nas versões anteriores, ele usa o hash SHA1.</span><span class="sxs-lookup"><span data-stu-id="9021a-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>|
|<span data-ttu-id="9021a-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="9021a-105">Suggestion</span></span>|<span data-ttu-id="9021a-106">Se houver problemas de compatibilidade com essa alteração no .NET Framework 4.7.1 ou uma versão posterior, é possível recusá-la adicionando a seguinte linha à seção <code>&lt;runtime&gt;</code> do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="9021a-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the <code>&lt;runtime&gt;</code> section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="9021a-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="9021a-107">Scope</span></span>|<span data-ttu-id="9021a-108">Secundário</span><span class="sxs-lookup"><span data-stu-id="9021a-108">Minor</span></span>|
|<span data-ttu-id="9021a-109">Versão</span><span class="sxs-lookup"><span data-stu-id="9021a-109">Version</span></span>|<span data-ttu-id="9021a-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="9021a-110">4.7.1</span></span>|
|<span data-ttu-id="9021a-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="9021a-111">Type</span></span>|<span data-ttu-id="9021a-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="9021a-112">Runtime</span></span>|
