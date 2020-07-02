---
ms.openlocfilehash: 0f87f9e9b87860da97ce96e18104b44ec4327c91
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621020"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="c2f59-101">PipeConnection.GetHashAlgorithm do WCF agora usa o SHA256</span><span class="sxs-lookup"><span data-stu-id="c2f59-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="c2f59-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="c2f59-102">Details</span></span>

<span data-ttu-id="c2f59-103">A partir do .NET Framework 4.7.1, o Windows Communication Foundation usa o hash SHA256 para gerar nomes aleatórios para pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="c2f59-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="c2f59-104">No .NET Framework 4.7 e nas versões anteriores, ele usa o hash SHA1.</span><span class="sxs-lookup"><span data-stu-id="c2f59-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c2f59-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="c2f59-105">Suggestion</span></span>

<span data-ttu-id="c2f59-106">Se houver problemas de compatibilidade com essa alteração no .NET Framework 4.7.1 ou uma versão posterior, é possível recusá-la adicionando a seguinte linha à seção <code>&lt;runtime&gt;</code> do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="c2f59-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the <code>&lt;runtime&gt;</code> section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="c2f59-107">Name</span><span class="sxs-lookup"><span data-stu-id="c2f59-107">Name</span></span>    | <span data-ttu-id="c2f59-108">Valor</span><span class="sxs-lookup"><span data-stu-id="c2f59-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c2f59-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="c2f59-109">Scope</span></span>   |<span data-ttu-id="c2f59-110">Secundária</span><span class="sxs-lookup"><span data-stu-id="c2f59-110">Minor</span></span>|
|<span data-ttu-id="c2f59-111">Versão</span><span class="sxs-lookup"><span data-stu-id="c2f59-111">Version</span></span>|<span data-ttu-id="c2f59-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="c2f59-112">4.7.1</span></span>|
|<span data-ttu-id="c2f59-113">Type</span><span class="sxs-lookup"><span data-stu-id="c2f59-113">Type</span></span>|<span data-ttu-id="c2f59-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="c2f59-114">Runtime</span></span>|
