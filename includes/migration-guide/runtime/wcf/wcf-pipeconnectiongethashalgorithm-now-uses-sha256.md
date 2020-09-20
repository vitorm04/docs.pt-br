---
ms.openlocfilehash: 3cf1740565343558a85fdfa68957773468c28231
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770916"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="5cd06-101">PipeConnection.GetHashAlgorithm do WCF agora usa o SHA256</span><span class="sxs-lookup"><span data-stu-id="5cd06-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="5cd06-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="5cd06-102">Details</span></span>

<span data-ttu-id="5cd06-103">A partir do .NET Framework 4.7.1, o Windows Communication Foundation usa o hash SHA256 para gerar nomes aleatórios para pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="5cd06-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="5cd06-104">No .NET Framework 4.7 e nas versões anteriores, ele usa o hash SHA1.</span><span class="sxs-lookup"><span data-stu-id="5cd06-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5cd06-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="5cd06-105">Suggestion</span></span>

<span data-ttu-id="5cd06-106">Se houver problemas de compatibilidade com essa alteração no .NET Framework 4.7.1 ou uma versão posterior, é possível recusá-la adicionando a seguinte linha à seção `<runtime>` do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="5cd06-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the `<runtime>` section of your app.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true" />
  </runtime>
</configuration>

| Name    | Value   |
|:--------|:--------|
| Scope   | Minor   |
| Version | 4.7.1   |
| Type    | Runtime |

#### Affected APIs

Not detectable via API analysis.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
