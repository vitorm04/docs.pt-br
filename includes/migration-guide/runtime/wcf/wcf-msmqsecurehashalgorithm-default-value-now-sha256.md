---
ms.openlocfilehash: 9baca45de1c8994f610815e84fdee8ba3930eb04
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496799"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="8001b-101">O valor padrão MsmqSecureHashAlgorithm do WCF agora é SHA256</span><span class="sxs-lookup"><span data-stu-id="8001b-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="8001b-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="8001b-102">Details</span></span>

<span data-ttu-id="8001b-103">A partir do .NET Framework 4.7.1, o algoritmo de assinatura da mensagem padrão no WCF para mensagens Msmq é SHA256.</span><span class="sxs-lookup"><span data-stu-id="8001b-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="8001b-104">No .NET Framework 4.7 e versões anteriores, o algoritmo de assinatura da mensagem padrão é SHA1.</span><span class="sxs-lookup"><span data-stu-id="8001b-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8001b-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="8001b-105">Suggestion</span></span>

<span data-ttu-id="8001b-106">Se houver problemas de compatibilidade com essa alteração no .NET Framework 4.7.1 ou uma versão posterior, será possível recusá-la adicionando a seguinte linha à seção <code>&lt;runtime&gt;</code> do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="8001b-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="8001b-107">Nome</span><span class="sxs-lookup"><span data-stu-id="8001b-107">Name</span></span>    | <span data-ttu-id="8001b-108">Valor</span><span class="sxs-lookup"><span data-stu-id="8001b-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8001b-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="8001b-109">Scope</span></span>   |<span data-ttu-id="8001b-110">Secundária</span><span class="sxs-lookup"><span data-stu-id="8001b-110">Minor</span></span>|
|<span data-ttu-id="8001b-111">Versão</span><span class="sxs-lookup"><span data-stu-id="8001b-111">Version</span></span>|<span data-ttu-id="8001b-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="8001b-112">4.7.1</span></span>|
|<span data-ttu-id="8001b-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="8001b-113">Type</span></span>|<span data-ttu-id="8001b-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="8001b-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="8001b-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="8001b-115">Affected APIs</span></span>

<span data-ttu-id="8001b-116">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="8001b-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
