---
ms.openlocfilehash: 318609c15d2e0b9a7ee59b38463735b33ef87974
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857251"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="f90bd-101">PipeConnection.GetHashAlgorithm do WCF agora usa o SHA256</span><span class="sxs-lookup"><span data-stu-id="f90bd-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f90bd-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="f90bd-102">Details</span></span>|<span data-ttu-id="f90bd-103">A partir do .NET Framework 4.7.1, o Windows Communication Foundation usa o hash SHA256 para gerar nomes aleatórios para pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="f90bd-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="f90bd-104">No .NET Framework 4.7 e nas versões anteriores, ele usa o hash SHA1.</span><span class="sxs-lookup"><span data-stu-id="f90bd-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>|
|<span data-ttu-id="f90bd-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="f90bd-105">Suggestion</span></span>|<span data-ttu-id="f90bd-106">Se houver problemas de compatibilidade com essa alteração no .NET Framework 4.7.1 ou uma versão posterior, é possível recusá-la adicionando a seguinte linha à seção <code>&lt;runtime&gt;</code> do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="f90bd-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the <code>&lt;runtime&gt;</code> section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="f90bd-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="f90bd-107">Scope</span></span>|<span data-ttu-id="f90bd-108">Secundária</span><span class="sxs-lookup"><span data-stu-id="f90bd-108">Minor</span></span>|
|<span data-ttu-id="f90bd-109">Versão</span><span class="sxs-lookup"><span data-stu-id="f90bd-109">Version</span></span>|<span data-ttu-id="f90bd-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="f90bd-110">4.7.1</span></span>|
|<span data-ttu-id="f90bd-111">Type</span><span class="sxs-lookup"><span data-stu-id="f90bd-111">Type</span></span>|<span data-ttu-id="f90bd-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="f90bd-112">Runtime</span></span>|
