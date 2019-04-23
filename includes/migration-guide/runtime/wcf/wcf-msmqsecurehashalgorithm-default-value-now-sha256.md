---
ms.openlocfilehash: ce8e162e11802de1b06bfbc63d5c55de67ef23df
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803199"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="52e92-101">O valor padrão MsmqSecureHashAlgorithm do WCF agora é SHA256</span><span class="sxs-lookup"><span data-stu-id="52e92-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="52e92-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="52e92-102">Details</span></span>|<span data-ttu-id="52e92-103">A partir do .NET Framework 4.7.1, o algoritmo de assinatura da mensagem padrão no WCF para mensagens Msmq é SHA256.</span><span class="sxs-lookup"><span data-stu-id="52e92-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="52e92-104">No .NET Framework 4.7 e versões anteriores, o algoritmo de assinatura da mensagem padrão é SHA1.</span><span class="sxs-lookup"><span data-stu-id="52e92-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>|
|<span data-ttu-id="52e92-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="52e92-105">Suggestion</span></span>|<span data-ttu-id="52e92-106">Se houver problemas de compatibilidade com essa alteração no .NET Framework 4.7.1 ou uma versão posterior, será possível recusá-la adicionando a seguinte linha à seção <code>&lt;runtime&gt;</code> do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="52e92-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="52e92-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="52e92-107">Scope</span></span>|<span data-ttu-id="52e92-108">Secundário</span><span class="sxs-lookup"><span data-stu-id="52e92-108">Minor</span></span>|
|<span data-ttu-id="52e92-109">Versão</span><span class="sxs-lookup"><span data-stu-id="52e92-109">Version</span></span>|<span data-ttu-id="52e92-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="52e92-110">4.7.1</span></span>|
|<span data-ttu-id="52e92-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="52e92-111">Type</span></span>|<span data-ttu-id="52e92-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="52e92-112">Runtime</span></span>|
