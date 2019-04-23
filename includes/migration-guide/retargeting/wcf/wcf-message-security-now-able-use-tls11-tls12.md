---
ms.openlocfilehash: 0a3dc43ebdc58d54675f2264a8ee56d9f4358cd8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803163"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a><span data-ttu-id="8aa91-101">A segurança de mensagens do WCF agora pode usar o TLS1.1 e o TLS1.2</span><span class="sxs-lookup"><span data-stu-id="8aa91-101">WCF message security now is able to use TLS1.1 and TLS1.2</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8aa91-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="8aa91-102">Details</span></span>|<span data-ttu-id="8aa91-103">A partir do .NET Framework 4.7, os clientes podem configurar o TLS1.1 ou o TLS1.2 na segurança de mensagens do WCF, além do SSL3.0 e o TLS1.0, por meio das configurações do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8aa91-103">Starting in the .NET Framework 4.7, customers can configure either TLS1.1 or TLS1.2 in WCF message security in addition to SSL3.0 and TLS1.0 through application configuration settings.</span></span>|
|<span data-ttu-id="8aa91-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="8aa91-104">Suggestion</span></span>|<span data-ttu-id="8aa91-105">No .NET Framework 4.7, a compatibilidade com o TLS1.1 e o TLS1.2 na segurança de mensagens do WCF é desabilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="8aa91-105">In the .NET Framework 4.7, support for TLS1.1 and TLS1.2 in WCF message security is disabled by default.</span></span> <span data-ttu-id="8aa91-106">É possível habilitá-la adicionando a seguinte linha à seção <code>&lt;runtime&gt;</code> do arquivo web.config:</span><span class="sxs-lookup"><span data-stu-id="8aa91-106">You can enable it by adding the following line to the <code>&lt;runtime&gt;</code> section of the app.config or web.config file:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="8aa91-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="8aa91-107">Scope</span></span>|<span data-ttu-id="8aa91-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="8aa91-108">Edge</span></span>|
|<span data-ttu-id="8aa91-109">Versão</span><span class="sxs-lookup"><span data-stu-id="8aa91-109">Version</span></span>|<span data-ttu-id="8aa91-110">4.7</span><span class="sxs-lookup"><span data-stu-id="8aa91-110">4.7</span></span>|
|<span data-ttu-id="8aa91-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="8aa91-111">Type</span></span>|<span data-ttu-id="8aa91-112">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="8aa91-112">Retargeting</span></span>|
