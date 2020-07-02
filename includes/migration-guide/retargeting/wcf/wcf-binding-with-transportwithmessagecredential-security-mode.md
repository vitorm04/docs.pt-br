---
ms.openlocfilehash: 0e949cbdeda99dd7b94e919b903a21171a57f527
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614285"
---
### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a><span data-ttu-id="ac284-101">Associação do WCF com o modo de segurança TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="ac284-101">WCF binding with the TransportWithMessageCredential security mode</span></span>

#### <a name="details"></a><span data-ttu-id="ac284-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ac284-102">Details</span></span>

<span data-ttu-id="ac284-103">Começando com o .NET Framework 4.6.1, a associação do WCF que usar o modo de segurança TransportWithMessageCredential poderá ser configurada para receber mensagens com cabeçalhos &quot;to&quot; não assinados para chaves de segurança assimétricas. Por padrão, os cabeçalhos &quot;to&quot; não assinados continuarão a ser rejeitados no NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="ac284-103">Beginning in the .NET Framework 4.6.1, WCF binding that uses the TransportWithMessageCredential security mode can be set up to receive messages with unsigned &quot;to&quot; headers for asymmetric security keys.By default, unsigned &quot;to&quot; headers will continue to be rejected in .NET Framework 4.6.1.</span></span> <span data-ttu-id="ac284-104">Eles só serão aceitos se o aplicativo aceitar esse novo modo de operação usando a opção de configuração Switch.System.ServiceModel.AllowUnsignedToHeader.</span><span class="sxs-lookup"><span data-stu-id="ac284-104">They will only be accepted if an application opts into this new mode of operation using the Switch.System.ServiceModel.AllowUnsignedToHeader configuration switch.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ac284-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="ac284-105">Suggestion</span></span>

<span data-ttu-id="ac284-106">Como esse é um recurso de aceitação, ele não deve afetar o comportamento dos aplicativos existentes.</span><span class="sxs-lookup"><span data-stu-id="ac284-106">Because this is an opt-in feature, it should not affect the behavior of existing apps.</span></span><br/><span data-ttu-id="ac284-107">Para controlar se o novo comportamento está sendo usado ou não, use a seguinte configuração:</span><span class="sxs-lookup"><span data-stu-id="ac284-107">To control whether the new behavior is used or not, use the following configuration setting:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.ServiceModel.AllowUnsignedToHeader=true" />
</runtime>
```

| <span data-ttu-id="ac284-108">Name</span><span class="sxs-lookup"><span data-stu-id="ac284-108">Name</span></span>    | <span data-ttu-id="ac284-109">Valor</span><span class="sxs-lookup"><span data-stu-id="ac284-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ac284-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="ac284-110">Scope</span></span>   | <span data-ttu-id="ac284-111">Transparente</span><span class="sxs-lookup"><span data-stu-id="ac284-111">Transparent</span></span> |
| <span data-ttu-id="ac284-112">Versão</span><span class="sxs-lookup"><span data-stu-id="ac284-112">Version</span></span> | <span data-ttu-id="ac284-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="ac284-113">4.6.1</span></span>       |
| <span data-ttu-id="ac284-114">Type</span><span class="sxs-lookup"><span data-stu-id="ac284-114">Type</span></span>    | <span data-ttu-id="ac284-115">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="ac284-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="ac284-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ac284-116">Affected APIs</span></span>

- <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
