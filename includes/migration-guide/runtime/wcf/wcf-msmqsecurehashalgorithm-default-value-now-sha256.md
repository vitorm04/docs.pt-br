---
ms.openlocfilehash: 7c0227980aa5d90f3788783088bcd7cd9509ed66
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770808"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="4b10e-101">O valor padrão MsmqSecureHashAlgorithm do WCF agora é SHA256</span><span class="sxs-lookup"><span data-stu-id="4b10e-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="4b10e-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="4b10e-102">Details</span></span>

<span data-ttu-id="4b10e-103">A partir do .NET Framework 4.7.1, o algoritmo de assinatura da mensagem padrão no WCF para mensagens Msmq é SHA256.</span><span class="sxs-lookup"><span data-stu-id="4b10e-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="4b10e-104">No .NET Framework 4.7 e versões anteriores, o algoritmo de assinatura da mensagem padrão é SHA1.</span><span class="sxs-lookup"><span data-stu-id="4b10e-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4b10e-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="4b10e-105">Suggestion</span></span>

<span data-ttu-id="4b10e-106">Se você tiver problemas de compatibilidade com essa alteração no .NET Framework 4.7.1 ou posterior, poderá recusar a alteração adicionando a seguinte linha à `<runtime>` seção do arquivo de app.config:</span><span class="sxs-lookup"><span data-stu-id="4b10e-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the `<runtime>` section of your app.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; />
  </runtime>
</configuration>
```

| <span data-ttu-id="4b10e-107">Nome</span><span class="sxs-lookup"><span data-stu-id="4b10e-107">Name</span></span>    | <span data-ttu-id="4b10e-108">Valor</span><span class="sxs-lookup"><span data-stu-id="4b10e-108">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="4b10e-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="4b10e-109">Scope</span></span>   | <span data-ttu-id="4b10e-110">Secundária</span><span class="sxs-lookup"><span data-stu-id="4b10e-110">Minor</span></span>   |
| <span data-ttu-id="4b10e-111">Versão</span><span class="sxs-lookup"><span data-stu-id="4b10e-111">Version</span></span> | <span data-ttu-id="4b10e-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="4b10e-112">4.7.1</span></span>   |
| <span data-ttu-id="4b10e-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="4b10e-113">Type</span></span>    | <span data-ttu-id="4b10e-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="4b10e-114">Runtime</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="4b10e-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="4b10e-115">Affected APIs</span></span>

<span data-ttu-id="4b10e-116">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="4b10e-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
