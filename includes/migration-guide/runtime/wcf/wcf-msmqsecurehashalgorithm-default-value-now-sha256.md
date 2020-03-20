---
ms.openlocfilehash: ce8e162e11802de1b06bfbc63d5c55de67ef23df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857238"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="766dc-101">O valor padrão MsmqSecureHashAlgorithm do WCF agora é SHA256</span><span class="sxs-lookup"><span data-stu-id="766dc-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="766dc-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="766dc-102">Details</span></span>|<span data-ttu-id="766dc-103">A partir do .NET Framework 4.7.1, o algoritmo de assinatura da mensagem padrão no WCF para mensagens Msmq é SHA256.</span><span class="sxs-lookup"><span data-stu-id="766dc-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="766dc-104">No .NET Framework 4.7 e versões anteriores, o algoritmo de assinatura da mensagem padrão é SHA1.</span><span class="sxs-lookup"><span data-stu-id="766dc-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>|
|<span data-ttu-id="766dc-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="766dc-105">Suggestion</span></span>|<span data-ttu-id="766dc-106">Se houver problemas de compatibilidade com essa alteração no .NET Framework 4.7.1 ou uma versão posterior, será possível recusá-la adicionando a seguinte linha à seção <code>&lt;runtime&gt;</code> do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="766dc-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="766dc-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="766dc-107">Scope</span></span>|<span data-ttu-id="766dc-108">Secundária</span><span class="sxs-lookup"><span data-stu-id="766dc-108">Minor</span></span>|
|<span data-ttu-id="766dc-109">Versão</span><span class="sxs-lookup"><span data-stu-id="766dc-109">Version</span></span>|<span data-ttu-id="766dc-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="766dc-110">4.7.1</span></span>|
|<span data-ttu-id="766dc-111">Type</span><span class="sxs-lookup"><span data-stu-id="766dc-111">Type</span></span>|<span data-ttu-id="766dc-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="766dc-112">Runtime</span></span>|
