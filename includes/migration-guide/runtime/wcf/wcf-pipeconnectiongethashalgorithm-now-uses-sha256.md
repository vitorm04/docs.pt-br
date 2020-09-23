---
ms.openlocfilehash: 9f5f238e3d4222af1da3a1713e1b3e65de6e6f49
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91025374"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="65183-101">PipeConnection.GetHashAlgorithm do WCF agora usa o SHA256</span><span class="sxs-lookup"><span data-stu-id="65183-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="65183-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="65183-102">Details</span></span>

<span data-ttu-id="65183-103">A partir do .NET Framework 4.7.1, o Windows Communication Foundation usa o hash SHA256 para gerar nomes aleatórios para pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="65183-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="65183-104">No .NET Framework 4.7 e nas versões anteriores, ele usa o hash SHA1.</span><span class="sxs-lookup"><span data-stu-id="65183-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="65183-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="65183-105">Suggestion</span></span>

<span data-ttu-id="65183-106">Se houver problemas de compatibilidade com essa alteração no .NET Framework 4.7.1 ou uma versão posterior, é possível recusá-la adicionando a seguinte linha à seção `<runtime>` do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="65183-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the `<runtime>` section of your app.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="65183-107">Name</span><span class="sxs-lookup"><span data-stu-id="65183-107">Name</span></span>    | <span data-ttu-id="65183-108">Valor</span><span class="sxs-lookup"><span data-stu-id="65183-108">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="65183-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="65183-109">Scope</span></span>   | <span data-ttu-id="65183-110">Secundária</span><span class="sxs-lookup"><span data-stu-id="65183-110">Minor</span></span>   |
| <span data-ttu-id="65183-111">Versão</span><span class="sxs-lookup"><span data-stu-id="65183-111">Version</span></span> | <span data-ttu-id="65183-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="65183-112">4.7.1</span></span>   |
| <span data-ttu-id="65183-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="65183-113">Type</span></span>    | <span data-ttu-id="65183-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="65183-114">Runtime</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="65183-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="65183-115">Affected APIs</span></span>

<span data-ttu-id="65183-116">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="65183-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
