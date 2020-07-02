---
ms.openlocfilehash: c646372104457e8bc5d418744847f3ee771c8d8b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614297"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a><span data-ttu-id="88cef-101">A segurança de mensagens do WCF agora pode usar o TLS1.1 e o TLS1.2</span><span class="sxs-lookup"><span data-stu-id="88cef-101">WCF message security now is able to use TLS1.1 and TLS1.2</span></span>

#### <a name="details"></a><span data-ttu-id="88cef-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="88cef-102">Details</span></span>

<span data-ttu-id="88cef-103">A partir do .NET Framework 4.7, os clientes podem configurar o TLS1.1 ou o TLS1.2 na segurança de mensagens do WCF, além do SSL3.0 e o TLS1.0, por meio das configurações do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="88cef-103">Starting in the .NET Framework 4.7, customers can configure either TLS1.1 or TLS1.2 in WCF message security in addition to SSL3.0 and TLS1.0 through application configuration settings.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="88cef-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="88cef-104">Suggestion</span></span>

<span data-ttu-id="88cef-105">No .NET Framework 4.7, a compatibilidade com o TLS1.1 e o TLS1.2 na segurança de mensagens do WCF é desabilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="88cef-105">In the .NET Framework 4.7, support for TLS1.1 and TLS1.2 in WCF message security is disabled by default.</span></span> <span data-ttu-id="88cef-106">É possível habilitá-la adicionando a seguinte linha à seção `<runtime>` do arquivo web.config:</span><span class="sxs-lookup"><span data-stu-id="88cef-106">You can enable it by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" />
</runtime>
```

| <span data-ttu-id="88cef-107">Name</span><span class="sxs-lookup"><span data-stu-id="88cef-107">Name</span></span>    | <span data-ttu-id="88cef-108">Valor</span><span class="sxs-lookup"><span data-stu-id="88cef-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="88cef-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="88cef-109">Scope</span></span>   | <span data-ttu-id="88cef-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="88cef-110">Edge</span></span>        |
| <span data-ttu-id="88cef-111">Versão</span><span class="sxs-lookup"><span data-stu-id="88cef-111">Version</span></span> | <span data-ttu-id="88cef-112">4.7</span><span class="sxs-lookup"><span data-stu-id="88cef-112">4.7</span></span>         |
| <span data-ttu-id="88cef-113">Type</span><span class="sxs-lookup"><span data-stu-id="88cef-113">Type</span></span>    | <span data-ttu-id="88cef-114">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="88cef-114">Retargeting</span></span> |
